---
title: Interfaces de hospedagem CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131963"
---
# <a name="clr-hosting-interfaces"></a>Interfaces de hospedagem CLR
Esta seção descreve as interfaces que os hosts não gerenciados podem usar para integrar o Common Language Runtime (CLR) em seus aplicativos. As informações referem-se à .NET Framework versão 2,0 e versões posteriores. Essas interfaces permitem que o host controle muitos outros aspectos do tempo de execução do que era possível nas versões 1,0 e 1,1 e fornece uma integração muito mais rígida entre o CLR e o modelo de execução do host.  
  
 No .NET Framework versão 1,0 e 1,1, o modelo de hospedagem habilitou um host não gerenciado para carregar o CLR em um processo, para definir determinadas configurações e para receber notificações de eventos. No entanto, em geral, o host e o CLR eram executados de forma independente nesse processo. No .NET Framework versão 2,0 e versões posteriores, novas camadas de abstração permitem que o host forneça muitos dos recursos fornecidos atualmente pelos tipos no assembly do Win32 e estenda o conjunto de recursos que o host pode configurar.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Fornece um método que executa um retorno de chamada para um evento registrado.  
  
 [Interface IApartmentCallback](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Fornece métodos para fazer retornos de chamada em um apartamento.  
  
 [Interface IAppDomainBinding](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Fornece métodos para definir a configuração de tempo de execução.  
  
 [Interface ICatalogServices](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Fornece métodos para catalogar serviços. (Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)  
  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Fornece métodos que dão suporte à comunicação entre o host e o CLR sobre assemblies.  
  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Gerencia uma lista de assemblies que são carregados pelo CLR e não pelo host.  
  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Fornece métodos para o host obter acesso e configurar vários aspectos do, o CLR.  
  
 [Interface ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Fornece métodos que permitem que um host associe um conjunto de tarefas a um identificador e um nome amigável.  
  
 [Interface ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Fornece métodos que permitem ao host configurar despejos de heap personalizados para o relatório de erros.  
  
 [Interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do CLR.  
  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Fornece métodos para o host avaliar e comunicar alterações nas informações de política para assemblies.  
  
 [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Permite que o host bloqueie classes gerenciadas, métodos, propriedades e campos específicos da execução em código parcialmente confiável.  
  
 [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementa um método de retorno de chamada que permite ao host notificar o CLR do status de solicitações de e/s especificadas.  
  
 [Interface ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Permite que o host relate condições de pressão de memória usando uma abordagem semelhante à da função de `CreateMemoryResourceNotification` do Win32.  
  
 [Interface ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Fornece métodos que permitem ao host registrar e cancelar o registro de retornos de chamada para eventos CLR.  
  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Fornece métodos que permitem que o host especifique ações de política a serem executadas em caso de falhas e tempos limite.  
  
 [Interface ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Fornece métodos que permitem ao host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que são internas ao CLR, sem a necessidade de criar ou compreender essa identidade.  
  
 [Interface ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Fornece métodos que permitem ao host manipular o conjunto de assemblies referenciados por um arquivo ou fluxo usando dados de identidade de assembly que são internos ao CLR, sem a necessidade de criar ou compreender essas identidades.  
  
 [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Fornece recursos semelhantes a [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), com um método adicional para definir a interface de controle de host.  
  
 [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Fornece métodos para o host obter informações sobre as tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.  
  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Fornece métodos que permitem ao host fazer solicitações do CLR ou fornecer notificação ao CLR sobre a tarefa associada.  
  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Fornece métodos que permitem que o host solicite explicitamente que o CLR crie uma nova tarefa, obtenha a tarefa em execução no momento e defina o idioma geográfico e a cultura da tarefa.  
  
 [Interface ICLRValidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Fornece métodos para validar imagens executáveis portáteis (PE) e relatar erros de validação.  
  
 [Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Fornece métodos para configurar o CLR.  
  
 [Interface ICorThreadpool](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Fornece métodos para acessar o pool de threads.  
  
 [Interface IDebuggerInfo](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Fornece métodos para obter informações sobre o estado dos serviços de depuração.  
  
 [Interface IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Fornece métodos para notificar o host sobre o bloqueio e o desbloqueio de threads pelos serviços de depuração.  
  
 [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
 [Interface IGCHost2](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Fornece o método [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) que permite que um host defina o tamanho do segmento de coleta de lixo e o tamanho máximo da geração de zero do sistema de coleta de lixo com valores maiores que `DWORD`.  
  
 [Interface IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Fornece um método que permite que o coletor de lixo solicite o host para alterar os limites de memória virtual.  
  
 [Interface IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Fornece métodos para participar do agendamento de threads que, de outra forma, seriam bloqueados para coleta de lixo.  
  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Fornece métodos que permitem que um host especifique conjuntos de assemblies que devem ser carregados pelo CLR ou pelo host.  
  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Fornece métodos que permitem que um host carregue assemblies e módulos independentemente do CLR.  
  
 [Interface IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Fornece uma representação de um evento de redefinição automática implementado pelo host.  
  
 [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Fornece métodos para configurar o carregamento de assemblies e para determinar a quais interfaces de hospedagem o host dá suporte.  
  
 [Interface IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Serve como a representação do host de uma seção crítica para Threading.  
  
 [Interface IHostGCManager](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo CLR.  
  
 [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Fornece métodos que permitem que o CLR interaja com portas de conclusão de e/s fornecidas pelo host.  
  
 [Interface IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Fornece métodos para que o CLR solicite alocações refinadas do heap por meio do host.  
  
 [Interface IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Fornece a implementação do host de uma representação de um evento de redefinição manual.  
  
 [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Fornece métodos para que o CLR faça solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual Win32 padrão.  
  
 [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Fornece métodos que notificam o host das ações que o CLR executa em caso de anulações, tempos limite ou falhas.  
  
 [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Permite que o CLR mantenha informações de contexto de segurança implementadas pelo host.  
  
 [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Fornece métodos que habilitam o acesso e o controle sobre o contexto de segurança do thread em execução no momento.  
  
 [Interface IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Fornece uma representação de um semáforo implementado pelo host.  
  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Fornece métodos para que o CLR crie primitivos de sincronização chamando o host, em vez de usar as funções de sincronização do Win32.  
  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Fornece métodos que permitem que o CLR se comunique com o host para gerenciar tarefas.  
  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Fornece métodos que permitem que o CLR trabalhe com tarefas por meio do host em vez de usar as funções de fibra ou de Threading do sistema operacional padrão.  
  
 [Interface IHostThreadPoolManager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Fornece métodos para que o CLR configure o pool de threads e enfileirar itens de trabalho para o pool de threads.  
  
 [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Fornece métodos para controlar um objeto gerenciado.  
  
 "IObjectHandle"  
 Fornece um método para desencapsular objetos Marshal-by-Value do indireção.  
  
 [Interface ITypeName](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Fornece métodos para obter informações de nome de tipo. (Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)  
  
 [Interface ITypeNameBuilder](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Fornece métodos para criar um nome de tipo. (Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)  
  
 [Interface ITypeNameFactory](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Fornece métodos para decompor um nome de tipo. (Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)  
  
 IValidator  
 Fornece métodos para validar imagens executáveis portáteis (PE) e relatar erros de validação.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces e coclasses de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework versão 1,0 e 1,1.  
  
 [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework 4.
