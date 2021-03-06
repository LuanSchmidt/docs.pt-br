---
title: Convenções de maiúsculas e minúsculas
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 8af4a15e1e5b34c38b14c6b547cf44801bbf13e6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741765"
---
# <a name="capitalization-conventions"></a>Convenções de maiúsculas e minúsculas
As diretrizes neste capítulo destacam um método simples para usar o caso, quando aplicado de forma consistente, tornar os identificadores para tipos, membros e parâmetros fáceis de ler.

## <a name="capitalization-rules-for-identifiers"></a>Regras de capitalização para identificadores
 Para diferenciar palavras em um identificador, coloque em maiúscula a primeira letra de cada palavra no identificador. Não use sublinhados para diferenciar palavras, ou para esse assunto, em qualquer lugar nos identificadores. Há duas maneiras apropriadas de colocar identificadores em maiúsculas, dependendo do uso do identificador:

- PascalCasing

- camelCasing

 A Convenção PascalCasing, usada para todos os identificadores, exceto nomes de parâmetro, coloca em maiúscula o primeiro caractere de cada palavra (incluindo acrônimos sobre duas letras de comprimento), conforme mostrado nos exemplos a seguir:

 `PropertyDescriptor`
 `HtmlTag`

 Um caso especial é feito para acrônimos de duas letras nas quais as letras são colocadas em maiúsculas, conforme mostrado no identificador a seguir:

 `IOStream`

 A Convenção camelCasing, usada apenas para nomes de parâmetro, coloca em maiúscula o primeiro caractere de cada palavra, exceto a primeira palavra, conforme mostrado nos exemplos a seguir. Como o exemplo também mostra, os acrônimos de duas letras que começam um identificador de camel-case são minúsculos.

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️ Use PascalCasing para todos os nomes de membro público, tipo e namespace que consistem em várias palavras.

 ✔️ Use camelCasing para nomes de parâmetro.

 A tabela a seguir descreve as regras de capitalização para diferentes tipos de identificadores.

|Identifier|Maiúsculas|Exemplo|
|----------------|------------|-------------|
|Namespace|Pascal|`namespace System.Security { ... }`|
|{1&gt;Tipo&lt;1}|Pascal|`public class StreamReader { ... }`|
|Interface|Pascal|`public interface IEnumerable { ... }`|
|Método|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|propriedade|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|Event|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|Campo|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|Valor de enumeração|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|Parâmetro|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>Capitalização de palavras compostas e termos comuns
 A maioria dos termos compostos é tratada como palavras únicas para fins de capitalização.

 ❌ não colocar todas as palavras em maiúsculas nas chamadas de palavras compostas de forma fechada.

 Essas são palavras compostas escritas como uma única palavra, como ponto de extremidade. Para as diretrizes de uso de maiúsculas e minúsculas, trate uma palavra composta de forma fechada como uma única palavra. Use um dicionário atual para determinar se uma palavra composta é escrita em formato fechado.

|Pascal|Camel|não|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a>Diferenciação de maiúsculas e minúsculas
 Os idiomas que podem ser executados no CLR não precisam dar suporte à diferenciação de maiúsculas e minúsculas, embora alguns façam. Mesmo que seu idioma dê suporte a isso, outras linguagens que podem acessar sua estrutura não têm. As APIs que são acessíveis externamente, portanto, não podem depender apenas de maiúsculas e minúsculas para distinguir entre dois nomes no mesmo contexto.

 ❌ não presuma que todas as linguagens de programação diferenciam maiúsculas de minúsculas. Eles não são. Os nomes não podem diferir apenas por maiúsculas e minúsculas.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
