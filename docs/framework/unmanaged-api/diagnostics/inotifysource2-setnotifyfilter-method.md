---
title: Método INotifySource2::SetNotifyFilter
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 554756bdda6e7167b013e7114e647f952cd1069d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435956"
---
# <a name="inotifysource2setnotifyfilter-method"></a>Método INotifySource2::SetNotifyFilter
Atribui um filtro de notificação para uso com esta origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `in_NotifyFilter`  
 no Uma combinação de bits bit a [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) valores de enumeração que identificam retornos de chamada para a API do depurador.  
  
 `in_pUserThreadFilter`  
 no Um ponteiro para uma estrutura de [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) que identifica threads para a API do depurador.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Consulte também

- [Interface INotifySource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interface INotifyConnection2](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
