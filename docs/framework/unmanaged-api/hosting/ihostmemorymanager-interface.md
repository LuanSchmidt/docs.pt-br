---
title: Interface IHostMemoryManager
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128656"
---
# <a name="ihostmemorymanager-interface"></a>Interface IHostMemoryManager
Fornece métodos que permitem que o Common Language Runtime (CLR) faça solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual Win32 padrão.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AcquiredVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Notifica o host de que o Common Language Runtime (CLR) adquiriu a memória especificada do sistema operacional.|  
|[Método CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Obtém um ponteiro de interface para uma instância de [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) que é usada para solicitar alocações de memória de um heap criado pelo host.|  
|[Método GetMemoryLoad](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Obtém a quantidade de memória física que está sendo usada no momento, conforme relatado pelo host.|  
|[Método NeedsVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Notifica o host que o CLR vai tentar usar a memória especificada.|  
|[Método RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Registra um ponteiro para uma função de retorno de chamada que o host chama para notificar o CLR sobre a carga de memória atual no computador.|  
|[Método ReleasedVirtualAddressSpace](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Notifica o host que o CLR concluiu usando a memória especificada.|  
|[Método VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Serve como um wrapper lógico para a função Win32 correspondente, que reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.|  
|[Método VirtualFree](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Serve como um wrapper lógico para a função Win32 correspondente, que libera, desconfirma ou libera e desconfirma uma região de páginas dentro do espaço de endereço virtual do processo de chamada.|  
|[Método VirtualProtect](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Serve como um wrapper lógico para a função Win32 correspondente, que altera a proteção em uma região de páginas confirmadas no espaço de endereço virtual do processo de chamada.|  
|[Método VirtualQuery](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Serve como um wrapper lógico para a função Win32 correspondente, que recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.|  
  
## <a name="remarks"></a>Comentários  
 o `IHostMemoryManager` também fornece métodos para o CLR obter um ponteiro por meio do qual fazer solicitações de memória no heap e obter o nível de pressão de memória no processo, conforme relatado pelo host.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
