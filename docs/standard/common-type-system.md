---
title: Common Type System e Common Language Specification
description: Saiba como o CTS (Common Type System) e a CLS (Common Language Specification) possibilitam ao .NET dar suporte a várias linguagens.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: d162a736b8f7b56293fc75a445c2a80cce597768
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664526"
---
# <a name="common-type-system--common-language-specification"></a>Common Type System e Common Language Specification

Novamente, dois termos que são usados livremente no mundo do .NET, eles realmente são essenciais para compreender como uma implementação do .NET possibilita o desenvolvimento para várias linguagens e para entender como ela funciona.

## <a name="common-type-system"></a>Common Type System

Para começar do zero, lembre-se que uma implementação do .NET é _independente de linguagem_. Isso não significa apenas que um programador pode escrever seu código em qualquer idioma que pode ser compilada para IL. Isso também significa que ela precisa ser capaz de interagir com o código escrito em outras linguagens que podem ser usadas em uma implementação do .NET.

Para fazer isso de forma transparente, deve haver uma maneira comum de descrever todos os tipos com suporte. Isso é o que o CTS (Common Type System) é responsável por fazer. Ele foi feito de várias maneiras:

* Estabelecer uma estrutura para a execução em qualquer idioma.
* Fornecer um modelo orientado a objetos para dar suporte à implementação de várias linguagens em uma implementação do .NET.
* Definir um conjunto de regras que todas as linguagens devem seguir quando se trata de trabalhar com tipos.
* Fornecer uma biblioteca que contém os tipos primitivos básicos que são usados no desenvolvimento de aplicativos (por exemplo, `Boolean`, `Byte`, `Char` etc.)

O CTS define dois tipos principais que devem ter suporte: tipos de referência e valor. Seus nomes apontam para suas definições.

Os objetos de tipos de referência são representados por uma referência ao valor real do objeto. Uma referência aqui é similar a um ponteiro no C/C++. Ele simplesmente se refere a um local da memória no qual estão os valores dos objetos. Isso tem um profundo impacto sobre como esses tipos são usados. Se você atribuir um tipo de referência a uma variável e, em seguida, passar essa variável em um método, por exemplo, qualquer alteração feita no objeto será refletida no objeto principal. Não há nenhuma cópia.

Tipos de valor são o oposto, no qual os objetos são representados por seus valores. Se você atribuir um tipo de valor a uma variável, você estará, essencialmente, copiando um valor do objeto.

O CTS define várias categorias de tipos, cada um com sua semântica específica e o uso:

* Classes
* Estruturas
* Enums
* Interfaces
* Delegados

O CTS também define todas as outras propriedades de tipos, como modificadores de acesso, o que são membros de tipo válidos, como a herança e a sobrecarga funcionam e assim por diante. Infelizmente, se aprofundar em qualquer um deles está além do escopo de um artigo introdutório como este, mas você pode consultar a seção [Mais recursos](#more-resources) no final para obter links para mais conteúdos detalhados que abordam esses tópicos.

## <a name="common-language-specification"></a>Common Language Specification

Para habilitar cenários de interoperabilidade completa, todos os objetos que são criados em código devem se basear em alguns pontos em comum nos idiomas que estão consumindo eles (são seus _chamadores_). Como há várias linguagens diferentes, o .NET especificou essas semelhanças em algo chamado de CLS **(Common Language Specification)**. A CLS define um conjunto de recursos que são necessários para muitos aplicativos comuns. Ela também fornece uma espécie de receita para qualquer linguagem que é implementada no .NET, no que ela precisar dar suporte.

A CLS é um subconjunto do CTS. Isso significa que todas as regras no CTS também se aplicam à CLS, a menos que as regras da CLS sejam mais estritas. Se um componente é criado usando apenas as regras na CLS, ou seja, ele expõe apenas os recursos da CLS em sua API, ele é chamado de **compatível com CLS**. Por exemplo, as `<framework-librares>` estão em conformidade com CLS precisamente porque precisam funcionar em todas as linguagens com suporte no .NET.

Você pode consultar os documentos na seção [Mais recursos](#more-resources) abaixo para obter uma visão geral de todos os recursos na CLS.

## <a name="more-resources"></a>Mais recursos

* [Common Type System](./base-types/common-type-system.md)
* [Common Language Specification](language-independence-and-language-independent-components.md)
