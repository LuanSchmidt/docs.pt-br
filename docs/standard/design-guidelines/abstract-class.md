---
title: Design de classe abstrata
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709589"
---
# <a name="abstract-class-design"></a>Design de classe abstrata
**X DO NOT** definir construtores internos públicos ou privados em tipos abstratos.  
  
 Os construtores só devem ser públicos se os usuários precisarem criar instâncias do tipo. Como não é possível criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público é projetado incorretamente e induzindo aos usuários.  
  
 **✓ DO** definir um construtor interno ou uma protegidos em classes abstratas.  
  
 Um construtor protegido é mais comum e simplesmente permite que a classe base faça sua própria inicialização quando os subtipos são criados.  
  
 Um construtor interno pode ser usado para limitar implementações concretas da classe abstrata ao assembly que define a classe.  
  
 **✓ DO** fornecer pelo menos um tipo concreto que herda de cada classe abstrata que você enviar.  
  
 Fazer isso ajuda a validar o design da classe abstrata. Por exemplo, <xref:System.IO.FileStream?displayProperty=nameWithType> é uma implementação da classe abstrata <xref:System.IO.Stream?displayProperty=nameWithType>.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
