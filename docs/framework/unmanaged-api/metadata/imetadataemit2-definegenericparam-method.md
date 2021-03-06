---
title: Método IMetaDataEmit2::DefineGenericParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444659"
---
# <a name="imetadataemit2definegenericparam-method"></a>Método IMetaDataEmit2::DefineGenericParam
Cria uma definição para um parâmetro de tipo genérico e Obtém um token para esse parâmetro de tipo genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 no Um `mdTypeDef` ou `mdMethodDef` token que representa o método ou construtor para o qual definir um parâmetro genérico.  
  
 `ulParamSeq`  
 no O índice do parâmetro genérico.  
  
 `dwParamFlags`  
 no Um valor da enumeração [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) que descreve o tipo para o parâmetro genérico.  
  
 `szname`  
 no O nome do parâmetro.  
  
 `reserved`  
 no Esse parâmetro é reservado para extensibilidade futura.  
  
 `rtkConstraints`  
 no Uma matriz de restrições de tipo terminada em zero. Os membros da matriz devem ser um `mdTypeDef`, `mdTypeRef`ou `mdTypeSpec` token de metadados.  
  
 `pgp`  
 fora Um token que representa o parâmetro genérico.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
