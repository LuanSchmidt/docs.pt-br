---
title: Criar um aplicativo do .NET Core com plug-ins
description: Saiba como criar um aplicativo do .NET Core compatível com plug-ins.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 16fc9d3c721ddd0618c980c7dc406b7ad7864ff5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739705"
---
# <a name="create-a-net-core-application-with-plugins"></a>Criar um aplicativo do .NET Core com plug-ins

Este tutorial mostra como criar um <xref:System.Runtime.Loader.AssemblyLoadContext> personalizado para carregar plug-ins. Um <xref:System.Runtime.Loader.AssemblyDependencyResolver> é usado para resolver as dependências do plug-in. O tutorial isola corretamente as dependências do plug-in do aplicativo de hospedagem. Você aprenderá como:

- Estruturar um projeto para permitir plug-ins.
- Criar um <xref:System.Runtime.Loader.AssemblyLoadContext> personalizado para carregar cada plug-in.
- Usar o tipo <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> para permitir que os plug-ins tenham dependências.
- Criar plug-ins que possam ser implantados facilmente apenas copiando os artefatos de build.

## <a name="prerequisites"></a>Prerequisites

- Instale o [SDK do .NET Core 3,0](https://dotnet.microsoft.com/download) ou uma versão mais recente.

## <a name="create-the-application"></a>Criar o aplicativo

A primeira etapa é criar o aplicativo:

1. Crie uma nova pasta e, nessa pasta, execute o seguinte comando:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Para facilitar a criação do projeto, crie um arquivo de solução do Visual Studio na mesma pasta. Execute o seguinte comando:

    ```dotnetcli
    dotnet new sln
    ```

3. Execute o seguinte comando para adicionar o projeto de aplicativo à solução:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Agora podemos preencher o esqueleto do aplicativo. Substitua o código no arquivo *AppWithPlugin/Program.cs* pelo código a seguir:

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a>Criar as interfaces do plug-in

A próxima etapa na criação de um aplicativo com plug-ins é definir a interface que os plug-ins precisam implementar. Sugerimos a criação de uma biblioteca de classes contendo todos os tipos que você planeja usar para a comunicação entre o aplicativo e os plug-ins. Essa divisão permite que você publique sua interface de plug-in como um pacote sem precisar enviar seu aplicativo completo.

Na pasta raiz do projeto, execute `dotnet new classlib -o PluginBase`. Além disso, execute `dotnet sln add PluginBase/PluginBase.csproj` para adicionar o projeto ao arquivo de solução. Exclua o arquivo `PluginBase/Class1.cs` e crie um arquivo na pasta `PluginBase` chamada `ICommand.cs` com a seguinte definição de interface:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Essa interface `ICommand` é aquela que todos os plug-ins implementarão.

Agora que a interface `ICommand` está definida, o projeto de aplicativo pode ser um pouco mais preenchido. Adicione uma referência do projeto `AppWithPlugin` ao projeto `PluginBase` com o comando `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` na pasta raiz.

Substitua o comentário `// Load commands from plugins` pelo seguinte snippet de código para permitir que os plug-ins sejam carregados dos caminhos de arquivo fornecidos:

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

Em seguida, substitua o comentário `// Output the loaded commands` pelo snippet de código a seguir:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Substitua o comentário `// Execute the command with the name passed as an argument` pelo snippet a seguir:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

E, finalmente, adicione métodos estáticos à classe `Program` denominada `LoadPlugin` e `CreateCommands`, como é mostrado aqui:

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a>Carregar plug-ins

Agora, o aplicativo pode carregar e instanciar corretamente os comandos de assemblies de plug-in carregados, mas ainda não consegue carregar os assemblies de plug-in. Crie um arquivo chamado *PluginLoadContext.cs* na pasta *AppWithPlugin* com o seguinte conteúdo:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

O tipo `PluginLoadContext` é derivado do tipo <xref:System.Runtime.Loader.AssemblyLoadContext>. O tipo de `AssemblyLoadContext` é um tipo especial no tempo de execução que permite aos desenvolvedores isolar assemblies carregados em grupos diferentes para garantir que as versões do assembly não entrem em conflito. Além disso, um `AssemblyLoadContext` personalizado pode escolher caminhos diferentes de onde carregar os assemblies e substituir o comportamento padrão. O `PluginLoadContext` usa uma instância do tipo `AssemblyDependencyResolver` introduzida no .NET Core 3.0 para resolver nomes de assembly para caminhos. O objeto `AssemblyDependencyResolver` é construído com o caminho para uma biblioteca de classes .NET. Ele resolve assemblies e bibliotecas nativas para seus caminhos relativos com base no arquivo *.deps.json* da biblioteca de classes cujo caminho foi passado para o construtor `AssemblyDependencyResolver`. O `AssemblyLoadContext` personalizado permite que os plug-ins tenham suas próprias dependências e o `AssemblyDependencyResolver` facilita o carregamento correto das dependências.

Agora que o projeto `AppWithPlugin` tem o tipo `PluginLoadContext`, atualize o método `Program.LoadPlugin` com o seguinte corpo:

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

Com uma instância de `PluginLoadContext` diferente para cada plug-in, os plug-ins pode ter dependências diferentes ou mesmo conflitantes sem problemas.

## <a name="simple-plugin-with-no-dependencies"></a>Plug-in simples sem dependências

Novamente na pasta raiz, faça o seguinte:

1. Execute o seguinte comando para criar um novo projeto de biblioteca de classes chamado `HelloPlugin`:
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Execute o seguinte comando para adicionar o projeto à solução de `AppWithPlugin`:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. Substitua o arquivo *HelloPlugin/Class1.cs* por um arquivo chamado *HelloCommand.cs* com o seguinte conteúdo:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Agora, abra o arquivo *HelloPlugin.csproj*. Ele deve ser semelhante ao seguinte:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Entre as marcas `<Project>`, adicione os seguintes elementos:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

O elemento `<Private>false</Private>` é importante. Ele informa ao MSBuild que ele não deve copiar o *PluginBase.dll* para o diretório de saída do HelloPlugin. Se o assembly *PluginBase.dll* estiver presente no diretório de saída, o `PluginLoadContext` encontrará o assembly lá e o carregará ao carregar o assembly *HelloPlugin.dll*. Neste ponto, o tipo `HelloPlugin.HelloCommand` implementará a interface `ICommand` do *PluginBase.dll* no diretório de saída do projeto `HelloPlugin`, não a interface `ICommand` que é carregada no contexto de carregamento padrão. Como o tempo de execução vê esses dois tipos como tipos diferentes de assemblies diferentes, o método `AppWithPlugin.Program.CreateCommands` não encontrará os comandos. Como resultado, os metadados `<Private>false</Private>` serão necessários para a referência ao assembly que contém as interfaces de plug-in.

Agora que o projeto `HelloPlugin` está concluído, devemos atualizar o projeto `AppWithPlugin` para saber onde o plug-in `HelloPlugin` pode ser encontrado. Após o comentário `// Paths to plugins to load`, adicione `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` como um elemento da matriz `pluginPaths`.

## <a name="plugin-with-library-dependencies"></a>Plug-in com dependências de biblioteca

Quase todos os plug-ins são mais complexos do que um simples "Olá, Mundo", e muitos plug-ins têm dependências de outras bibliotecas. Os projetos de plug-in `JsonPlugin` e `OldJson` no exemplo mostram dois exemplos de plug-ins com dependências de pacotes NuGet em `Newtonsoft.Json`. Os próprios arquivos do projeto não têm nenhuma informação especial para as referências do projeto e (depois de adicionar os caminhos do plug-in à matriz de `pluginPaths`), os plug-ins são executados perfeitamente, mesmo que sejam executados na mesma execução do aplicativo AppWithPlugin. No entanto, esses projetos não copiam os assemblies referenciados para o diretório de saída, de modo que os assemblies precisam estar presentes na máquina do usuário para que os plug-ins funcionem. Há duas maneiras de contornar esse problema. A primeira opção é usar o comando `dotnet publish` para publicar a biblioteca de classes. Como alternativa, se você quer usar a saída do `dotnet build` para seu plug-in, adicione a propriedade `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` entre as marcas `<PropertyGroup>` no arquivo de projeto do plug-in. Veja o projeto de plug-in `XcopyablePlugin` como exemplo.

## <a name="other-examples-in-the-sample"></a>Outros exemplos no exemplo

O código-fonte completo para este tutorial pode ser encontrado no [repositório dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). O exemplo completo inclui alguns outros exemplos do comportamento `AssemblyDependencyResolver`. Por exemplo, o objeto `AssemblyDependencyResolver` também pode resolver bibliotecas nativas, bem como assemblies satélites localizados incluídos em pacotes do NuGet. O `UVPlugin` e `FrenchPlugin` no repositório de amostras demonstram esses cenários.

## <a name="reference-a-plugin-from-a-nuget-package"></a>Referenciar um plug-in de um pacote NuGet

Vamos supor que haja um aplicativo A que tenha uma interface de plug-in definida no pacote NuGet chamado `A.PluginBase`. Como você referenciaria o pacote corretamente em seu projeto de plug-in? Para as referências do projeto, o uso dos metadados `<Private>false</Private>` no elemento `ProjectReference` no arquivo de projeto impediu que a dll fosse copiada para a saída.

Faça referenciar o pacote `A.PluginBase` corretamente, altere o elemento `<PackageReference>` no arquivo de projeto para o seguinte:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Isso impede que os assemblies `A.PluginBase` sejam copiados para o diretório de saída do plug-in e garante que o plug-in use a versão A do `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Recomendações de estrutura de destino do plug-in

Como o carregamento de dependência do plug-in usa o arquivo *.deps.json*, há uma pegadinha em relação à estrutura de destino do plug-in. Especificamente, os plug-ins devem ser direcionados a um runtime como o .NET Core 3.0 e não a uma versão do .NET Standard. O arquivo *.deps.json* é gerado com base na estrutura de destino do projeto e, como muitos pacotes compatíveis com o .NET Standard enviam assemblies de referência para compilar no .NET Standard e assemblies de implementação para runtimes específicos, o *.deps.json* pode não reconhecer corretamente os assemblies de implementação ou obter a versão do .NET Standard de um assembly em vez da versão do .NET Core esperada.

## <a name="plugin-framework-references"></a>Referências da estrutura do plugin

Atualmente, os plug-ins não podem introduzir novas estruturas no processo. Por exemplo, você não pode carregar um plug-in que usa o `Microsoft.AspNetCore.App` Framework em um aplicativo que usa apenas a estrutura de `Microsoft.NETCore.App` raiz. O aplicativo host deve declarar referências a todas as estruturas necessárias para plugins.
