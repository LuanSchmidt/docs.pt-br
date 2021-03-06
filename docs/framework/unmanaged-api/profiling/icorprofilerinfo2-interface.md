---
title: Interface ICorProfilerInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: fdac9eedb0ae442d6dd2646859cab13398020a87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449779"
---
# <a name="icorprofilerinfo2-interface"></a>Interface ICorProfilerInfo2
Fornece métodos que os profileres de código usam para se comunicar com o Common Language Runtime (CLR) para controlar o monitoramento de eventos e informações de solicitação. A interface `ICorProfilerInfo2` é uma extensão da interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) . Ou seja, ele fornece novos métodos com suporte no .NET Framework versão 2,0 e versões posteriores.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Percorre a pilha do thread especificado para relatar os quadros de chamada gerenciados ao criador de perfil.|  
|[Método EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Obtém um enumerador que permite a iteração sobre os objetos congelados no módulo especificado.|  
|[Método GetAppDomainStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Obtém o endereço do campo de domínio estático do aplicativo especificado que está no escopo do domínio do aplicativo especificado.|  
|[Método GetArrayObjectInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Obtém informações detalhadas sobre um objeto de matriz.|  
|[Método GetBoxClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Obtém informações sobre o layout de classe para um tipo de valor especificado que é boxed.|  
|[Método GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Obtém a `ClassID` de um tipo usando o token de metadados especificado e os valores de `ClassID` de qualquer argumento de tipo.|  
|[Método GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Obtém o módulo pai da classe genérica especificada, o token de metadados para a classe, a `ClassID` de sua classe pai e a `ClassID` para cada argumento de tipo, se presente, da classe.|  
|[Método GetClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Obtém informações sobre o layout, na memória, dos campos definidos pela classe especificada. Ou seja, esse método obtém os deslocamentos dos campos da classe.|  
|[Método GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Obtém as extensões do código nativo associado ao `FunctionID`especificado.|  
|[Método GetContextStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Obtém o endereço do campo estático de contexto especificado que está no escopo do contexto especificado.|  
|[Método GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Obtém a `FunctionID` de uma função usando o token de metadados especificado, contendo a classe e valores de `ClassID` de qualquer argumento de tipo.|  
|[Método GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Obtém a classe pai, o token de metadados e a `ClassID` de cada argumento de tipo, se presente, de uma função.|  
|[Método GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Obtém as regiões de memória (os segmentos do heap) que compõem as gerações do heap coletado por lixo.|  
|[Método GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Obtém as informações de endereço nativo e de quadro da cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executada ou que acabou de ser executada.|  
|[Método GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Obtém o segmento do heap que contém o objeto especificado.|  
|[Método GetRVAStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Obtém o endereço do campo de endereço virtual relativo (RVA)-estático especificado.|  
|[Método GetStaticFieldInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Obtém o escopo no qual o campo especificado é estático.|  
|[Método GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Obtém informações sobre o layout de um objeto de cadeia de caracteres.|  
|[Método GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Obtém a ID do domínio do aplicativo no qual o thread especificado está executando o código no momento.|  
|[Método GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Obtém o endereço do campo de thread estático especificado que está no escopo do thread especificado.|  
|[Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.|  
  
## <a name="remarks"></a>Comentários  
 Um criador de perfil chama um método na interface `ICorProfilerInfo2` para se comunicar com o CLR para controlar as informações de solicitação e monitoramento de eventos.  
  
 Os métodos da interface `ICorProfilerInfo2` são implementados pelo CLR usando o modelo de thread livre. Cada método retorna um HRESULT para indicar êxito ou falha. Para obter uma lista de possíveis códigos de retorno, consulte o arquivo CorError. h.  
  
 O CLR passa uma interface `ICorProfilerInfo2` para cada criador de perfil de código durante a inicialização, usando a implementação do criador de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Um criador de perfil de código pode então chamar métodos da interface `ICorProfilerInfo2` para obter informações sobre o código gerenciado que está sendo executado sob o controle do CLR.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
