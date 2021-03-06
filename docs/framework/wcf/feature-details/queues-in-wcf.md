---
title: Filas no Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: fbe3a546fd431beb5ddf1d71153d38580a19ecc9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348349"
---
# <a name="queues-in-windows-communication-foundation"></a>Filas no Windows Communication Foundation
Os tópicos nesta seção discutem o suporte do Windows Communication Foundation (WCF) para filas do. O WCF fornece suporte para enfileiramento aproveitando o enfileiramento de mensagens da Microsoft (anteriormente conhecido como MSMQ) como um transporte e habilita os seguintes cenários:  
  
- Aplicativos menos rígidos. O envio de aplicativos pode enviar mensagens para filas sem a necessidade de saber se o aplicativo receptor está disponível para processar a mensagem. A fila fornece independência de processamento que permite que um aplicativo de envio envie mensagens para a fila em uma taxa que não depende de quão rápido os aplicativos de recebimento podem processar as mensagens. A disponibilidade geral do sistema aumenta quando o envio de mensagens para uma fila não está rigidamente acoplado ao processamento de mensagens.  
  
- Isolamento de falha. Os aplicativos que enviam ou recebem mensagens para uma fila podem falhar sem afetar uns dos outros. Se, por exemplo, o aplicativo de recebimento falhar, o aplicativo de envio poderá continuar a enviar mensagens para a fila. Quando o destinatário estiver novamente, ele poderá processar as mensagens da fila. O isolamento de falhas aumenta a confiabilidade e a disponibilidade geral do sistema.  
  
- Nivelamento de carga. O envio de aplicativos pode saturar o recebimento de aplicativos com mensagens. As filas podem gerenciar taxas de produção e consumo de mensagens incompatíveis para que um receptor não fique sobrecarregado.  
  
- Operações desconectadas. O envio, recebimento e processamento de operações podem ser desconectados ao se comunicar por redes de alta latência ou redes de disponibilidade limitada, como no caso de dispositivos móveis. As filas permitem que essas operações continuem, mesmo quando os pontos de extremidade são desconectados. Quando a conexão é restabelecida, a fila encaminha mensagens para o aplicativo de recebimento.  
  
 Para usar o recurso filas em um aplicativo WCF, você pode usar uma das associações padrão ou pode criar uma associação personalizada se uma das associações padrão não atender às suas necessidades. Para obter mais informações sobre associações padrão relevantes e como escolher uma, consulte [como: trocar mensagens com pontos de extremidade WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Para obter mais informações sobre como criar associações personalizadas, confira [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Uma visão geral dos conceitos do enfileiramento de mensagens.  
  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Uma visão geral do suporte à fila do WCF.  
  
 [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Explica como usar a classe <xref:System.ServiceModel.NetMsmqBinding> para se comunicar entre um cliente WCF e um serviço WCF.  
  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Explica como usar o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para se comunicar entre o WCF e os aplicativos de enfileiramento de mensagens.  
  
 [Agrupamento de mensagens em fila em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Explica como agrupar mensagens em uma fila para facilitar o processamento de mensagens correlacionadas por um único aplicativo de recebimento.  
  
 [Mensagens em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Explica como enlote mensagens em uma transação.  
  
 [Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Explica como lidar com falhas de transferência e entrega de mensagens usando filas de mensagens mortas e como processar mensagem da fila inatividade.  
  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Explica como lidar com mensagens suspeitas (mensagens que excederam o número máximo de tentativas de entrega para o aplicativo de recebimento).  
  
 [Diferenças de recursos da Fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Resume as diferenças no recurso de filas do WCF entre o Windows Vista, o Windows Server 2003 e o [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Protegendo mensagens usando a segurança do transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Descreve como usar a segurança de transporte para proteger mensagens em fila.  
  
 [Protegendo as mensagens com segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Descreve como usar a segurança de mensagem para proteger mensagens enfileiradas.  
  
 [Solução de problemas de mensagens em fila](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Explica como solucionar problemas comuns de enfileiramento.  
  
 [Práticas recomendadas para a comunicação em fila](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Explica as práticas recomendadas para usar a comunicação em fila do WCF.  
