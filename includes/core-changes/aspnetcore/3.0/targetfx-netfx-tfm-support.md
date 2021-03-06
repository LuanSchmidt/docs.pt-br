---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937276"
---
### <a name="target-framework-net-framework-support-dropped"></a>Estrutura de destino: suporte a .NET Framework Descartado

A partir do ASP.NET Core 3,0, .NET Framework é uma estrutura de destino sem suporte.

#### <a name="change-description"></a>Descrição das alterações

.NET Framework 4,8 é a última versão principal do .NET Framework. Novos aplicativos de ASP.NET Core devem ser criados no .NET Core. A partir da versão 3,0 do .NET Core, você pode considerar ASP.NET Core 3,0 como parte do .NET Core.

Os clientes que usam ASP.NET Core com .NET Framework podem continuar de uma maneira totalmente compatível usando a [versão 2,1 do LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). O suporte e serviço para 2,1 continua até, pelo menos, 21 de agosto de 2021. Essa data é de três anos após a declaração da versão do LTS de acordo com a [política de suporte do .net](https://www.microsoft.com/net/platform/support-policy). O suporte para pacotes ASP.NET Core 2,1 **em .NET Framework** será estendido indefinidamente, semelhante à [política de serviço para outras estruturas ASP.net baseadas em pacote](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Para obter mais informações sobre como portar do .NET Framework para o .NET Core, consulte [portando para o .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions` pacotes (como registro em log, injeção de dependência e configuração) e Entity Framework Core não são afetados. Eles continuarão a dar suporte a .NET Standard.

Para obter mais informações sobre a motivação para essa alteração, consulte [a postagem do blog original](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

ASP.NET Core aplicativos podem ser executados no .NET Core ou .NET Framework.

#### <a name="new-behavior"></a>Novo comportamento

ASP.NET Core aplicativos só podem ser executados no .NET Core.

#### <a name="recommended-action"></a>Ação recomendada

Execute uma das seguintes ações:

- Mantenha seu aplicativo no ASP.NET Core 2,1.
- Migre seu aplicativo e as dependências para o .NET Core.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

{1&gt;Nenhum&lt;1}

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
