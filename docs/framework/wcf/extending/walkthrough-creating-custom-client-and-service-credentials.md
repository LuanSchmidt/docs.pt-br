---
title: 'Passo a passo: criar credenciais de serviço e cliente personalizados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: d49df909521b3b5e5cf509c1367821856e91e30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795475"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Passo a passo: criar credenciais de serviço e cliente personalizados

Este tópico mostra como implementar credenciais de cliente e de serviço personalizadas e como usar credenciais personalizadas do código do aplicativo.

## <a name="credentials-extensibility-classes"></a>Classes de extensibilidade de credenciais

As <xref:System.ServiceModel.Description.ClientCredentials> classes <xref:System.ServiceModel.Description.ServiceCredentials> e são os pontos de entrada principais para a extensibilidade de segurança do Windows Communication Foundation (WCF). Essas classes de credenciais fornecem as APIs que permitem que o código do aplicativo defina informações de credenciais e converta tipos de credenciais em tokens de segurança. (Os*tokens de segurança* são o formulário usado para transmitir informações de credenciais dentro de mensagens SOAP.) As responsabilidades dessas classes de credenciais podem ser divididas em duas áreas:

- Forneça as APIs para que os aplicativos definam informações de credenciais.

- Execute como um alocador <xref:System.IdentityModel.Selectors.SecurityTokenManager> para implementações.

As implementações padrão fornecidas no WCF dão suporte aos tipos de credenciais fornecidos pelo sistema e criam um Gerenciador de token de segurança capaz de lidar com esses tipos de credenciais.

## <a name="reasons-to-customize"></a>Motivos para personalizar

Há várias razões para a personalização de classes de credencial de cliente ou serviço. Principalmente, é o requisito de alterar o comportamento de segurança padrão do WCF em relação à manipulação de tipos de credenciais fornecidos pelo sistema, especialmente pelos seguintes motivos:

- Alterações que não são possíveis usando outros pontos de extensibilidade.

- Adicionando novos tipos de credencial.

- Adicionando novos tipos de token de segurança personalizados.

Este tópico descreve como implementar credenciais de cliente e de serviço personalizadas e como usá-las do código do aplicativo.

## <a name="first-in-a-series"></a>Primeiro em uma série

A criação de uma classe de credenciais personalizadas é apenas a primeira etapa, porque o motivo para personalizar as credenciais é alterar o comportamento do WCF em relação ao provisionamento de credenciais, serialização de token de segurança ou autenticação. Outros tópicos nesta seção descrevem como criar serializadores personalizados e autenticadores. Nesse sentido, a criação de uma classe de credencial personalizada é o primeiro tópico da série. As ações subsequentes (criando serializadores personalizados e autenticadores) só podem ser feitas após a criação de credenciais personalizadas. Os tópicos adicionais que se baseiam neste tópico incluem:

- [Como: Criar um provedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)

- [Como: Criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md)

- [Como: Crie um token](how-to-create-a-custom-token.md)personalizado.

## <a name="procedures"></a>Procedimentos

#### <a name="to-implement-custom-client-credentials"></a>Para implementar credenciais de cliente personalizadas

1. Defina uma nova classe derivada da <xref:System.ServiceModel.Description.ClientCredentials> classe.

2. Opcional. Adicione novos métodos ou propriedades para novos tipos de credencial. Se você não adicionar novos tipos de credencial, ignore esta etapa. O exemplo a seguir adiciona `CreditCardNumber` uma propriedade.

3. Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado automaticamente pela infraestrutura de segurança do WCF quando a credencial de cliente personalizada é usada. Esse método é responsável por criar e retornar uma instância de uma implementação da <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe.

    > [!IMPORTANT]
    > É importante observar que o <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> método é substituído para criar um Gerenciador de token de segurança personalizado. O Gerenciador de token de segurança, <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>derivado de, deve retornar um provedor de token de segurança <xref:System.IdentityModel.Selectors.SecurityTokenProvider>personalizado derivado de, para criar o token de segurança real. Se você não seguir esse padrão para criar tokens de segurança, seu aplicativo poderá funcionar incorretamente quando <xref:System.ServiceModel.ChannelFactory> os objetos forem armazenados em cache (que é o comportamento padrão para proxies de cliente do WCF), potencialmente resultando em uma elevação de ataque de privilégio. O objeto de credencial personalizado é armazenado em cache como <xref:System.ServiceModel.ChannelFactory>parte do. No entanto, <xref:System.IdentityModel.Selectors.SecurityTokenManager> o personalizado é criado em cada invocação, o que atenua a ameaça de segurança, desde que a lógica de criação do <xref:System.IdentityModel.Selectors.SecurityTokenManager>token seja colocada no.

4. Substituir o método <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Para implementar um Gerenciador de tokens de segurança de cliente personalizado

1. Defina uma nova classe derivada de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.

2. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> método se uma implementação <xref:System.IdentityModel.Selectors.SecurityTokenProvider> personalizada precisar ser criada. Para obter mais informações sobre provedores de token de segurança [personalizados, consulte Como: Crie um provedor](how-to-create-a-custom-security-token-provider.md)de token de segurança personalizado.

3. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> método se uma implementação <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> personalizada precisar ser criada. Para obter mais informações sobre autenticadores de token de segurança [personalizados, consulte Como: Crie um autenticador](how-to-create-a-custom-security-token-authenticator.md)de token de segurança personalizado.

4. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> método se for necessário <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> criar um personalizado. Para obter mais informações sobre tokens de segurança personalizados e serializadores de token [de segurança personalizados, consulte Como: Crie um token](how-to-create-a-custom-token.md)personalizado.

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Para usar credenciais de cliente personalizadas do código do aplicativo

1. Crie uma instância do cliente gerado que representa a interface de serviço ou crie uma instância do <xref:System.ServiceModel.ChannelFactory> que aponte para um serviço com o qual você deseja se comunicar.

2. Remova o comportamento de credenciais de cliente fornecido pelo sistema <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> da coleção, que pode ser acessada por meio da <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.

3. Crie uma nova instância de uma classe de credenciais de cliente personalizada e adicione- <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> a à coleção, que pode ser acessada por meio da <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

O procedimento anterior mostra como usar credenciais de cliente do código do aplicativo. As credenciais do WCF também podem ser configuradas usando o arquivo de configuração do aplicativo. Usar a configuração do aplicativo geralmente é preferível ao embutir em código porque ele permite a modificação de parâmetros do aplicativo sem a necessidade de modificar a origem, a recompilação e a reimplantação.

O procedimento a seguir descreve como fornecer suporte para a configuração de credenciais personalizadas.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Criando um manipulador de configuração para credenciais de cliente personalizadas

1. Defina uma nova classe derivada de <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.

2. Opcional. Adicione Propriedades para todos os parâmetros de configuração adicionais que você deseja expor por meio da configuração do aplicativo. O exemplo a seguir adiciona uma propriedade `CreditCardNumber`chamada.

3. Substitua a <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> propriedade para retornar o tipo da classe de credenciais de cliente personalizada criada com o elemento de configuração.

4. Substituir o método <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A>. O método é responsável por criar e retornar uma instância da classe de credencial personalizada com base nas configurações carregadas do arquivo de configuração. Chame o método <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> base desse método para recuperar as configurações de credenciais fornecidas pelo sistema carregadas em sua instância personalizada de credenciais de cliente.

5. Opcional. Se você adicionou propriedades adicionais na etapa 2, precisará substituir a <xref:System.Configuration.ConfigurationElement.Properties%2A> propriedade para registrar as definições de configuração adicionais para a estrutura de configuração para reconhecê-las. Combine suas propriedades com as propriedades da classe base para permitir que as configurações fornecidas pelo sistema sejam configuradas por meio desse elemento de configuração de credenciais de cliente personalizadas.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Depois que você tiver a classe de manipulador de configuração, ela poderá ser integrada à estrutura de configuração do WCF. Isso permite que as credenciais de cliente personalizadas sejam usadas nos elementos de comportamento do ponto de extremidade do cliente, conforme mostrado no próximo procedimento.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Para registrar e usar um manipulador de configuração de credenciais de cliente personalizado na configuração do aplicativo

1. Adicione um elemento`extensions`< > e um elemento`behaviorExtensions`> < ao arquivo de configuração.

2. Adicione um elemento`add`< > ao elemento >`behaviorExtensions`< e defina o `name` atributo como um valor apropriado.

3. Defina o `type` atributo para o nome de tipo totalmente qualificado. Inclua também o nome do assembly e outros atributos do assembly.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    <system.serviceModel>
    ```

4. Depois de registrar seu manipulador de configuração, o elemento credenciais personalizadas pode ser usado dentro do mesmo arquivo de configuração em vez do elemento de`clientCredentials`> de < fornecido pelo sistema. Você pode usar as propriedades fornecidas pelo sistema e as novas propriedades que você adicionou à implementação do manipulador de configuração. O exemplo a seguir define o valor de uma propriedade personalizada usando `creditCardNumber` o atributo.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Para implementar credenciais de serviço personalizadas

1. Defina uma nova classe derivada de <xref:System.ServiceModel.Description.ServiceCredentials>.

2. Opcional. Adicione novas propriedades para fornecer APIs para novos valores de credencial que estão sendo adicionados. Se você não adicionar novos valores de credencial, ignore esta etapa. O exemplo a seguir adiciona `AdditionalCertificate` uma propriedade.

3. Substituir o método <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>. Esse método é chamado automaticamente pela infraestrutura do WCF quando a credencial de cliente personalizada é usada. O método é responsável por criar e retornar uma instância de uma implementação da <xref:System.IdentityModel.Selectors.SecurityTokenManager> classe (descrita no próximo procedimento).

4. Opcional. Substituir o método <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A>. Isso é necessário apenas se adicionar novas propriedades ou campos internos à implementação de credenciais de cliente personalizadas.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Para implementar um Gerenciador de token de segurança de serviço personalizado

1. Defina uma nova classe derivada da <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe.

2. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> método se uma implementação <xref:System.IdentityModel.Selectors.SecurityTokenProvider> personalizada precisar ser criada. Para obter mais informações sobre provedores de token de segurança [personalizados, consulte Como: Crie um provedor](how-to-create-a-custom-security-token-provider.md)de token de segurança personalizado.

3. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> método se uma implementação <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> personalizada precisar ser criada. Para obter mais informações sobre autenticadores de token de segurança [personalizados, consulte Como: Crie um tópico de autenticador](how-to-create-a-custom-security-token-authenticator.md) de token de segurança personalizado.

4. Opcional. Substitua o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> método se for necessário <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> criar um personalizado. Para obter mais informações sobre tokens de segurança personalizados e serializadores de token [de segurança personalizados, consulte Como: Crie um token](how-to-create-a-custom-token.md)personalizado.

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Para usar credenciais de serviço personalizadas do código do aplicativo

1. Crie uma instância do <xref:System.ServiceModel.ServiceHost>.

2. Remova o comportamento das credenciais de serviço fornecidas pelo sistema <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> da coleção.

3. Crie uma nova instância da classe de credenciais de serviço personalizada e adicione-a <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> à coleção.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Adicione suporte para configuração usando as etapas descritas anteriormente nos procedimentos "`To create a configuration handler for custom client credentials`" e "`To register and use a custom client credentials configuration handler in the application configuration`." A única diferença é usar a <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> classe em vez <xref:System.ServiceModel.Configuration.ClientCredentialsElement> da classe como uma classe base para o manipulador de configuração. O elemento de credencial de serviço personalizado pode ser usado sempre que o `<serviceCredentials>` elemento fornecido pelo sistema for usado.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Como: Criar um provedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)
- [Como: Criar um autenticador de token de segurança personalizado](how-to-create-a-custom-security-token-authenticator.md)
- [Como: Criar um token personalizado](how-to-create-a-custom-token.md)
