---
title: Tipo de Dados Long
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343969"
---
# <a name="long-data-type-visual-basic"></a>Tipo de dados Long (Visual Basic)

Contém inteiros assinados de 64 bits (8 bytes) que variam em valor de-9.223.372.036.854.775.808 até 9.223.372.036.854.775.807 (9.2... E + 18).

## <a name="remarks"></a>Comentários

Use o tipo de dados `Long` para conter números inteiros muito grandes para caber no tipo de dados `Integer`.

O valor padrão de `Long` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma variável `Long` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Long` (ou seja, se for menor que <xref:System.Int64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `Long`.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Os literais numéricos também podem incluir o [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) `L` para denotar o tipo de dados `Long`, como mostra o exemplo a seguir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Dicas de programação

- **Considerações sobre interoperabilidade.** Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, lembre-se de que `Long` tem uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para esse componente, declare-o como `Integer` em vez de `Long` no seu novo código de Visual Basic.

- **Ampliação.** O tipo de dados `Long` amplia a `Decimal`, `Single`ou `Double`. Isso significa que você pode converter `Long` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.

- **Digite os caracteres.** Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`. Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int64?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- <xref:System.Int64>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
