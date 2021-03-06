---
title: Adicionar recursos do navegador da Web ao aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: 5feecd975700745541103e81fd09bfc5e788c729
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747218"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Como adicionar recursos do navegador da Web a um Aplicativo do Windows Forms
Com o controle <xref:System.Windows.Forms.WebBrowser>, você pode adicionar a funcionalidade do navegador da Web ao seu aplicativo. O controle funciona como um navegador da Web por padrão. Depois de carregar uma URL inicial definindo a propriedade <xref:System.Windows.Forms.WebBrowser.Url%2A>, você pode navegar clicando em hiperlinks ou usando atalhos de teclado para voltar e avançar pelo histórico de navegação. Por padrão, você pode acessar a funcionalidade adicional do navegador por meio do menu de atalho acessado quando se clica com o botão direito do mouse. Você também pode abrir novos documentos soltando-os no controle. O controle de <xref:System.Windows.Forms.WebBrowser> também tem várias propriedades, métodos e eventos que você pode usar para implementar recursos de interface de usuário semelhantes àqueles encontrados no Internet Explorer.  
  
 O exemplo de código a seguir implementa uma barra de endereços, botões de navegador típicos, um menu **Arquivo**, uma barra de status e uma barra de título que exibe o título da página atual.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies `System`, `System.Drawing`e `System.Windows.Forms`.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.WebBrowser>
- [Controle WebBrowser](webbrowser-control-windows-forms.md)
