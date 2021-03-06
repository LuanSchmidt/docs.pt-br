---
title: 'Como: Animar a posição ou cor de uma parada de gradiente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: 4762233cace895c9d492fb426f3f6be14498ad53
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593367"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Como: Animar a posição ou cor de uma parada de gradiente
Este exemplo mostra como animar a <xref:System.Windows.Media.GradientStop.Color%2A> e <xref:System.Windows.Media.GradientStop.Offset%2A> de <xref:System.Windows.Media.GradientStop> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima três marcas de gradiente dentro de um <xref:System.Windows.Media.LinearGradientBrush>. O exemplo usa três animações, cada qual animando uma marca de gradiente diferente:  
  
- A primeira animação, um <xref:System.Windows.Media.Animation.DoubleAnimation>, anima a primeira parada gradiente <xref:System.Windows.Media.GradientStop.Offset%2A> de 0,0 a 1,0 e, em seguida, volta a 0.0. Como resultado, a primeira cor do gradiente muda do lado esquerdo para o lado direito do retângulo e, em seguida, volta para o lado esquerdo.  
  
- A segunda animação, um <xref:System.Windows.Media.Animation.ColorAnimation>, anima a parada de gradiente segundo <xref:System.Windows.Media.GradientStop.Color%2A> partir <xref:System.Windows.Media.Colors.Purple%2A> para <xref:System.Windows.Media.Colors.Yellow%2A> e, em seguida, de volta para <xref:System.Windows.Media.Colors.Purple%2A>. Como resultado, a cor intermediária do gradiente muda de roxo para amarelo e de volta para roxo.  
  
- A terceira animação, outro <xref:System.Windows.Media.Animation.ColorAnimation>, anima a opacidade da parada de gradiente terceiro <xref:System.Windows.Media.GradientStop.Color%2A> por -1 e, em seguida, de volta. Como resultado, a terceira cor do gradiente desaparece e, em seguida, se torna opaca novamente.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Embora este exemplo usa uma <xref:System.Windows.Media.LinearGradientBrush>, o processo é o mesmo para animar <xref:System.Windows.Media.GradientStop> objetos dentro de um <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Para obter exemplos adicionais, consulte o [Exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.GradientStop>
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
