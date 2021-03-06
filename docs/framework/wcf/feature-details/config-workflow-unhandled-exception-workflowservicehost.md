---
title: 'Como: configurar um comportamento de exceção sem tratamento de fluxo de trabalho com WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957254"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Como: configurar um comportamento de exceção sem tratamento de fluxo de trabalho com WorkflowServiceHost
O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção sem tratamento ocorrer em um fluxo de trabalho <xref:System.ServiceModel.Activities.WorkflowServiceHost>hospedado no. Este tópico mostra como configurar esse comportamento em um arquivo de configuração.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Para configurar o WorkflowUnhandledExceptionBehavior  
  
1. Adicione um elemento`workflowUnhandledException`< > em um elemento`behavior`<`serviceBehaviors`> dentro de um elemento < >, usando `action` o atributo para especificar a ação a ser tomada quando uma exceção sem tratamento ocorrer, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > O exemplo de configuração anterior está usando uma configuração simplificada. Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     O `action` atributo do elemento <`workflowUnhandledException`> pode ser definido como um dos seguintes valores:  
  
     **abandon**  
     Anula a instância na memória sem tocar no estado de instância persistente (ou seja, reverta para o último ponto de persistência).  
  
     **abandonAndSuspend**  
     Anula a instância na memória e atualiza a instância persistente a ser suspensa.  
  
     **cancel**  
     Chama manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, o que também pode removê-la do repositório de instância  
  
     **terminate**  
     Conclui a instância na memória e a remove do repositório de instância.  
  
     Para obter mais informações <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>sobre o, consulte [extensibilidade do host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Consulte também

- [Extensibilidade de host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
