---
title: Mapas do Protobuf para dicionários-gRPC para desenvolvedores do WCF
description: Entenda como usar o Protobuf Maps para representar. Tipos de dicionário de rede.
ms.date: 09/09/2019
ms.openlocfilehash: 8b4f29daa263f329dc533d3ddc596d0f47c1b6e0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967423"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mapas de Protobuf para dicionários

É importante poder representar coleções arbitrárias de valores nomeados em mensagens. No .NET, isso é normalmente Tratado usando tipos de dicionário. O equivalente do Protobuf do tipo .NET <xref:System.Collections.Generic.IDictionary%602> é o tipo de `map<key_type, value_type>`. Esta seção mostra como declarar uma `map` no Protobuf e como usar o código gerado.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

No código gerado, `map` campos usam a classe `Google.Protobuf.Collections.MapField<TKey, TValue>`, que implementa as interfaces de coleção do .NET padrão, incluindo <xref:System.Collections.Generic.IDictionary%602>.

Os campos de mapa não podem ser repetidos diretamente em uma definição de mensagem, mas você pode criar uma mensagem aninhada contendo um mapa e usar `repeated` no tipo de mensagem, como no exemplo a seguir:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Usando Propriedades MapField no código

As propriedades `MapField` geradas de `map` campos são somente leitura e nunca serão `null`das. Para definir uma propriedade de mapa, use o método `Add(IDictionary<TKey,TValue> values)` na propriedade `MapField` vazia para copiar valores de qualquer dicionário .NET.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Leitura adicional

Para obter mais informações sobre o Protobuf, consulte a documentação oficial do [Protobuf](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Anterior](protobuf-enums.md)
>[Próximo](wcf-services-to-grpc-comparison.md)
