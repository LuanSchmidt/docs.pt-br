---
title: Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: ec265525d01dab0669939569501fce91b500a900
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127500"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
Retorna o thread gerenciado que possui o bloqueio de monitor neste objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppThread`  
 fora O thread gerenciado que possui o bloqueio de monitor neste objeto.  
  
 `pAcquisitionCount`  
 fora O número de vezes que esse thread teria que liberar o bloqueio antes que ele retorne sem proprietário.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|S_FALSE|Nenhum thread gerenciado possui o bloqueio de monitor neste objeto.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Se um thread gerenciado possuir o bloqueio de monitor neste objeto:  
  
- O método retorna S_OK.  
  
- O objeto de thread é válido até que o thread saia.  
  
 Se nenhum thread gerenciado possuir o bloqueio de monitor nesse objeto, `ppThread` e `pAcquisitionCount` não serão alterados e o método retornará S_FALSE.  
  
 Se `ppThread` ou `pAcquisitionCount` não for um ponteiro válido, o resultado será indefinido.  
  
 Se ocorrer um erro de modo que não possa ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retornará um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
