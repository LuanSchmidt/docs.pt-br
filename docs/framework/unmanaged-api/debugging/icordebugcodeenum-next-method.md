---
title: Método ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125521"
---
# <a name="icordebugcodeenumnext-method"></a>Método ICorDebugCodeEnum::Next

Obtém o número especificado de instâncias "ICorDebugCode" da enumeração, começando na posição atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>Parâmetros

`celt`  
no O número de instâncias de `ICorDebugCode` a serem recuperadas.

`values`  
fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto `ICorDebugCode`.

`pceltFetched`  
fora Um ponteiro para o número de instâncias de `ICorDebugCode` retornadas na verdade. Esse valor pode ser nulo se `celt` for um.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
