---
title: Tratamento padrão de teclado e mouse no controle DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 36defff02450b40265c9b6801380cab78eabe5f3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746124"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Tratamento padrão de teclado e mouse no controle DataGridView Windows Forms

As tabelas a seguir descrevem como os usuários podem interagir com o controle de <xref:System.Windows.Forms.DataGridView> por meio de um teclado e um mouse.  
  
> [!NOTE]
> Para personalizar o comportamento do teclado, você pode manipular eventos de teclado padrão, como <xref:System.Windows.Forms.Control.KeyDown>. No modo de edição, no entanto, o controle de edição hospedado recebe a entrada do teclado e os eventos de teclado não ocorrem para o controle de <xref:System.Windows.Forms.DataGridView>. Para lidar com eventos de controle de edição, anexe seus manipuladores ao controle de edição em um manipulador de eventos <xref:System.Windows.Forms.DataGridView.EditingControlShowing>. Como alternativa, você pode personalizar o comportamento do teclado em uma subclasse <xref:System.Windows.Forms.DataGridView> substituindo os métodos <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> e <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>.  
  
## <a name="default-keyboard-handling"></a>Manipulação de teclado padrão  
  
### <a name="basic-navigation-and-entry-keys"></a>Teclas básicas de navegação e de entrada  
  
|Tecla ou combinação de teclas|Descrição|  
|----------------------------|-----------------|  
|SETA PARA BAIXO|Move o foco para a célula diretamente abaixo da célula atual. Se o foco estiver na última linha, não fará nada.|  
|SETA PARA A ESQUERDA|Move o foco para a célula anterior na linha. Se o foco estiver na primeira célula na linha, não fará nada.|  
|SETA PARA A DIREITA|Move o foco para a próxima célula na linha. Se o foco estiver na última célula na linha, não fará nada.|  
|SETA PARA CIMA|Move o foco para a célula diretamente acima da célula atual. Se o foco estiver na primeira linha, não fará nada.|  
|INÍCIO|Move o foco para a primeira célula na linha atual.|  
|END|Move o foco até a última célula na linha atual.|  
|{1&gt;PAGE DOWN&lt;1}|Rola o controle para baixo pelo número de linhas que são totalmente exibidas. Move o foco para a última linha totalmente exibida sem alterar as colunas.|  
|{1&gt;PAGE UP&lt;1}|Rola o controle para cima pelo número de linhas que são totalmente exibidas. Move o foco para a primeira linha exibida sem alterar as colunas.|  
|TAB|Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `false`, o moverá o foco para a próxima célula na linha atual. Se o foco já estiver na última célula da linha, o foco moverá para a primeira célula da linha seguinte. Se o foco estiver na última célula no controle, moverá o foco para o próximo controle na ordem de tabulação do contêiner pai.<br /><br /> Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `true`, o moverá o foco para o próximo controle na ordem de tabulação do contêiner pai.|  
|SHIFT+TAB|Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `false`, o moverá o foco para a célula anterior na linha atual. Se o foco já estiver na primeira célula da linha, moverá o foco para a última célula da linha anterior. Se o foco estiver na primeira célula no controle, moverá o foco para o controle anterior na ordem de tabulação do contêiner pai.<br /><br /> Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `true`, o moverá o foco para o controle anterior na ordem de tabulação do contêiner pai.|  
|CTRL + TAB|Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `false`, o moverá o foco para o próximo controle na ordem de tabulação do contêiner pai.<br /><br /> Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `true`, o moverá o foco para a próxima célula na linha atual. Se o foco já estiver na última célula da linha, o foco moverá para a primeira célula da linha seguinte. Se o foco estiver na última célula no controle, moverá o foco para o próximo controle na ordem de tabulação do contêiner pai.|  
|CTRL+SHIFT+TAB|Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `false`, o moverá o foco para o controle anterior na ordem de tabulação do contêiner pai.<br /><br /> Se o valor da propriedade <xref:System.Windows.Forms.DataGridView.StandardTab%2A> for `true`, o moverá o foco para a célula anterior na linha atual. Se o foco já estiver na primeira célula da linha, moverá o foco para a última célula da linha anterior. Se o foco estiver na primeira célula no controle, moverá o foco para o controle anterior na ordem de tabulação do contêiner pai.|  
|CTRL+SETA|Move o foco para a célula mais distante na direção da seta.|  
|CTRL+HOME|Move o foco para a primeira célula no controle.|  
|CTRL+END|Move o foco para a última célula no controle.|  
|CTRL+PAGE DOWN/UP|Mesmo que PAGE DOWN ou PAGE UP.|  
|{1&gt;F2&lt;1}|Coloca a célula atual no modo de edição de célula se o valor da propriedade <xref:System.Windows.Forms.DataGridView.EditMode%2A> for <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> ou <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|{1&gt;F3&lt;1}|Classifica a coluna atual se o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> for <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. É o mesmo que clicar no cabeçalho da coluna atual. Disponível desde .NET Framework 4.7.2. Para habilitar esse recurso, os aplicativos devem ter como destino .NET Framework 4.7.2 ou versões posteriores ou aceitar explicitamente as melhorias de acessibilidade usando as opções do AppContext.|  
|{1&gt;F4&lt;1}|Se a célula atual for uma <xref:System.Windows.Forms.DataGridViewComboBoxCell>, colocará a célula no modo de edição e exibirá a lista suspensa.|  
|ALT+SETA PARA CIMA/PARA BAIXO|Se a célula atual for uma <xref:System.Windows.Forms.DataGridViewComboBoxCell>, colocará a célula no modo de edição e exibirá a lista suspensa.|  
|ESPAÇO|Se a célula atual for uma <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>ou <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, o gerará os eventos <xref:System.Windows.Forms.DataGridView.CellClick> e <xref:System.Windows.Forms.DataGridView.CellContentClick>. Se a célula atual for uma <xref:System.Windows.Forms.DataGridViewButtonCell>, também pressionará o botão. Se a célula atual for uma <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, o também alterará o estado de verificação.|  
|ENTER|Confirma as alterações feitas na célula e na linha atuais e move o foco para a célula diretamente abaixo da célula atual. Se o foco estiver na última linha, confirmará as alterações sem mover o foco.|  
|{1&gt;ESC&lt;1}|Se o controle estiver no modo de edição, cancelará a edição. Se o controle não estiver no modo de edição, reverte as alterações que foram feitas na linha atual se o controle estiver associado a uma fonte de dados que dá suporte à edição ou se o modo virtual tiver sido implementado com escopo de confirmação de nível de linha.|  
|BACKSPACE|Exclui o caractere antes do ponto de inserção ao editar uma célula.|  
|DELETE|Exclui o caractere após o ponto de inserção ao editar uma célula.|  
|CTRL+ENTER|Confirma as alterações na célula atual sem mover o foco. Também confirma as alterações na linha atual se o controle estiver associado a uma fonte de dados que dá suporte à edição ou se o modo virtual tiver sido implementado com escopo de confirmação de nível de linha.|  
|CTRL+0|Insere um valor <xref:System.DBNull.Value?displayProperty=nameWithType> na célula atual se a célula puder ser editada. Por padrão, o valor de exibição de um valor de <xref:System.DBNull> célula é o valor da propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> do <xref:System.Windows.Forms.DataGridViewCellStyle> em vigor para a célula atual.|  
  
### <a name="selection-keys"></a>Chaves de seleção

 Se a propriedade <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definida como `false` e a propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> for definida como <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, a alteração da célula atual usando as teclas de navegação alterará a seleção para a nova célula. As teclas SHIFT, CTRL e ALT não afetam esse comportamento.  
  
 Se a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> for definida como <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, o mesmo comportamento ocorrerá, mas com as adições a seguir.  
  
|Tecla ou combinação de teclas|Descrição|  
|----------------------------|-----------------|  
|SHIFT+BARRA DE ESPAÇOS|Seleciona a linha ou a coluna inteira (o mesmo que clicar no cabeçalho da linha ou da coluna).|  
|tecla de navegação (tecla de direção, PAGE UP/DOWN, HOME, END)|Se uma linha ou coluna inteira estiver selecionada, a alteração da célula atual para uma nova linha ou coluna moverá a seleção para a nova linha ou coluna inteira (dependendo do modo de seleção).|  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `false` e <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> estiver definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, a alteração da célula atual para uma nova linha ou coluna usando o teclado moverá a seleção para a nova linha ou coluna completa. As teclas SHIFT, CTRL e ALT não afetam esse comportamento.  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `true`, o comportamento de navegação não será alterado, mas navegar com o teclado enquanto pressiona SHIFT (incluindo CTRL + SHIFT) modificará uma seleção de várias células. Antes de iniciar a navegação, o controle marca a célula atual como uma célula de âncora. Quando você navega mantendo a tecla SHIFT pressionada, a seleção inclui todas as células entre a célula de âncora e a célula atual. As outras células no controle permanecerão selecionadas se já tiverem sido selecionadas, mas poderão ficar não selecionadas se a navegação do teclado colocá-las temporariamente entre a célula âncora e a célula atual.  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `true` e <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> estiver definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, o comportamento da célula de âncora e da célula atual será o mesmo, mas somente as linhas ou colunas completas serão selecionadas ou desmarcadas.  
  
## <a name="default-mouse-handling"></a>Manipulação padrão de mouse
  
### <a name="basic-mouse-handling"></a>Manipulação básica de mouse
  
> [!NOTE]
> Clicar em uma célula com o botão esquerdo do mouse sempre altera a célula atual. Clicar em uma célula com o botão direito do mouse abre um menu de atalho, quando disponível.  
  
|Ação do mouse|Descrição|  
|------------------|-----------------|  
|Botão esquerdo do mouse para baixo|Torna a célula clicada na célula atual e gera o evento <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>.|  
|Botão esquerdo do mouse para cima|Gera o <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> evento|  
|Clique com o botão esquerdo do mouse|Gera os eventos <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>|  
|Botão esquerdo do mouse para baixo e arrastar em uma célula de cabeçalho de coluna|Se a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> for `true`, o moverá a coluna para que ela possa ser removida para uma nova posição.|  
  
### <a name="mouse-selection"></a>Seleção do mouse

 Nenhum comportamento de seleção está associado com o botão do meio ou botão de rolagem do mouse.  
  
 Se a propriedade <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definida como `false` e a propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> for definida como <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, ocorrerá o seguinte comportamento.  
  
|Ação do mouse|Descrição|  
|------------------|-----------------|  
|Clicar com o botão esquerdo do mouse|Selecionará apenas a célula atual se o usuário clicar em uma célula. Nenhum comportamento de seleção se o usuário clicar em um cabeçalho de linha ou de coluna.|  
|Clicar com o botão direito do mouse|Exibe um menu de atalho, se estiver disponível.|  
  
 O mesmo comportamento ocorre quando o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> é definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, exceto que, dependendo do modo de seleção, clicar em um cabeçalho de linha ou coluna selecionará a linha ou coluna inteira e definirá a célula atual como a primeira célula na linha ou coluna.  
  
 Se <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> for definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, clicar em qualquer célula em uma linha ou coluna selecionará a linha ou coluna inteira.  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `true`, clicar em uma célula enquanto pressiona CTRL ou SHIFT modificará uma seleção de várias células.  
  
 Quando você clica em uma célula mantendo a tecla CTRL pressionada, a célula muda seu estado de seleção enquanto que todas as outras células mantêm o estado de seleção atual.  
  
 Quando você clica em uma célula ou uma série de células mantendo a tecla SHIFT pressionada, a seleção inclui todas as células entre a célula atual e uma célula âncora localizada na posição da célula atual antes do primeiro clique. Quando você clica e arrasta o ponteiro por várias células, a célula âncora é a célula clicada no início da operação de arrastar. Os cliques subsequentes, mantendo a tecla SHIFT pressionada, alteram a célula atual, mas não a célula âncora. As outras células no controle permanecerão selecionadas se já tiverem sido selecionadas, mas poderão ficar não selecionadas se a navegação do mouse colocá-las temporariamente entre a célula âncora e a célula atual.  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `true` e <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> estiver definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, clicar em um cabeçalho de linha ou coluna (dependendo do modo de seleção) enquanto pressiona SHIFT modificará uma seleção existente de linhas ou colunas completas se essa seleção existir. Caso contrário, isso limpará a seleção e iniciará uma nova seleção de colunas ou linhas inteiras. No entanto, clicar em um cabeçalho de linha ou de coluna mantendo a tecla CTRL pressionada, adicionará ou removerá a linha ou a coluna clicada da seleção atual, sem modificar a seleção atual.  
  
 Se <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definido como `true` e <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> estiver definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, clicar em uma célula enquanto pressiona SHIFT ou CTRL se comparará da mesma forma, exceto que somente as linhas e colunas completas serão afetadas.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- [Controle DataGridView](datagridview-control-windows-forms.md)
