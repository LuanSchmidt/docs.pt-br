---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: d8ea7010bef389b49f68c811565a641a580e230a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716951"
---
# <a name="fault-contract"></a>Contrato de falha
O exemplo de contrato de falha demonstra como comunicar informações de erro de um serviço para um cliente. O exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna em uma falha. O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 O contrato da calculadora foi modificado para incluir um <xref:System.ServiceModel.FaultContractAttribute>, conforme mostrado no código de exemplo a seguir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 O atributo <xref:System.ServiceModel.FaultContractAttribute> indica que a operação de `Divide` pode retornar uma falha do tipo `MathFault`. Uma falha pode ser de qualquer tipo que possa ser serializado. Nesse caso, o `MathFault` é um contrato de dados, da seguinte maneira:  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 O método `Divide` gera uma exceção de <xref:System.ServiceModel.FaultException%601> quando ocorre uma exceção de divisão por zero, conforme mostrado no código de exemplo a seguir. Essa exceção resulta em uma falha que está sendo enviada ao cliente.  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 O código do cliente força um erro solicitando uma divisão por zero. Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. Você vê a divisão por zero sendo relatada como uma falha. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 O cliente faz isso capturando a exceção de `FaultException<MathFault>` apropriada:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para evitar que os detalhes da implementação do serviço escapem o limite de segurança do serviço. `FaultContract` fornece uma maneira de descrever as falhas em um contrato e marcar determinados tipos de exceções conforme apropriado para a transmissão para o cliente. `FaultException<T>` fornece o mecanismo de tempo de execução para o envio de falhas aos consumidores.  
  
 No entanto, é útil ver os detalhes internos de uma falha de serviço durante a depuração. Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção sem tratamento no servidor devem ser incluídos na falha que é enviada ao cliente. Isso é feito com a definição de <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> para `true`. Você pode defini-lo no código ou na configuração, conforme mostrado no exemplo a seguir.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Além disso, o comportamento deve ser associado ao serviço definindo o atributo `behaviorConfiguration` do serviço no arquivo de configuração como "CalculatorServiceBehavior".  
  
 Para detectar essas falhas no cliente, o <xref:System.ServiceModel.FaultException> não genérico deve ser detectado.  
  
 Esse comportamento só deve ser usado para fins de depuração e nunca deve ser habilitado na produção.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
