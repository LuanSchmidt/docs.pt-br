---
title: Acessando OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: b8a09aff7b5a30b5267fbdbd7bd6391996f359c7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715097"
---
# <a name="accessing-operationcontext"></a>Acessando OperationContext
Este exemplo demonstra como as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.Send>) podem ser usadas com uma atividade de escopo personalizada para acessar <xref:System.ServiceModel.OperationContext.Current%2A> e anexar ou recuperar um cabeçalho de mensagem personalizado em uma mensagem de saída ou de entrada.  
  
## <a name="demonstrates"></a>Demonstra  
 Atividades de mensagem, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como usar pontos de extensibilidade (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nas atividades de mensagem para acessar <xref:System.ServiceModel.OperationContext.Current%2A>. As callbacks são registrados no runtime de fluxo de trabalho como uma implementação de <xref:System.Activities.IExecutionProperty> que é pegarada por atividades de mensagem em cima de execução. Quaisquer atividades de mensagem no mesmo define o escopo como essa implementação de <xref:System.Activities.IExecutionProperty> é afetado. Em particular, este exemplo usa uma atividade personalizado de escopo para forçar o comportamento de retorno de chamada. <xref:System.ServiceModel.Activities.ISendMessageCallback> é usado no fluxo de trabalho de cliente para incluir <xref:System.Activities.WorkflowApplication.Id%2A> de fluxo de trabalho como <xref:System.ServiceModel.Channels.MessageHeader>de saída. Este cabeçalho é capturado no serviço usando <xref:System.ServiceModel.Activities.IReceiveMessageCallback> e o valor de cabeçalho é impresso - ao console.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP. Para executar esse exemplo, as ACLs de URL adequadas devem ser adicionadas (consulte [Configurando http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes), seja executando o Visual Studio como administrador ou executando o comando a seguir em um prompt elevado para adicionar as ACLs apropriadas. Certifique-se de que seu domínio e nome de usuário são substituídos.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Uma vez que o URL ACLs é adicionado, use as seguintes etapas.  
  
    1. {1&gt;Compile a solução.&lt;1}  
  
    2. Defina vários projetos de inicialização clicando com o botão direito do mouse na solução e selecionando **definir projetos de inicialização**.  
  
    3. Adicionar **serviço** e **cliente** (nessa ordem) como vários projetos de inicialização.  
  
    4. Execute o aplicativo. O console de cliente mostra um fluxo de trabalho que executa duas vezes na janela de serviço mostra a ID da instância desses fluxos de trabalho.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
