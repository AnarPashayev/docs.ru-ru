---
title: Службы и транзакции
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: e60f84aafe6c62a657cd3f27c9ccdb6b65186c35
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235913"
---
# <a name="services-and-transactions"></a><span data-ttu-id="84a0c-102">Службы и транзакции</span><span class="sxs-lookup"><span data-stu-id="84a0c-102">Services and Transactions</span></span>

<span data-ttu-id="84a0c-103">Приложения Windows Communication Foundation (WCF) могут инициировать транзакцию в клиенте и координировать транзакцию внутри операции службы.</span><span class="sxs-lookup"><span data-stu-id="84a0c-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="84a0c-104">Клиенты могут инициировать транзакцию, вызвать несколько операций службы и обеспечить, чтобы операции службы либо фиксировались, либо откатывались как единый блок.</span><span class="sxs-lookup"><span data-stu-id="84a0c-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="84a0c-105">Чтобы включить поведение транзакции в контракте службы, укажите атрибут <xref:System.ServiceModel.ServiceBehaviorAttribute> и задайте его свойства <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> и <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> для операций службы, для которых требуются клиентские транзакции.</span><span class="sxs-lookup"><span data-stu-id="84a0c-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="84a0c-106">Параметр <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> указывает, следует ли автоматически завершать транзакцию, в которой выполняется метод, при отсутствии необработанных исключений.</span><span class="sxs-lookup"><span data-stu-id="84a0c-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="84a0c-107">Дополнительные сведения об этих атрибутах см. в разделе [атрибуты транзакций ServiceModel](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="84a0c-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="84a0c-108">Работа, выполняемая операциями службы и управляемая диспетчером ресурсов (например, ведение журнала обновления базы данных), является частью транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="84a0c-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="84a0c-109">В следующем примере показано использование атрибутов <xref:System.ServiceModel.ServiceBehaviorAttribute> и <xref:System.ServiceModel.OperationBehaviorAttribute> для управления поведением транзакций на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="84a0c-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="84a0c-110">Вы можете включить транзакции и поток транзакций, настроив привязки клиента и службы для использования протокола WS-AtomicTransaction и задав [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) для элемента значение `true` , как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="84a0c-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="84a0c-111">Клиенты могут начинать транзакции путем создания <xref:System.Transactions.TransactionScope> и вызова операций службы в области транзакции.</span><span class="sxs-lookup"><span data-stu-id="84a0c-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="84a0c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="84a0c-112">See also</span></span>

- [<span data-ttu-id="84a0c-113">Поддержка транзакций в System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="84a0c-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="84a0c-114">Модели транзакций</span><span class="sxs-lookup"><span data-stu-id="84a0c-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="84a0c-115">Поток транзакций WS</span><span class="sxs-lookup"><span data-stu-id="84a0c-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
