---
title: MDA notMarshalable
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddb6b0b5c2248d215245e0f881c8e7c91b13e480
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052423"
---
# <a name="notmarshalable-mda"></a>MDA notMarshalable
O MDA (Assistente de Depuração Gerenciado) de `notMarshalable` é ativado quando o CLR (Common Language Runtime) encontra um ponteiro de interface COM sem um proxy/stub registrado válido ou uma implementação incorreta da interface `IMarshal` ao tentar realizar marshaling da interface entre contextos.  
  
## <a name="symptoms"></a>Sintomas  
 Chamadas não são atendidas ou chamadas ocorrem no contexto errado para ponteiros de interface COM.  
  
## <a name="cause"></a>Causa  
 Nenhum proxy/stub registrado válido ou uma `IMarshal` incorreta ao tentar realizar marshaling da interface entre contextos.  
  
## <a name="resolution"></a>Resolução  
 Verifique se você tem um stub de proxy registrado e que a implementação `IMarshal` é válida.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem nenhum efeito sobre o tempo de execução.  
  
## <a name="output"></a>Saída  
 Uma mensagem que descreve o problema.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
