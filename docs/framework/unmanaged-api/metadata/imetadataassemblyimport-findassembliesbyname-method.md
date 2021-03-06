---
title: Método IMetaDataAssemblyImport::FindAssembliesByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448293"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>Método IMetaDataAssemblyImport::FindAssembliesByName
Obtém uma matriz de assemblies com o parâmetro de `szAssemblyName` especificado, usando as regras padrão empregadas pelo Common Language Runtime (CLR) para resolver referências.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szAppBase`  
 no O diretório raiz no qual Pesquisar o assembly fornecido. Se esse valor for definido como `null`, `FindAssembliesByName` procurará apenas no cache de assembly global para o assembly.  
  
 `szPrivateBin`  
 no Uma lista de subdiretórios delimitados por ponto-e-vírgula (por exemplo, "bin; BIN2"), sob o diretório raiz, no qual Pesquisar o assembly. Esses diretórios são investigados além daqueles especificados nas regras de investigação padrão.  
  
 `szAssemblyName`  
 no O nome do assembly a ser localizado. O formato dessa cadeia de caracteres é definido na página de referência de classe para <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 no Uma matriz do tipo [IUnknown](/cpp/atl/iunknown) na qual colocar os ponteiros de interface `IMetadataAssemblyImport`.  
  
 `cMax`  
 fora O número máximo de ponteiros de interface que podem ser colocados em `ppIUnk`.  
  
 `pcAssemblies`  
 fora O número de ponteiros de interface retornados. Ou seja, o número de ponteiros de interface realmente colocados em `ppIUnk`.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` retornado com êxito.|  
|`S_FALSE`|Não há assemblies.|  
  
## <a name="remarks"></a>Comentários  
 Dado um nome de assembly, o método `FindAssembliesByName` localiza o assembly seguindo as regras padrão para resolver referências de assembly. (Para obter mais informações, consulte [como o tempo de execução localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permite que o chamador configure vários aspectos do contexto do resolvedor de assembly, como a base do aplicativo e o caminho de pesquisa particular.  
  
 O método `FindAssembliesByName` requer que o CLR seja inicializado no processo para invocar a lógica de resolução do assembly. Portanto, você deve chamar o [codeinitialize](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passando COINITEE_DEFAULT) antes de chamar `FindAssembliesByName`e, em seguida, seguir com uma chamada para [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` retorna um ponteiro [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) para o arquivo que contém o manifesto do assembly para o nome do assembly que é passado. Se o nome do assembly fornecido não estiver totalmente especificado (por exemplo, se não incluir uma versão), vários assemblies poderão ser retornados.  
  
 `FindAssembliesByName` normalmente é usado por um compilador que tenta localizar um assembly referenciado no momento da compilação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Como o runtime localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
