---
title: '#elif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712566"
---
# <a name="elif-c-reference"></a>#elif (Referência de C#)
O `#elif` permite criar uma diretiva condicional composta. A expressão `#elif` será avaliada se nenhum dos [#if](./preprocessor-if.md) anteriores nem nenhuma diretiva `#elif`, opcional, anterior avaliar expressões para `true`. Se uma expressão `#elif` for avaliada como `true`, o compilador avalia todo o código entre o `#elif` e a próxima diretiva condicional. Por exemplo:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 É possível usar os operadores `==` (igualdade), `!=` (desigualdade), `&&` (e) e `||` (ou), para avaliar vários símbolos. Também é possível agrupar os símbolos e operadores com parênteses.  
  
## <a name="remarks"></a>Comentários  
 `#elif` é equivalente a usar:  
  
```csharp
#else  
#if  
```  
  
 Usar `#elif` é mais simples, porque cada `#if` requer um [#endif](./preprocessor-endif.md), enquanto um `#elif` pode ser usado sem um `#endif` de correspondência.  
  
 Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#elif`.  
  
## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Diretivas do pré-processador do C#](./index.md)
