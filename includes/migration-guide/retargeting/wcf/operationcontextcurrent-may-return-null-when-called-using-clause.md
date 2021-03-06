---
ms.openlocfilehash: 62ba525a28960d96c5458aa1481e1f319d5bc875
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859354"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current pode retornar nulo quando chamado usando cláusula

|   |   |
|---|---|
|Detalhes|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> poderá retornar <code>null</code> e um <xref:System.NullReferenceException> poderá ocorrer quando todas as seguintes condições forem verdadeiras:<ul><li>Você recupera o valor da propriedade <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> em um método que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</li><li>Você cria uma instância do objeto <xref:System.ServiceModel.OperationContextScope> em uma cláusula <code>using</code>.</li><li>Você recupera o valor da propriedade <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dentro de <code>using statement</code>. Por exemplo:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Sugestão|Para solucionar esse problema, você pode fazer o seguinte:<ul><li>Modifique o código da seguinte maneira para criar uma instância de um novo objeto não <code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A>:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Instalar a atualização mais recente do .NET Framework 4.6.2 ou atualizar para uma versão posterior do .NET Framework. Isso desabilita o fluxo do <xref:System.Threading.ExecutionContext> em <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> e restaura o comportamento de aplicativos do WCF no .NET Framework 4.6.1 e em versões anteriores. Esse comportamento é configurável; é equivalente a adicionar a seguinte configuração de aplicativo ao arquivo de configuração:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Se essa alteração for indesejável e seu aplicativo depender do fluxo do contexto de execução entre contextos de operação, você poderá habilitar o fluxo da seguinte maneira:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

