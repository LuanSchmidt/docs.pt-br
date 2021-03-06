---
title: Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 4068c8fee13a6086bc6b48bcc6d4117357062747
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449788"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
Especifica as funções implementadas pelo Profiler a serem chamadas nas versões atualizadas dos ganchos "Enter", "sair" e "tailcall" das funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .  
  
 `pFuncLeave`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .  
  
 `pFuncTailcall`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .  
  
## <a name="remarks"></a>Comentários  
 O método `SetEnterLeaveFunctionHooks2` é semelhante ao método [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) . Use o primeiro para especificar funções a serem usadas como versões mais recentes dos retornos de chamada enter/leave/tailcall e a última para especificar as funções a serem usadas como versões mais antigas dos retornos de chamada enter/leave/tailcall.  
  
 Somente um conjunto de retornos de chamada pode estar ativo por vez. Portanto, se um criador de perfil chamar `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` será usado.  
  
 O método `SetEnterLeaveFunctionHooks2` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) do criador de perfil.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
