---
title: Поток транзакций WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: cde5599734dbeb450e10b2b74cf035b41129d653
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296099"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="4c764-102">Поток транзакций WS</span><span class="sxs-lookup"><span data-stu-id="4c764-102">WS Transaction Flow</span></span>
<span data-ttu-id="4c764-103">В этом образце показано использование координируемой клиентом транзакции и параметры клиента и сервера для организации потока транзакции с использованием протокола WS-Atomic Transaction или OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="4c764-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="4c764-104">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) , реализующем службу калькулятора, но атрибуты операций, чтобы продемонстрировать использование `TransactionFlowAttribute` с **TransactionFlowOption** Перечисление, чтобы определить, какие транзакции уровень включения потока.</span><span class="sxs-lookup"><span data-stu-id="4c764-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="4c764-105">В области поточной транзакции в базу данных записывается журнал запрошенных операций, который сохраняется до завершения транзакции, координируемой клиентом, и если транзакция клиента не завершена, транзакция веб-службы следит, чтобы соответствующие обновления базы данных не были зафиксированы.</span><span class="sxs-lookup"><span data-stu-id="4c764-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c764-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="4c764-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4c764-107">После установления связи со службой и транзакцией клиент обращается к нескольким операциям службы.</span><span class="sxs-lookup"><span data-stu-id="4c764-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="4c764-108">Контракт службы определяется показанным ниже образом, при этом все операции показывают различные параметры `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="4c764-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 <span data-ttu-id="4c764-109">Определяет операции в порядке их выполнения:</span><span class="sxs-lookup"><span data-stu-id="4c764-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="4c764-110">запрос операции `Add` должен включать поточную транзакцию;</span><span class="sxs-lookup"><span data-stu-id="4c764-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="4c764-111">запрос операции `Subtract` может включать поточную транзакцию;</span><span class="sxs-lookup"><span data-stu-id="4c764-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="4c764-112">запрос операции `Multiply` не может содержать поточную транзакцию из-за явно установленного параметра NotAllowed;</span><span class="sxs-lookup"><span data-stu-id="4c764-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="4c764-113">запрос операции `Divide` не может содержать поточную транзакцию из-за отсутствия атрибута `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="4c764-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="4c764-114">Чтобы включить поток транзакций, привязок, у которых [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) включено свойство должно использоваться в дополнение к соответствующим атрибутам операции.</span><span class="sxs-lookup"><span data-stu-id="4c764-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="4c764-115">В этом образце конфигурация службы предоставляет в дополнение к конечной точке обмена метаданными конечные точки TCP и HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c764-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="4c764-116">Конечная точка TCP и HTTP используют следующие привязки, оба из которых имеют [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) включено свойство.</span><span class="sxs-lookup"><span data-stu-id="4c764-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="4c764-117">Предоставляемая системой привязка netTcpBinding позволяет задавать протокол transactionProtocol, а предоставляемая системой привязка wsHttpBinding использует только протокол WSAtomicTransactionOctober2004 с большими возможностями взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="4c764-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="4c764-118">OleTransactions, протокол доступно только для использования клиентами Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4c764-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="4c764-119">Для класса, реализующего интерфейс `ICalculator`, всем методам в качестве атрибута задано свойство <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>, имеющее значение `true`.</span><span class="sxs-lookup"><span data-stu-id="4c764-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="4c764-120">Этот параметр означает, что все действия, предпринятые в рамках метода, происходят в области транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c764-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="4c764-121">В этом случае предпринятые действия включают запись в журнал базы данных.</span><span class="sxs-lookup"><span data-stu-id="4c764-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="4c764-122">Если запрос операции включает поточную транзакцию, действия происходят в области входящей транзакции или автоматически создается новая область транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c764-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c764-123">Свойство <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> определяет локальное поведение реализаций методов службы и не определяет возможность или требования клиента передавать транзакцию.</span><span class="sxs-lookup"><span data-stu-id="4c764-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="4c764-124">На стороне клиента параметры операций `TransactionFlowOption` службы отражаются в создаваемом определении интерфейса `ICalculator` клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="4c764-125">Параметры свойства `transactionFlow` службы также отражаются в конфигурации приложения клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="4c764-126">Клиент может выбрать транспорт и протокол, выбрав соответствующее имя `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="4c764-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  <span data-ttu-id="4c764-127">Поведение этого образца не зависит от выбранного протокола или транспорта.</span><span class="sxs-lookup"><span data-stu-id="4c764-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="4c764-128">После установления связи со службой клиент создает новую область `TransactionScope`, в которую заключены вызовы операций службы.</span><span class="sxs-lookup"><span data-stu-id="4c764-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="4c764-129">Используются следующие вызовы операций.</span><span class="sxs-lookup"><span data-stu-id="4c764-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="4c764-130">Запрос `Add` передает нужную транзакцию службе, а действия службы происходят в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="4c764-131">Первый запрос `Subtract` также передает разрешенную транзакцию службе, действия службы снова происходят в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="4c764-132">Второй запрос `Subtract` выполняется в новой области транзакции, объявленной с помощью параметра `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="4c764-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="4c764-133">Он подавляет первоначальную внешнюю транзакцию клиента, и запрос не передает транзакцию службе.</span><span class="sxs-lookup"><span data-stu-id="4c764-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="4c764-134">Этот подход позволяет клиенту явно отказаться и защититься от передачи транзакции службе, если в этом нет необходимости.</span><span class="sxs-lookup"><span data-stu-id="4c764-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="4c764-135">Действия службы происходят в области новой, несвязанной транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c764-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="4c764-136">`Multiply` Запрос передает транзакцию службе, так как созданное клиентом определение `ICalculator` интерфейс включает <xref:System.ServiceModel.TransactionFlowAttribute> присвоено <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="4c764-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="4c764-137">Запрос `Divide` не передает транзакцию службе, так как, опять же, созданное клиентом определение интерфейса `ICalculator` не включает `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4c764-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="4c764-138">Действия службы снова происходят в области новой, несвязанной транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c764-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="4c764-139">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4c764-140">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4c764-141">Журнал запросов операций службы отображается в окне консоли службы.</span><span class="sxs-lookup"><span data-stu-id="4c764-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="4c764-142">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="4c764-143">После успешного выполнения область транзакции клиента завершается, а все действия, предпринятые в этой области, фиксируются.</span><span class="sxs-lookup"><span data-stu-id="4c764-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="4c764-144">В частности, в базе данных службы сохраняются 5 указанных записей.</span><span class="sxs-lookup"><span data-stu-id="4c764-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="4c764-145">Первые две произошли в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="4c764-146">Если в любом месте области `TransactionScope` клиента возникло исключение, транзакция не может завершиться.</span><span class="sxs-lookup"><span data-stu-id="4c764-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="4c764-147">Из-за этого записи, помещенные в журнал в этой области, не фиксируются в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4c764-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="4c764-148">Чтобы посмотреть на эту ситуацию, повторите выполнение образца, преобразовав в комментарий вызов для завершения внешней области `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="4c764-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="4c764-149">При таком выполнении записываются только 3 последних действия (из второго запроса `Subtract` и запросов `Multiply` и `Divide`), потому что к ним не передавалась транзакция клиента.</span><span class="sxs-lookup"><span data-stu-id="4c764-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4c764-150">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="4c764-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4c764-151">Чтобы построить версию решения C# или Visual Basic .NET, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="4c764-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="4c764-152">Убедитесь, что установлен SQL Server Express Edition, SQL Server, а в файле конфигурации приложения службы правильно задана строка подключения.</span><span class="sxs-lookup"><span data-stu-id="4c764-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="4c764-153">Чтобы запустить образец без использования базы данных, задайте `usingSql` значение в файле конфигурации приложения службы для</span><span class="sxs-lookup"><span data-stu-id="4c764-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to</span></span> `false`  
  
3. <span data-ttu-id="4c764-154">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c764-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4c764-155">Если планируется выполнять образец на нескольких компьютерах, включите координатор распределенных транзакций согласно приведенным ниже инструкциям и воспользуйтесь средством WsatConfig.exe из пакета Windows SDK для поддержки сетевых транзакций WCF.</span><span class="sxs-lookup"><span data-stu-id="4c764-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="4c764-156">См. в разделе [Настройка поддержки транзакций WS-Atomic](https://go.microsoft.com/fwlink/?LinkId=190370) сведения о настройке WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="4c764-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="4c764-157">При запуске образца, на одном компьютере или на разных компьютерах, необходимо настроить Майкрософт распределенных транзакций координатора) (MSDTC) включив поток сетевых транзакций, и используйте средство WsatConfig.exe для включения поддержки сети транзакций WCF.</span><span class="sxs-lookup"><span data-stu-id="4c764-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="4c764-158">Настройка координатора распределенных транзакций (Майкрософта) (MSDTC) на поддержку выполнения образца</span><span class="sxs-lookup"><span data-stu-id="4c764-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="4c764-159">На компьютере службы, работающем под управлением Windows Server 2003 или Windows XP настройте MSDTC, разрешите входящие сетевые транзакции, согласно следующим инструкциям.</span><span class="sxs-lookup"><span data-stu-id="4c764-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="4c764-160">Из **запустить** меню перейдите к **панели управления**, затем **Администрирование**, а затем **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="4c764-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c764-161">Разверните **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="4c764-161">Expand **Component Services**.</span></span> <span data-ttu-id="4c764-162">Откройте **компьютеров** папки.</span><span class="sxs-lookup"><span data-stu-id="4c764-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="4c764-163">Щелкните правой кнопкой мыши **Мой компьютер** и выберите **свойства**.</span><span class="sxs-lookup"><span data-stu-id="4c764-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="4c764-164">На **MSDTC** щелкните **конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="4c764-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="4c764-165">Проверьте **сетевой доступ DTC** и **Разрешить входящий**.</span><span class="sxs-lookup"><span data-stu-id="4c764-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="4c764-166">Нажмите кнопку **ОК**, затем нажмите кнопку **Да** перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4c764-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="4c764-167">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="4c764-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="4c764-168">На компьютере службы, работающем под управлением Windows Server 2008 или Windows Vista настройте MSDTC, разрешив входящие сетевые транзакции, согласно следующим инструкциям.</span><span class="sxs-lookup"><span data-stu-id="4c764-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="4c764-169">Из **запустить** меню перейдите к **панели управления**, затем **Администрирование**, а затем **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="4c764-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c764-170">Разверните **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="4c764-170">Expand **Component Services**.</span></span> <span data-ttu-id="4c764-171">Откройте **компьютеров** папки.</span><span class="sxs-lookup"><span data-stu-id="4c764-171">Open the **Computers** folder.</span></span> <span data-ttu-id="4c764-172">Выберите **координатор распределенных транзакций**.</span><span class="sxs-lookup"><span data-stu-id="4c764-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="4c764-173">Щелкните правой кнопкой мыши **Координатор распределенных транзакций** и выберите **свойства**.</span><span class="sxs-lookup"><span data-stu-id="4c764-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="4c764-174">На **безопасности** вкладке **сетевой доступ DTC** и **Разрешить входящие**.</span><span class="sxs-lookup"><span data-stu-id="4c764-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="4c764-175">Нажмите кнопку **ОК**, затем нажмите кнопку **Да** перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4c764-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="4c764-176">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="4c764-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="4c764-177">На клиентском компьютере настройте координатор распределенных транзакций, чтобы он разрешал исходящие сетевые транзакции.</span><span class="sxs-lookup"><span data-stu-id="4c764-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="4c764-178">Из **запустить** меню перейдите к `Control Panel`, затем **Администрирование**, а затем **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="4c764-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="4c764-179">Щелкните правой кнопкой мыши **Мой компьютер** и выберите **свойства**.</span><span class="sxs-lookup"><span data-stu-id="4c764-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="4c764-180">На **MSDTC** щелкните **конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="4c764-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="4c764-181">Проверьте **сетевой доступ DTC** и **Разрешить исходящий трафик**.</span><span class="sxs-lookup"><span data-stu-id="4c764-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="4c764-182">Нажмите кнопку **ОК**, затем нажмите кнопку **Да** перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4c764-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="4c764-183">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="4c764-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c764-184">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4c764-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4c764-185">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4c764-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4c764-186">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="4c764-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4c764-187">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="4c764-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
