---
title: Execução adiada e avaliação lenta em LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594560"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Execução adiada e avaliação lenta em LINQ to XML (C#)
As operações de consulta e eixo são geralmente implementadas para usar a execução adiada. Este tópico explica os requisitos e as vantagens da execução adiada, além de algumas considerações sobre a implementação.  
  
## <a name="deferred-execution"></a>Execução Adiada  
 A execução adiada significa que a avaliação de uma expressão será atrasada até que seu valor *realizado* seja realmente necessário. A execução adiada pode aumentar muito o desempenho quando você precisa manipular grandes coleções de dados, especialmente em programas que contêm uma série de consultas ou manipulações encadeadas. Na melhor das hipóteses, a execução adiada permite apenas uma única iteração pela coleção de origem.  
  
 As tecnologias LINQ usam de modo intenso a execução adiada em ambos os membros das classes <xref:System.Linq?displayProperty=nameWithType> centrais e nos métodos de extensão nos diversos namespaces LINQ, como <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 A execução adiada tem suporte direto na linguagem C# pela palavra-chave [yield](../../../language-reference/keywords/yield.md) (na forma da instrução `yield-return`) quando usada dentro de um bloco de iterador. Tal iterador deve retornar uma coleção do tipo <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> (ou um tipo derivado).  
  
## <a name="eager-vs-lazy-evaluation"></a>Avaliação ansiosa vs. lenta  
 Quando você escreve um método que implementa a execução adiada, também precisa decidir se deve implementar o método usando a avaliação lenta ou a avaliação ansiosa.  
  
- Na *avaliação lenta*, um único elemento da coleção de origem é processado durante cada chamada ao iterador. Essa é a forma comum de implementação de iteradores.  
  
- Na *avaliação adiantada*, a primeira chamada ao iterador resultará no processamento da coleção inteira. Uma cópia temporária da coleção de origem também pode ser necessária. Por exemplo, o método <xref:System.Linq.Enumerable.OrderBy%2A> precisa classificar toda a coleção antes de retornar o primeiro elemento.  
  
 A avaliação lenta normalmente gera um melhor desempenho porque distribui a sobrecarga de processamento uniformemente por toda a avaliação da coleção e minimiza o uso de dados temporários. Naturalmente, para algumas operações, não há nenhuma outra opção que não seja materializar resultados intermediários.  
  
## <a name="next-steps"></a>Próximas etapas  
 O próximo tópico deste tutorial ilustra a execução adiada:  
  
- [Exemplo de execução adiada (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Consulte também

- [Tutorial: Encadeando consultas (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Conceitos e terminologia (transformação funcional) (C#)](./concepts-and-terminology-functional-transformation.md)
- [Operações de agregação (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
