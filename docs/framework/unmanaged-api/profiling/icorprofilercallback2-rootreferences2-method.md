---
title: Método ICorProfilerCallback2::RootReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: dffd4365669da61f7b321110ad663c131ce591e6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439674"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>Método ICorProfilerCallback2::RootReferences2
Notifica o criador de perfil sobre referências de raiz após a ocorrência de uma coleta de lixo. Esse método é uma extensão do método [ICorProfilerCallback:: RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 no O número de elementos nas matrizes `rootRefIds`, `rootKinds`, `rootFlags`e `rootIds`.  
  
 `rootRefIds`  
 no Uma matriz de IDs de objeto, cada uma das quais faz referência a um objeto estático ou a um objeto na pilha. Os elementos na matriz de `rootKinds` fornecem informações para classificar os elementos correspondentes na matriz de `rootRefIds`.  
  
 `rootKinds`  
 no Uma matriz de valores [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) que indicam o tipo da raiz da coleta de lixo.  
  
 `rootFlags`  
 no Uma matriz de valores [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) que descrevem as propriedades de uma raiz de coleta de lixo.  
  
 `rootIds`  
 no Uma matriz de valores UINT_PTR que apontam para um inteiro que contém informações adicionais sobre a raiz da coleta de lixo, dependendo do valor do parâmetro `rootKinds`.  
  
 Se o tipo da raiz for uma pilha, a ID raiz será para a função que contém a variável. Se essa ID raiz for 0, a função será uma função sem nome que é interna ao CLR. Se o tipo da raiz for um identificador, a ID raiz será para o identificador de coleta de lixo. Para os outros tipos de raiz, a ID é um valor opaco e deve ser ignorada.  
  
## <a name="remarks"></a>Comentários  
 As matrizes `rootRefIds`, `rootKinds`, `rootFlags`e `rootIds` são matrizes paralelas. Ou seja, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`e `rootIds[i]` todos se referem à mesma raiz.  
  
 Tanto `RootReferences` quanto `RootReferences2` são chamados para notificar o criador de perfil. Os profileres normalmente implementarão um método ou o outro, mas não ambos, porque as informações transmitidas `RootReferences2` são um superconjunto do passado `RootReferences`.  
  
 É possível que as entradas em `rootRefIds` sejam zero, o que implica que a referência raiz correspondente é nula e não se refere a um objeto no heap gerenciado.  
  
 As IDs de objeto retornadas por `RootReferences2` não são válidas durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos de endereços antigos para novos endereços. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`. Quando [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e podem ser inspecionados com segurança.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
