---
title: <transport> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732816"
---
# <a name="transport-of-nethttpbinding"></a>> de transporte de \<de \<NetHttpBinding >
Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetHttpBinding**](nethttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**transporte >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientCredentialType|-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a autenticação HTTP.  O padrão é `None`. Este atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente de dentro de um domínio usando um proxy sobre HTTP. Esse atributo é aplicável somente quando o atributo `mode` do elemento `security` pai é `Transport` ou `TransportCredentialsOnly`. Este atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|territórios|Uma cadeia de caracteres que especifica o realm usado pelo esquema de autenticação HTTP para Digest ou autenticação básica. O padrão é uma cadeia de caracteres vazia.|  
|policyEnforcement|Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser aplicado.<br /><br /> 1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).<br />2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.<br />3. sempre – a política é sempre imposta. Os clientes que não dão suporte à proteção estendida não serão autenticados.|  
|protectionScenario|Essa enumeração Especifica o cenário de proteção imposto pela política.|  
  
## <a name="clientcredentialtype-attribute"></a>Atributo clientCredentialtype  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|As mensagens não são protegidas durante a transferência.|  
|Basic|Especifica autenticação básica.|  
|Digest|Especifica a autenticação Digest.|  
|NTLM|Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.|  
|Windows|Especifica a autenticação integrada do Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>Atributo proxyCredentialType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|-As mensagens não são protegidas durante a transferência.|  
|Basic|Especifica a autenticação básica, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.|  
|Digest|Especifica a autenticação Digest, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.|  
|NTLM|Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.|  
|Windows|Especifica a autenticação integrada do Windows.|  
|Certificate|Executa a autenticação de cliente usando um certificado. Essa opção só funcionará se o atributo `Mode` do elemento pai `security` for definido como transporte e não funcionará se estiver definido como TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Security >](security-of-nethttpbinding.md)|Define os recursos de segurança para o [\<NetHttpBinding](nethttpbinding.md).|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de segurança de transporte SSL com a associação básica. Por padrão, a associação básica dá suporte à comunicação HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
