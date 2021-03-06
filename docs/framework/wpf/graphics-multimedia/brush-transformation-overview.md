---
title: Visão geral da transformação de pincel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: 39b3ad9bebfc56002f77ad6e9026a4446c95455b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020583"
---
# <a name="brush-transformation-overview"></a>Visão geral da transformação de pincel
A classe pincel fornece duas propriedades de transformação: <xref:System.Windows.Media.Brush.Transform%2A> e <xref:System.Windows.Media.Brush.RelativeTransform%2A>. As propriedades permitem que você gire, ajuste a escala, distorça e traduza o conteúdo do pincel. Este tópico descreve as diferenças entre essas duas propriedades e fornece exemplos de uso.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve compreender os recursos do pincel que está transformando. Para <xref:System.Windows.Media.LinearGradientBrush> e <xref:System.Windows.Media.RadialGradientBrush>, consulte o [pintura com cores sólidas e gradientes Overview](painting-with-solid-colors-and-gradients-overview.md). Para <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, ou <xref:System.Windows.Media.VisualBrush>, consulte [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md). Você também deve estar familiarizado com transformações 2D descritas em [Transforms Overview](transforms-overview.md) (Visão geral de transformações).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Diferenças entre as propriedades Transformação e RelativeTransform  
 Quando você aplica uma transformação a um pincel <xref:System.Windows.Media.Brush.Transform%2A> propriedade, você precisa saber o tamanho da área pintada se você quiser transformar o conteúdo do pincel sobre seu centro. Suponha que a área pintada tenha 200 pixels independentes de dispositivo de largura e 150 de altura.  Se você tiver usado uma <xref:System.Windows.Media.RotateTransform> para girar o pincel a saída de 45 graus sobre seu centro, você daria a <xref:System.Windows.Media.RotateTransform> um <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 100 e uma <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 75.  
  
 Quando você aplica uma transformação a um pincel <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade, essa transformação é aplicada ao pincel antes que sua saída seja mapeada para a área pintada. A lista a seguir descreve a ordem em que os conteúdos de um pincel são processados e transformados.  
  
1. Processar o conteúdo do pincel. Para um <xref:System.Windows.Media.GradientBrush>, isso significa determinar a área do gradiente. Para um <xref:System.Windows.Media.TileBrush>, o <xref:System.Windows.Media.TileBrush.Viewbox%2A> é mapeado para o <xref:System.Windows.Media.TileBrush.Viewport%2A>. Ele se torna a saída do pincel.  
  
2. Projete a saída do pincel para o retângulo de transformação 1 x 1.  
  
3. Aplique o pincel <xref:System.Windows.Media.Brush.RelativeTransform%2A>, se ele tiver um.  
  
4. Projete a saída transformada na área pintada.  
  
5. Aplique o pincel <xref:System.Windows.Media.Transform>, se ele tiver um.  
  
 Porque o <xref:System.Windows.Media.Brush.RelativeTransform%2A> é aplicado enquanto a saída do pincel é mapeada para um retângulo 1 x 1, o Centro de transformação e valores de deslocamento parecem ser relativos. Por exemplo, se você tiver usado uma <xref:System.Windows.Media.RotateTransform> para girar o pincel a saída de 45 graus sobre seu centro, você daria a <xref:System.Windows.Media.RotateTransform> um <xref:System.Windows.Media.RotateTransform.CenterX%2A> de 0,5 e um <xref:System.Windows.Media.RotateTransform.CenterY%2A> de 0,5.  
  
 A ilustração a seguir mostra a saída de diversos pincéis que foram girados em 45 graus usando as <xref:System.Windows.Media.Brush.RelativeTransform%2A> e <xref:System.Windows.Media.Brush.Transform%2A> propriedades.  
  
 ![Propriedades RelativeTransform e Transformação](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Utilizando RelativeTransform com um TileBrush  
 Como pincéis de bloco são mais complexos que outros pincéis, aplicar um <xref:System.Windows.Media.Brush.RelativeTransform%2A> a um pode produzir resultados inesperados. Por exemplo, considere a seguinte imagem.  
  
 ![A imagem de origem](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.ImageBrush> para pintar uma área retangular com a imagem anterior. Ele se aplica um <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.Media.ImageBrush> do objeto <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade e define seu <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade para <xref:System.Windows.Media.Stretch.UniformToFill>, que deve preservar a proporção da imagem quando redimensionado para preencher completamente o retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Este exemplo gera a seguinte saída:  
  
 ![A saída transformada](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Observe que a imagem é distorcida, mesmo que o pincel <xref:System.Windows.Media.TileBrush.Stretch%2A> foi definido como <xref:System.Windows.Media.Stretch.UniformToFill>. Isso ocorre porque a transformação relativa é aplicada após o pincel <xref:System.Windows.Media.TileBrush.Viewbox%2A> é mapeado para seu <xref:System.Windows.Media.TileBrush.Viewport%2A>. A lista a seguir descreve cada etapa do processo:  
  
1. O conteúdo do pincel de projeto (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) em seu bloco base (<xref:System.Windows.Media.TileBrush.Viewport%2A>) usando o pincel <xref:System.Windows.Media.TileBrush.Stretch%2A> configuração.  
  
     ![Alongue o Viewbox para ajustar o visor](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Projete a saída do bloco base para o retângulo de transformação 1 x 1.  
  
     ![Mapeie o visor para o retângulo de transformação](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Aplicar o <xref:System.Windows.Media.RotateTransform>.  
  
     ![Aplique a transformação relativa](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Projete o bloco base transformado na área pintada.  
  
     ![Projete o pincel transformado na área de saída](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Exemplo: Gire um ImageBrush 45 graus  
 O exemplo a seguir aplica uma <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade de um <xref:System.Windows.Media.ImageBrush>. O <xref:System.Windows.Media.RotateTransform> do objeto <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades são definidas como 0,5, as coordenadas relativas do centro do conteúdo do ponto. Como resultado, o conteúdo do pincel é girado em torno de seu centro.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 O exemplo a seguir também se aplica uma <xref:System.Windows.Media.RotateTransform> para um <xref:System.Windows.Media.ImageBrush>, mas usa o <xref:System.Windows.Media.Brush.Transform%2A> propriedade em vez do <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade. Para girar o pincel sobre seu centro, o <xref:System.Windows.Media.RotateTransform> do objeto <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> deve ser definida como coordenadas absolutas. Como o retângulo que está sendo pintado pelo pincel tem 175 x 90 pixels, seu ponto central é (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 A ilustração a seguir mostra o pincel sem uma transformação, com a transformação aplicada para o <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriedade e com a transformação aplicada para o <xref:System.Windows.Media.Brush.Transform%2A> propriedade.  
  
 ![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Este exemplo é parte de um exemplo maior. Para obter o exemplo completo, consulte [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973) (Exemplo de pincéis). Para obter mais informações sobre pincéis, consulte [WPF Brushes Overview](wpf-brushes-overview.md) (Visão geral de pincéis do WPF).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Visão geral de transformações](transforms-overview.md)
