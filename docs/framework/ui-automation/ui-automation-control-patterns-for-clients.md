---
title: Padrões de Controle para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 193049aed6da3375b687e465678dca4dc90e6b39
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448816"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral apresenta padrões de controle para clientes de automação da interface do usuário. Ele inclui informações sobre como um cliente de automação de interface do usuário pode usar padrões de controle para acessar informações sobre o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Os padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independentemente do tipo de controle ou da aparência do controle. Os clientes de automação da interface do usuário podem examinar um <xref:System.Windows.Automation.AutomationElement> para determinar quais padrões de controle têm suporte e estar garantidos do comportamento do controle.  
  
 Para obter uma lista completa de padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtendo padrões de controle  
 Os clientes recuperam um padrão de controle de um <xref:System.Windows.Automation.AutomationElement> chamando <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Os clientes podem usar o método <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> ou uma propriedade individual `IsPatternAvailable` (por exemplo, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) para determinar se há suporte para um padrão ou grupo de padrões no <xref:System.Windows.Automation.AutomationElement>. No entanto, é mais eficiente tentar obter o padrão de controle e testar uma referência de `null` do que verificar as propriedades com suporte e recuperar o padrão de controle, pois isso resulta em menos chamadas de processo cruzado.  
  
 O exemplo a seguir demonstra como obter um padrão de controle de <xref:System.Windows.Automation.TextPattern> de um <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Recuperando propriedades em padrões de controle  
 Os clientes podem recuperar os valores de propriedade nos padrões de controle chamando <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> e converter o objeto retornado para um tipo apropriado. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
 Além dos métodos de `GetPropertyValue`, os valores de propriedade podem ser recuperados por meio de acessadores de Common Language Runtime (CLR) para acessar as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um padrão.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Controles com padrões de variáveis  
 Alguns tipos de controle dão suporte a padrões diferentes, dependendo do Estado ou da maneira como o controle está sendo usado. Exemplos de controles que podem ter padrões de variáveis são exibições de lista (miniaturas, blocos, ícones, lista, detalhes), gráficos do Microsoft Excel (pizza, linha, barra, valor de célula com uma fórmula), área de documento do Microsoft Word (normal, layout da Web, estrutura de tópicos, layout de impressão, impressão Visualização) e capas do Microsoft Windows Media Player.  
  
 Controles que implementam tipos de controle personalizados podem ter qualquer conjunto de padrões de controle que são necessários para representar sua funcionalidade.  
  
## <a name="see-also"></a>Consulte também

- [UI Automation Control Patterns](ui-automation-control-patterns.md) (Padrões de controle da Automação da Interface do Usuário)
- [UI Automation Text Pattern](ui-automation-text-pattern.md) (Padrão de texto da Automação da Interface do Usuário)
- [Invocando um controle utilizando automação de interface do usuário](invoke-a-control-using-ui-automation.md)
- [Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapeamento de padrão de controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md)
- [Amostra de texto de inserção de TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Exemplo de pesquisa e seleção de TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
