---
title: Pintando com imagens, desenhos e visuais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929604"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Pintando com imagens, desenhos e visuais
Este <xref:System.Windows.Media.ImageBrush>tópico descreve como usar objetos, <xref:System.Windows.Media.DrawingBrush>e <xref:System.Windows.Media.VisualBrush> para pintar uma área com uma imagem, um <xref:System.Windows.Media.Drawing>ou um <xref:System.Windows.Media.Visual>.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de pincéis que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece e seus recursos básicos. Para uma introdução, consulte a [Visão geral de pincéis do WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Pintar uma área com uma imagem  
 Um <xref:System.Windows.Media.ImageBrush> pinta uma área com um <xref:System.Windows.Media.ImageSource>. O tipo mais comum de <xref:System.Windows.Media.ImageSource> ser usado com um <xref:System.Windows.Media.ImageBrush> é um <xref:System.Windows.Media.Imaging.BitmapImage>, que descreve um gráfico de bitmap. Você pode usar um <xref:System.Windows.Media.DrawingImage> para pintar usando um <xref:System.Windows.Media.Drawing> objeto, mas é mais simples usar um <xref:System.Windows.Media.DrawingBrush> em vez disso. Para obter mais informações <xref:System.Windows.Media.ImageSource> sobre objetos, consulte [visão geral da geração de imagens](imaging-overview.md).  
  
 Para pintar com um <xref:System.Windows.Media.ImageBrush>, crie um <xref:System.Windows.Media.Imaging.BitmapImage> e use-o para carregar o conteúdo do bitmap. Em seguida, use <xref:System.Windows.Media.Imaging.BitmapImage> o para definir <xref:System.Windows.Media.ImageBrush.ImageSource%2A> a propriedade do <xref:System.Windows.Media.ImageBrush>. Por fim, aplique <xref:System.Windows.Media.ImageBrush> o ao objeto que você deseja pintar.  No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você também pode apenas definir a <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade de <xref:System.Windows.Media.ImageBrush> com o caminho da imagem a ser carregada.  
  
 Como todos <xref:System.Windows.Media.Brush> os objetos, <xref:System.Windows.Media.ImageBrush> um pode ser usado para pintar objetos, como formas, painéis, controles e texto. A ilustração a seguir mostra alguns efeitos que podem ser obtidos com <xref:System.Windows.Media.ImageBrush>um.  
  
 ![Exemplos de saída de ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objetos pintados por um ImageBrush  
  
 Por padrão, um <xref:System.Windows.Media.ImageBrush> amplia sua imagem para preencher completamente a área que está sendo pintada, possivelmente distorcendo a imagem se a área pintada tiver uma taxa de proporção diferente da imagem. Você pode alterar esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de seu valor padrão de <xref:System.Windows.Media.Stretch.Fill> para <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>ou <xref:System.Windows.Media.Stretch.UniformToFill>. Como <xref:System.Windows.Media.ImageBrush> é um tipo de <xref:System.Windows.Media.TileBrush>, você pode especificar exatamente como um pincel de imagem preenche a área de saída e até mesmo cria padrões. Para obter mais informações sobre <xref:System.Windows.Media.TileBrush> recursos avançados, consulte a [visão geral do TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Exemplo: Pintar um objeto com uma imagem de bitmap  
 O exemplo a seguir usa <xref:System.Windows.Media.ImageBrush> um para pintar <xref:System.Windows.Controls.Panel.Background%2A> o de <xref:System.Windows.Controls.Canvas>um.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Pintar uma área com um desenho  
 Um <xref:System.Windows.Media.DrawingBrush> permite que você pinte uma área com formas, texto, imagens e vídeo. As formas dentro de um pincel de desenho podem ser pintadas com uma cor sólida, gradiente, imagem <xref:System.Windows.Media.DrawingBrush>ou até mesmo outra. A ilustração a seguir demonstra alguns usos de <xref:System.Windows.Media.DrawingBrush>um.  
  
 ![Exemplos de saída de DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objetos pintados por um DrawingBrush  
  
 Um <xref:System.Windows.Media.DrawingBrush> pinta uma área com um <xref:System.Windows.Media.Drawing> objeto. Um <xref:System.Windows.Media.Drawing> objeto descreve o conteúdo visível, como uma forma, bitmap, vídeo ou uma linha de texto. Diferentes tipos de desenhos descrevem diferentes tipos de conteúdo. A seguir está uma lista dos diferentes tipos de objetos de desenho.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Desenha uma forma.  
  
- <xref:System.Windows.Media.ImageDrawing>– Desenha uma imagem.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Desenha texto.  
  
- <xref:System.Windows.Media.VideoDrawing>– Reproduz um arquivo de áudio ou de vídeo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Desenha outros desenhos. Use um grupo de desenhos para combinar outros desenhos em um único desenho composto.  
  
 Para obter mais informações <xref:System.Windows.Media.Drawing> sobre objetos, consulte a [visão geral de objetos de desenho](drawing-objects-overview.md).  
  
 Como um <xref:System.Windows.Media.ImageBrush>, um <xref:System.Windows.Media.DrawingBrush> amplia seu <xref:System.Windows.Media.DrawingBrush.Drawing%2A> para preencher sua área de saída. Você pode substituir esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de sua configuração padrão de <xref:System.Windows.Media.Stretch.Fill>. Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Exemplo: Pintar um objeto com um desenho  
 O exemplo a seguir mostra como pintar um objeto com um desenho de três elipses. Um <xref:System.Windows.Media.GeometryDrawing> é usado para descrever as reticências.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Pintar uma área com um visual  
 O mais versátil e poderoso de todos os pincéis, o <xref:System.Windows.Media.VisualBrush> pinta uma área com um <xref:System.Windows.Media.Visual>. Um <xref:System.Windows.Media.Visual> é um tipo gráfico de baixo nível que serve como o ancestral de muitos componentes gráficos úteis. Por exemplo, as <xref:System.Windows.Window>classes <xref:System.Windows.FrameworkElement>, e <xref:System.Windows.Controls.Control> são todos os tipos de <xref:System.Windows.Media.Visual> objetos. Usando um <xref:System.Windows.Media.VisualBrush>, você pode pintar áreas com quase qualquer [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objeto gráfico.  
  
> [!NOTE]
> Embora <xref:System.Windows.Media.VisualBrush> seja um tipo de <xref:System.Windows.Freezable> objeto, ele não pode ser congelado (tornar-se somente leitura) <xref:System.Windows.Media.VisualBrush.Visual%2A> quando sua propriedade é definida com um valor `null`diferente de.  
  
 Há duas maneiras de especificar o <xref:System.Windows.Media.VisualBrush.Visual%2A> conteúdo de um. <xref:System.Windows.Media.VisualBrush>  
  
- Crie um novo <xref:System.Windows.Media.Visual> e use-o para definir <xref:System.Windows.Media.VisualBrush.Visual%2A> a propriedade do <xref:System.Windows.Media.VisualBrush>. Para obter um exemplo, consulte [o exemplo: Pinte um objeto com uma seção](#examplevisualbrush1) visual a seguir.  
  
- Use um existente <xref:System.Windows.Media.Visual>, que cria uma imagem duplicada do destino <xref:System.Windows.Media.Visual>. Você pode usar o <xref:System.Windows.Media.VisualBrush> para criar efeitos interessantes, como reflexão e ampliação. Para obter um exemplo, consulte [o exemplo: Crie uma seção](#examplevisualbrush2) de reflexão.  
  
 Quando você define um novo <xref:System.Windows.Media.VisualBrush.Visual%2A> para um <xref:System.Windows.Media.VisualBrush> e que <xref:System.Windows.Media.Visual> é um <xref:System.Windows.UIElement> (como um <xref:System.Windows.UIElement> painel ou controle), o sistema de layout é executado no e seus elementos filho quando a <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> propriedade é definida como `true`. No entanto, <xref:System.Windows.UIElement> a raiz é essencialmente isolada do restante do sistema: os estilos e o layout externo não podem percarner esse limite. Portanto, você deve especificar explicitamente o tamanho da raiz <xref:System.Windows.UIElement>, pois seu único pai é o <xref:System.Windows.Media.VisualBrush> e, portanto, não pode se dimensionar automaticamente para a área que está sendo pintada. Para mais informações sobre o layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consulte [Layout](../advanced/layout.md).  
  
 Como <xref:System.Windows.Media.ImageBrush> e <xref:System.Windows.Media.DrawingBrush>, um<xref:System.Windows.Media.VisualBrush> amplia seu conteúdo para preencher sua área de saída. Você pode substituir esse comportamento alterando a <xref:System.Windows.Media.TileBrush.Stretch%2A> propriedade de sua configuração padrão de <xref:System.Windows.Media.Stretch.Fill>. Para obter mais informações, consulte a propriedade <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Exemplo: Pintar um objeto com um Visual  
 No exemplo a seguir, vários controles e um painel são usados para pintar um retângulo.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Exemplo: Criar uma reflexão  
 O exemplo anterior mostrou como criar um novo <xref:System.Windows.Media.Visual> para uso como um plano de fundo. Você também pode usar um <xref:System.Windows.Media.VisualBrush> para exibir um Visual existente; essa funcionalidade permite que você produza efeitos visuais interessantes, como reflexos e ampliação. O exemplo a seguir usa <xref:System.Windows.Media.VisualBrush> um para criar uma reflexão de <xref:System.Windows.Controls.Border> um que contém vários elementos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um objeto visual refletido](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Um objeto visual refletido  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Para outros exemplos que mostram como ampliar partes da tela e como criar reflexões, consulte o [Exemplo do VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Recursos do TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.TileBrush> e <xref:System.Windows.Media.VisualBrush> são tipos de objetos. <xref:System.Windows.Media.TileBrush>os objetos fornecem uma grande quantidade de controle sobre como uma área é pintada com uma imagem, um desenho ou um Visual. Por exemplo, em vez de apenas pintar uma área com uma única imagem alongada, você pode pintá-la com uma série de blocos de imagens que criam um padrão.  
  
 Um <xref:System.Windows.Media.TileBrush> tem três componentes principais: conteúdo, blocos e a área de saída.  
  
 ![Componentes de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Componentes de um TileBrush com um único bloco  
  
 ![Componentes de um TileBrush xadrez](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Componentes de um TileBrush com vários blocos  
  
 Para obter mais informações sobre os recursos de <xref:System.Windows.Media.TileBrush> divisão de objetos, consulte [visão geral do TileBrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Visão geral de TileBrush](tilebrush-overview.md)
- [Visão geral de pincéis do WPF](wpf-brushes-overview.md)
- [Visão geral da geração de imagens](imaging-overview.md)
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de máscaras da opacidade](opacity-masks-overview.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Exemplo de ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Exemplo de VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
