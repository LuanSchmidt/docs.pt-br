---
title: CHAVE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319707"
---
# <a name="key-entity-sql"></a>CHAVE (Entity SQL)
Extraia a chave de uma referência ou uma expressão de entidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Comentários  
 Uma chave de entidade contém os valores chave na ordem correta de entidade ou de referência de entidade especificada. Porque os vários conjuntos de entidades podem ser baseados no mesmo tipo, a mesma chave pode aparecer em cada conjunto de entidades. Para obter uma referência única, use `REF`. O tipo de retorno de operador- de CHAVE é um tipo da linha que inclui um campo para cada tecla de entidade, na mesma ordem.  
  
 No exemplo a seguir, o operador- de chave é passado uma referência para a entidade de BadOrder, e retorna a parte principal da referência. Nesse caso, um tipo de registro com o exatamente um campo que corresponde à propriedade de `Id` .  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador- de CHAVE para extrair a parte principal de uma expressão com referência de tipo. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
