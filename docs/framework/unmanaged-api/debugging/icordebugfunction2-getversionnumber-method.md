---
title: Método ICorDebugFunction2::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137799"
---
# <a name="icordebugfunction2getversionnumber-method"></a>Método ICorDebugFunction2::GetVersionNumber
Obtém a versão editar e continuar desta função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pnVersion`  
 fora Um ponteiro para um inteiro que é o número de versão da função que é representada por esse objeto ICorDebugFunction2.  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução controla o número de edições que foram feitas em cada módulo durante uma sessão de depuração. O número de versão de uma função é mais um que o número da edição que introduziu a função. A versão original da função é a versão 1. O número é incrementado para um módulo toda vez que [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) é chamado nesse módulo. Portanto, se o corpo de uma função foi substituído na primeira e terceira chamada para `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` pode retornar a versão 1, 2 ou 4 para essa função, mas não a versão 3. (Essa função não teria nenhuma versão 3.)  
  
 O número de versão é acompanhado separadamente para cada módulo. Portanto, se você executar quatro edições no módulo 1 e nenhum no módulo 2, a próxima edição no módulo 1 atribuirá um número de versão de 6 a todas as funções editadas no módulo 1. Se os mesmos toques de edição do módulo 2, as funções no módulo 2 receberão um número de versão 2.  
  
 O número de versão obtido pelo método `GetVersionNumber` pode ser menor que o obtido por [ICorDebugFunction:: GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 O método [ICorDebugCode:: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) executa a mesma operação que `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
