---
title: Interface ICorDebugManagedCallback2
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 97f103844c38ebd3dbff058bfe96ab953cdba960
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131468"
---
# <a name="icordebugmanagedcallback2-interface"></a>Interface ICorDebugManagedCallback2
Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica da interface [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Notifica o depurador de que o conjunto de tarefas associado à conexão especificada foi alterado.|  
|[Método CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Notifica o depurador de que uma nova conexão foi criada.|  
|[Método DestroyConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Notifica o depurador de que a conexão especificada foi encerrada.|  
|[Método Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Notifica o depurador de que uma pesquisa de um manipulador de exceção foi iniciada.|  
|[Método ExceptionUnwind](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Fornece uma notificação de status durante o processo de desenrolamento de exceções.|  
|[Método FunctionRemapComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Notifica o depurador de que a execução de código mudou para uma nova versão de uma função editada.|  
|[Método FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Notifica o depurador de que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.|  
|[Método MDANotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Fornece uma notificação de que a execução de código encontrou uma mensagem do assistente de depuração gerenciada (MDA).|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugManagedCallback2` estende a interface `ICorDebugManagedCallback` para manipular novos eventos de depuração introduzidos no .NET Framework versão 2,0.  
  
 Um depurador deve implementar `ICorDebugManagedCallback2` se estiver depurando .NET Framework aplicativos 2,0. Uma instância de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passada como o objeto de retorno de chamada para [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
