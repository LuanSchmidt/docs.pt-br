---
title: Função _CorValidateImage
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 42da5bb761ba8ce388bd41d46e8fdc4561ad0290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136878"
---
# <a name="_corvalidateimage-function"></a>Função _CorValidateImage
Valida as imagens de módulo gerenciado e notifica o carregador do sistema operacional depois que elas tiverem sido carregadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ImageBase`  
 no Um ponteiro para o local inicial da imagem a ser validada como código gerenciado. A imagem já deve estar carregada na memória.  
  
 `FileName`  
 no O nome do arquivo da imagem.  
  
## <a name="return-value"></a>Valor retornado  
 Essa função retorna os valores padrão `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`e `E_FAIL`, bem como os valores a seguir.  
  
|Valor retornado|Descrição|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|A imagem é inválida. Esse valor tem o HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|A imagem é válida. Esse valor tem o HRESULT 0x00000000l.|  
  
## <a name="remarks"></a>Comentários  
 No Windows XP e versões posteriores, o carregador do sistema operacional verifica módulos gerenciados examinando o bit do diretório do descritor COM no cabeçalho COFF (Common Object File Format). Um bit definido indica um módulo gerenciado. Se o carregador detectar um módulo gerenciado, ele carregará o MsCorEE. dll e chamará `_CorValidateImage`, que executará as seguintes ações:  
  
- Confirma que a imagem é um módulo gerenciado válido.  
  
- Altera o ponto de entrada na imagem para um ponto de entrada no Common Language Runtime (CLR).  
  
- Para versões de 64 bits do Windows, o modifica a imagem que está na memória transformando-a de PE32 para PE32 + Format.  
  
- Retorna ao carregador quando as imagens de módulo gerenciado são carregadas.  
  
 Para imagens executáveis, o carregador do sistema operacional chama a função [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) , independentemente do ponto de entrada especificado no executável. Para imagens de assembly de DLL, o carregador chama a função [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) .  
  
 `_CorExeMain` ou `_CorDllMain` executa as seguintes ações:  
  
- Inicializa o CLR.  
  
- Localiza o ponto de entrada gerenciado do cabeçalho CLR do assembly.  
  
- Inicia a execução.  
  
 O carregador chama a função [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) quando as imagens de módulo gerenciado são descarregadas. No entanto, essa função não executa nenhuma ação; Ele apenas retorna.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
