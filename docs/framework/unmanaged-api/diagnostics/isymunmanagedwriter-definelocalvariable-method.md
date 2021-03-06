---
title: Método ISymUnmanagedWriter::DefineLocalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: f6a741df3ea57b5e9b4fa8bc5d304bfedd1d6c15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428015"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>Método ISymUnmanagedWriter::DefineLocalVariable
Define uma única variável no escopo léxico atual. Esse método pode ser chamado várias vezes para uma variável do mesmo nome que tem várias casas em um escopo. Nesse caso, no entanto, os valores dos parâmetros `startOffset` e `endOffset` não devem se sobrepor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 no Um ponteiro para um `WCHAR` que define o nome da variável local.  
  
 `attributes`  
 no Os atributos da variável local.  
  
 `cSig`  
 no Um `ULONG32` que indica o tamanho, em bytes, do buffer de `signature`.  
  
 `signature`  
 no A assinatura da variável local.  
  
 `addrKind`  
 no O tipo de endereço.  
  
 `addr1`  
 no O primeiro endereço para a especificação de parâmetro.  
  
 `addr2`  
 no O segundo endereço para a especificação de parâmetro.  
  
 `addr3`  
 no O terceiro endereço para a especificação de parâmetro.  
  
 `startOffset`  
 no O deslocamento de início da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo. Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.  
  
 `endOffset`  
 no O deslocamento de fim da variável. Esse parâmetro é opcional. Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo. Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Método DefineGlobalVariable](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [Método DefineLocalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
