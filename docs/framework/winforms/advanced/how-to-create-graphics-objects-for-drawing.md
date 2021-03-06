---
title: 'Como: criar objetos gráficos para desenho'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964337"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Como: criar objetos gráficos para desenho
Antes de poder desenhar linhas e formas, renderizar texto ou exibir e manipular imagens com o GDI+, você precisa criar um <xref:System.Drawing.Graphics> objeto. O <xref:System.Drawing.Graphics> objeto representa uma superfície de desenho de GDI+ e é o objeto usado para criar imagens gráficas.  
  
 Há duas etapas ao trabalhar com gráficos:  
  
1. Criando um <xref:System.Drawing.Graphics> objeto.  
  
2. Usando o <xref:System.Drawing.Graphics> objeto para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.  
  
## <a name="creating-a-graphics-object"></a>Criando um objeto gráfico  
 Um objeto gráfico pode ser criado de várias maneiras.  
  
#### <a name="to-create-a-graphics-object"></a>Para criar um objeto gráfico  
  
- Receber uma referência a um objeto de gráfico como parte do <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> no caso de um formulário ou controle. Geralmente é assim que você obtém uma referência a um objeto gráfico ao criar código de pintura para um controle. Da mesma forma, você também pode obter um objeto gráfico como uma propriedade <xref:System.Drawing.Printing.PrintPageEventArgs> do ao manipular <xref:System.Drawing.Printing.PrintDocument.PrintPage> o evento para <xref:System.Drawing.Printing.PrintDocument>um.  
  
     - ou -  
  
- Chame o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário. Use esse método se quiser desenhar em um formulário ou controle que já exista.  
  
     - ou -  
  
- Crie um <xref:System.Drawing.Graphics> objeto de qualquer objeto que herde <xref:System.Drawing.Image>de. Essa abordagem é útil quando você quer alterar uma imagem existente.  
  
     As seções a seguir dão detalhes sobre cada um desses processos.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs no manipulador de eventos de pintura  
 Ao programar <xref:System.Windows.Forms.PaintEventHandler> para controles <xref:System.Drawing.Printing.PrintDocument.PrintPage> ou para para <xref:System.Drawing.Printing.PrintDocument>, um objeto de gráfico é fornecido como uma das propriedades de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Para obter uma referência a um objeto Gráfico de PaintEventArgs no evento de pintura  
  
1. Declare o <xref:System.Drawing.Graphics> objeto.  
  
2. Atribua a variável para se referir <xref:System.Drawing.Graphics> ao objeto passado como parte <xref:System.Windows.Forms.PaintEventArgs>do.  
  
3. Inserir código para pintar o formulário ou o controle.  
  
     O exemplo a seguir mostra como fazer referência <xref:System.Drawing.Graphics> a um objeto <xref:System.Windows.Forms.PaintEventArgs> do no <xref:System.Windows.Forms.Control.Paint> evento:  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>Método CreateGraphics  
 Você também pode usar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Para criar um objeto gráfico com o método CreateGraphics  
  
- Chame o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método do formulário ou controle no qual você deseja renderizar gráficos.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>Criar de um objeto de imagem  
 Além disso, você pode criar um objeto gráfico a partir de qualquer objeto derivado da <xref:System.Drawing.Image> classe.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Para criar um objeto Gráfico de uma imagem  
  
- Chame o <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> método, fornecendo o nome da variável de imagem da qual você deseja criar um <xref:System.Drawing.Graphics> objeto.  
  
     O exemplo a seguir mostra como usar um <xref:System.Drawing.Bitmap> objeto:  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> Você só pode criar <xref:System.Drawing.Graphics> objetos de arquivos. bmp não indexados, como arquivos. bmp de 16 bits, 24 bits e 32 bits. Cada pixel dos arquivos .bmp não indexados mantém uma cor, em contraste com pixels de arquivos .bmp indexados, que mantêm um índice para uma tabela de cores.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Desenhar e manipular imagens e formas  
 Depois de criado, um <xref:System.Drawing.Graphics> objeto pode ser usado para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens. Os objetos principais usados com o <xref:System.Drawing.Graphics> objeto são:  
  
- A <xref:System.Drawing.Pen> classe — usada para desenhar linhas, estruturar formas ou renderizar outras representações geométricas.  
  
- A <xref:System.Drawing.Brush> classe — usada para preencher áreas de elementos gráficos, como formas preenchidas, imagens ou texto.  
  
- A <xref:System.Drawing.Font> classe — fornece uma descrição de quais formas usar ao renderizar texto.  
  
- A <xref:System.Drawing.Color> estrutura — representa as diferentes cores a serem exibidas.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Para usar o objeto Gráfico que você criou  
  
- Trabalhe com o objeto apropriado listado acima para desenhar o que você precisa.  
  
     Para mais informações, consulte os seguintes tópicos:  
  
    |Para renderizar|Consulte|  
    |---------------|---------|  
    |Linhas|[Como: Desenhar uma linha em um formulário do Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Formas|[Como: Desenhar uma forma contornada](how-to-draw-an-outlined-shape.md)|  
    |Texto|[Como: Desenhar texto em um formulário do Windows](how-to-draw-text-on-a-windows-form.md)|  
    |Imagens|[Como: Renderizar imagens com GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Consulte também

- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Linhas, Curvas e Formas](lines-curves-and-shapes.md)
- [Como: Renderizar imagens com GDI+](how-to-render-images-with-gdi.md)
