---
title: Alterações significativas de criptografia-.NET Core
description: Lista as alterações relacionadas à criptografia de interrupção no .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: 4b13985a12ee0530edd3a0960923aafef1696d90
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116471"
---
# <a name="cryptography-breaking-changes"></a>Alterações significativas de criptografia

As seguintes alterações significativas estão documentadas nesta página:

- [EnvelopedCms usa como padrão a criptografia AES-256](#envelopedcms-defaults-to-aes-256-encryption)
- [O tamanho mínimo para geração de chave RSAOpenSsl aumentou](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
