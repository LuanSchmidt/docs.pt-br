---
title: Método IMetaDataImport::GetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437063"
---
# <a name="imetadataimportgetpropertyprops-method"></a>Método IMetaDataImport::GetPropertyProps
Obtém os metadados para a propriedade representada pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `prop`  
 no Um token que representa a propriedade para a qual retornar metadados.  
  
 `pClass`  
 fora Um ponteiro para o token de TypeDef que representa o tipo que implementa a propriedade.  
  
 `szProperty`  
 fora Um buffer para armazenar o nome da propriedade.  
  
 `cchProperty`  
 no O tamanho em caracteres largos de `szProperty`.  
  
 `pchProperty`  
 fora O número de caracteres largos retornados em `szProperty`.  
  
 `pdwPropFlags`  
 fora Um ponteiro para qualquer sinalizador de atributo aplicado à propriedade. Esse valor é um bitmask da enumeração [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) .  
  
 `ppvSig`  
 fora Um ponteiro para a assinatura de metadados da propriedade.  
  
 `pbSig`  
 fora O número de bytes retornados em `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 fora Um sinalizador que especifica o tipo da constante que é o valor padrão da propriedade. Esse valor é da enumeração CorElementType.  
  
 `ppDefaultValue`  
 fora Um ponteiro para os bytes que armazenam o valor padrão para essa propriedade.  
  
 `pcchDefaultValue`  
 fora O tamanho em caracteres largos de `ppDefaultValue`, se `pdwCPlusTypeFlag` for ELEMENT_TYPE_STRING; caso contrário, esse valor não será relevante. Nesse caso, o comprimento de `ppDefaultValue` é inferido do tipo especificado por `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 fora Um ponteiro para o token MethodDef que representa o método de acessador set para a propriedade.  
  
 `pmdGetter`  
 fora Um ponteiro para o token MethodDef que representa o método acessador get para a propriedade.  
  
 `rmdOtherMethod`  
 fora Uma matriz de tokens MethodDef que representa outros métodos associados à propriedade.  
  
 `cMax`  
 no O tamanho máximo da matriz de `rmdOtherMethod`. Se você não fornecer uma matriz grande o suficiente para manter todos os métodos, eles serão ignorados sem aviso.  
  
 `pcOtherMethod`  
 fora O número de tokens MethodDef retornados em `rmdOtherMethod`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
