---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901970"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depende das [bibliotecas de armazenamento do Azure](https://github.com/Azure/azure-storage-net). Essas bibliotecas renomeam seus assemblies, pacotes e namespaces. A partir do ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` usa os novos pacotes e APIs prefixados `Microsoft.Azure.Storage.`.

Para perguntas sobre as APIs de armazenamento do Azure, use <https://github.com/Azure/azure-storage-net>. Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote referenciou o `WindowsAzure.Storage` pacote NuGet.

#### <a name="new-behavior"></a>Novo comportamento

O pacote faz referência ao pacote NuGet `Microsoft.Azure.Storage.Blob`.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração permite que `Microsoft.AspNetCore.DataProtection.AzureStorage` migrem para os pacotes de armazenamento do Azure recomendados.

#### <a name="recommended-action"></a>Ação recomendada

Se você ainda precisar usar as APIs mais antigas do armazenamento do Azure com o ASP.NET Core 3,0, adicione uma dependência direta ao pacote [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Esse pacote pode ser instalado junto com as novas APIs de `Microsoft.Azure.Storage`.

Em muitos casos, a atualização envolve apenas a alteração das instruções `using` para usar os novos namespaces:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

{1&gt;Nenhum&lt;1}

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
