---
title: Instalar o .NET Core no Linux RHEL 8,1 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8781d6bd14daf975fcc602fd2924a333750d4256
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714384"
---
# <a name="rhel-81-package-manager---install-net-core"></a>Gerenciador de pacotes RHEL 8,1 – instalar o .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no RHEL 8,1. O .NET Core 3,1 ainda não está disponível para o RHEL 8,1.

> [!NOTE]
> O RHEL 8,0 não inclui o .NET Core 3,0. Use o comando `yum upgrade` para atualizar para RHEL 8,1.

## <a name="register-your-red-hat-subscription"></a>Registrar sua assinatura do Red Hat

Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat. Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o SDK do .NET Core. Em seu terminal, execute os comandos a seguir.

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalar o ASP.NET Core Runtime

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução de ASP.NET Core. Em seu terminal, execute os comandos a seguir.

```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução do .NET Core. Em seu terminal, execute os comandos a seguir.

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a>Veja também

- [Usando o .NET Core 3,0 no Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
