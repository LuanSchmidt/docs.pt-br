---
title: 'Como: Reproduzir um som do sistema de um Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: 765021875767a754e62e3ec11e56487e4de91e93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602772"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Como: Reproduzir um som do sistema de um Windows Form
O código a seguir exemplo reproduz o `Exclamation` som do sistema em tempo de execução. Para obter mais informações sobre os sons do sistema, consulte <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Exemplo  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [Como: Executar um bipe de um formulário do Windows](how-to-play-a-beep-from-a-windows-form.md)
- [Como: Reproduzir um som de um formulário do Windows](how-to-play-a-sound-from-a-windows-form.md)
