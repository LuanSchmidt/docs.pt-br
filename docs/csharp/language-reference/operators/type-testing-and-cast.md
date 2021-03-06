---
title: Operadores cast e teste de tipo – Referência de C#
description: Saiba mais sobre os operadores do C# que você pode usar para verificar o tipo de um resultado de expressão e convertê-lo para outro tipo, se necessário.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: c3550a593eafb9b50fa7e419e2f747c3e7a0e2ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972641"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operadores cast e teste de tipo (Referência de C#)

Você pode usar os seguintes operadores para executar a verificação de tipo ou conversão de tipo:

- [operador is](#is-operator): para verificar se o tipo de runtime de uma expressão é compatível com um determinado tipo
- [operador as](#as-operator): para converter explicitamente uma expressão em um determinado tipo, se o tipo de runtime for compatível com esse tipo
- [operador cast ()](#cast-operator-): para executar uma conversão explícita
- [operador typeof](#typeof-operator): para obter a instância <xref:System.Type?displayProperty=nameWithType> para um tipo

## <a name="is-operator"></a>Operador is

O operador `is` verifica se o tipo de runtime de um resultado de expressão é compatível com um determinado tipo. A partir C# do 7,0, o operador de`is`também testa um resultado de expressão em relação a um padrão.

A expressão com o operador `is` de teste de tipo tem o seguinte formato

```csharp
E is T
```

em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo. `E` não pode ser um método anônimo ou uma expressão lambda.

A expressão `E is T` retorna `true` se o resultado de `E` não for nulo e puder ser convertido para o tipo `T` por uma conversão de referência, uma conversão boxing ou uma conversão unboxing; caso contrário, retorna `false`. O operador `is` não considera conversões definidas pelo usuário.

O exemplo a seguir demonstra que o operador `is` retorna `true` se o tipo de runtime de um resultado da expressão é derivado de um determinado tipo, ou seja, existe uma conversão de referência entre tipos:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

O exemplo a seguir mostra que o operador de `is` leva em consideração as conversões boxing e unboxing, mas não considera as [conversões numéricas](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Para saber mais sobre conversões em C#, confira o capítulo [Conversões](~/_csharplang/spec/conversions.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Teste de tipo com correspondência de padrões

A partir C# do 7,0, o operador de`is`também testa um resultado de expressão em relação a um padrão. Em particular, ele dá suporte ao padrão de tipo da seguinte forma:

```csharp
E is T v
```

em que `E` é uma expressão que retorna um valor, `T` é o nome de um tipo ou um parâmetro de tipo, e `v` é uma nova variável local do tipo `T`. Se o resultado de `E` não for nulo e puder ser convertido para `T` por uma conversão de referência, boxing ou unboxing, a expressão `E is T v` retornará `true` e o valor convertido do resultado de `E`será atribuído à variável `v`.

O exemplo a seguir demonstra o uso do operador `is` com um padrão de tipo:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Para saber mais sobre o padrão de tipos e outros padrões com suporte, confira [Correspondência de padrões com is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>operador as

O operador `as` converte explicitamente o resultado de uma expressão para uma determinada referência ou tipo de valor anulável. Se a conversão não for possível, o operador `as` retorna `null`. Ao contrário do [operador cast ()](#cast-operator-), o operador `as` nunca lança uma exceção.

A expressão da forma

```csharp
E as T
```

em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo, produz o mesmo resultado que

```csharp
E is T ? (T)(E) : (T)null
```

exceto que `E` é avaliado apenas uma vez.

O operador `as` considera apenas as conversões de referência, anulável, boxing e unboxing. Não é possível usar o operador `as` para executar uma conversão definida pelo usuário. Para fazer isso, use o operador [cast ()](#cast-operator-).

O exemplo a seguir demonstra o uso do operador `as`:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Como mostrado no exemplo anterior, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida. A partir C# do 7,0, você pode usar o [operador is](#type-testing-with-pattern-matching) para testar se a conversão é bem sucedido e, se tiver sucesso, atribuir seu resultado a uma nova variável.

## <a name="cast-operator-"></a>Operador cast ()

Uma expressão de conversão do formulário `(T)E` realiza uma conversão explícita do resultado da expressão `E` para o tipo `T`. Se não existir nenhuma conversão explícita do tipo `E` para o tipo `T`, ocorrerá um erro em tempo de compilação. No tempo de execução, uma conversão explícita pode não ter êxito e uma expressão de conversão pode lançar uma exceção.

O exemplo a seguir demonstra conversões numéricas e de referência explícitas:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Para saber mais sobre conversões explícitas sem suporte, confira a seção [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md). Para saber mais sobre como definir uma conversão de tipo explícito ou implícito personalizado, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Outros usos de ()

Você também usa parênteses para [ chamar um método ou chamar um delegado ](member-access-operators.md#invocation-operator-).

Outro uso dos parênteses é ajustar a ordem na qual as operações em uma expressão são avaliadas. Para saber mais, confira [Operadores C#](index.md).

## <a name="typeof-operator"></a>Operador typeof

O operador `typeof` obtém a instância <xref:System.Type?displayProperty=nameWithType> para um tipo. O argumento do operador `typeof` deve ser o nome de um tipo ou um parâmetro de tipo, como mostra o exemplo a seguir:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Você também pode usar o operador `typeof` com tipos genéricos não associados. O nome de um tipo genérico não associado deve conter o número apropriado de vírgulas, que é um a menos que o número de parâmetros de tipo. O exemplo a seguir mostra o uso do operador `typeof` com um tipo genérico não associado:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Uma expressão não pode ser um argumento do operador `typeof`. Para obter a instância de <xref:System.Type?displayProperty=nameWithType> para o tipo de tempo de execução de um resultado de expressão, use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType>.

### <a name="type-testing-with-the-typeof-operator"></a>Teste de tipo com o operador `typeof`

Use o operador `typeof` para verificar se o tipo de runtime do resultado da expressão corresponde exatamente a um determinado tipo. O exemplo a seguir demonstra a diferença entre a verificação de tipo executada com o operador `typeof` e o [operador is](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os operadores `is`, `as`e `typeof` não podem ser sobrecarregados.

Um tipo definido pelo usuário não pode sobrecarregar o operador `()`, mas pode definir conversões de tipo customizado que podem ser executadas por uma expressão de conversão. Para saber mais, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operador is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operador as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Expressões cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operador typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Como converter com segurança usando correspondência de padrões e os operadores is e as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Genéricos no .NET](../../../standard/generics/index.md)
