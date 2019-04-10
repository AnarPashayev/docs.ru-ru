---
title: Контракт ошибок
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 21c4894b3927b6fdcf9aff16ea07020eeb073977
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317133"
---
# <a name="fault-contract"></a><span data-ttu-id="4fe10-102">Контракт ошибок</span><span class="sxs-lookup"><span data-stu-id="4fe10-102">Fault Contract</span></span>
<span data-ttu-id="4fe10-103">Этот образец демонстрирует передачу информации об ошибке из службы клиенту.</span><span class="sxs-lookup"><span data-stu-id="4fe10-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="4fe10-104">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md), с помощью некоторых дополнительный код, добавленный в службу для преобразования внутреннего исключения в ошибку.</span><span class="sxs-lookup"><span data-stu-id="4fe10-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="4fe10-105">Клиент пытается выполнить операцию деления на ноль для принудительного сбоя службы.</span><span class="sxs-lookup"><span data-stu-id="4fe10-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fe10-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="4fe10-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4fe10-107">В контракт калькулятора добавлен атрибут <xref:System.ServiceModel.FaultContractAttribute>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="4fe10-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4fe10-108">Атрибут <xref:System.ServiceModel.FaultContractAttribute> указывает, что операция `Divide` может возвратить сбой типа `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="4fe10-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="4fe10-109">Сбой может принадлежать к любому типу, который сериализовать.</span><span class="sxs-lookup"><span data-stu-id="4fe10-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="4fe10-110">В данном случае `MathFault` представляет собой следующий контракт данных:</span><span class="sxs-lookup"><span data-stu-id="4fe10-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="4fe10-111">Метод `Divide` вызывает исключение <xref:System.ServiceModel.FaultException%601> при делении на ноль, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="4fe10-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="4fe10-112">В результате исключения клиенту отправляется сбой.</span><span class="sxs-lookup"><span data-stu-id="4fe10-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="4fe10-113">Клиентский код принудительно создает ошибку, запрашивая деление не ноль.</span><span class="sxs-lookup"><span data-stu-id="4fe10-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="4fe10-114">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="4fe10-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4fe10-115">Деление на ноль будет выведено на консоль в виде сбоя.</span><span class="sxs-lookup"><span data-stu-id="4fe10-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="4fe10-116">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="4fe10-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4fe10-117">Клиент выводит сбой, перехватывая соответствующее исключение `FaultException<MathFault>`:</span><span class="sxs-lookup"><span data-stu-id="4fe10-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="4fe10-118">По умолчанию сведения о непредвиденных исключениях не отправляются клиенту во избежание утечки сведений о подробностях реализации службы за периметр безопасности службы.</span><span class="sxs-lookup"><span data-stu-id="4fe10-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> `FaultContract` <span data-ttu-id="4fe10-119">позволяет описать сбои в контракте и отметить определенные типы исключений как пригодные для передачи клиенту.</span><span class="sxs-lookup"><span data-stu-id="4fe10-119">provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> `FaultException<T>` <span data-ttu-id="4fe10-120">предоставляет механизм времени выполнения для отправки сбоев потребителям.</span><span class="sxs-lookup"><span data-stu-id="4fe10-120">provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="4fe10-121">Тем не менее, при отладке удобно иметь возможность просматривать внутренние сведения о сбое службы.</span><span class="sxs-lookup"><span data-stu-id="4fe10-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="4fe10-122">Для отключения описанного выше защитного поведения можно указать, что сведения о каждом необработанном исключении на сервере должны включаться в отправляемый клиенту сбой.</span><span class="sxs-lookup"><span data-stu-id="4fe10-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="4fe10-123">Это делается путем присвоения свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> значения `true`.</span><span class="sxs-lookup"><span data-stu-id="4fe10-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="4fe10-124">Задать это свойство можно в коде или в конфигурации, как показано в следующем образце.</span><span class="sxs-lookup"><span data-stu-id="4fe10-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="4fe10-125">Кроме того, поведение должно быть связано со службой, задав `behaviorConfiguration` атрибут службы в файле конфигурации значения «calculatorservicebehavior».</span><span class="sxs-lookup"><span data-stu-id="4fe10-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="4fe10-126">Для перехвата таких сбоев на клиенте необходимо перехватывать неуниверсальное исключение <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="4fe10-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="4fe10-127">Это поведение следует использовать только в целях отладки и ни в коем случае не в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="4fe10-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fe10-128">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="4fe10-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4fe10-129">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fe10-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4fe10-130">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fe10-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4fe10-131">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fe10-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fe10-132">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4fe10-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4fe10-133">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4fe10-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4fe10-134">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="4fe10-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fe10-135">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="4fe10-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
