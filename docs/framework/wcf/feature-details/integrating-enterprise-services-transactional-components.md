---
title: Интеграция транзакционных компонентов служб Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: c73be31bef67f1de818f7b04181a3540bbd7caa8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991539"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Интеграция транзакционных компонентов служб Enterprise Services
Windows Communication Foundation (WCF) предоставляет автоматический механизм интеграции с корпоративными службами (см. раздел [Интеграция с приложениями COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Однако для разработки служб, которые внутренне используют транзакционные компоненты, размещенные внутри служб Enterprise Services, может потребоваться гибкость. Поскольку функции транзакций WCF основаны на <xref:System.Transactions> инфраструктуре, процесс интеграции корпоративных служб с WCF идентичен тому, что позволяет задавать взаимодействие между <xref:System.Transactions> службами и Enterprise Services, как описано в [Взаимодействие с корпоративными службами и транзакциями COM+](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Чтобы обеспечить требуемый уровень взаимодействия между входящей поточной транзакцией и транзакцией контекста COM+, реализация службы должна создать экземпляр <xref:System.Transactions.TransactionScope> и использовать соответствующее значение из перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Интеграция служб Enterprise Services с операцией службы  
 В представленном ниже коде показана операция с разрешенным потоком транзакций, которая создает область <xref:System.Transactions.TransactionScope> с параметром <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. В этом сценарии используются следующие условия.  
  
- Если клиент передает транзакцию, операция, включая вызов компонента Enterprise Services, выполняется в рамках области этой транзакции. Использование параметра <xref:System.Transactions.EnterpriseServicesInteropOption.Full> обеспечивает синхронизацию транзакции с контекстом <xref:System.EnterpriseServices>. Это означает, что внешняя транзакция для <xref:System.Transactions> и <xref:System.EnterpriseServices> одна и та же.  
  
- Если клиент не передает транзакцию, при присвоении <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> значения `true` для операции создается новая область транзакции. Аналогично, использование параметра <xref:System.Transactions.EnterpriseServicesInteropOption.Full> обеспечивает идентичность транзакции операции и транзакции, используемой внутри контекста компонента <xref:System.EnterpriseServices>.  
  
 Любые дополнительные вызовы метода также происходят в пределах области той же транзакции операции.  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Если между текущей транзакцией операции и вызовами транзакционных компонентов Enterprise Services синхронизация не требуется, при создании экземпляра <xref:System.Transactions.EnterpriseServicesInteropOption.None> используйте параметр <xref:System.Transactions.TransactionScope>.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Интеграция служб Enterprise Services с клиентом  
 В представленном ниже клиентском коде показано использование экземпляра <xref:System.Transactions.TransactionScope> с параметром <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. В этом сценарии вызовы операций службы, которые поддерживают поток транзакций, происходят в рамках области той же транзакции, что и вызовы компонентов Enterprise Services.  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a>См. также

- [Интеграция с приложениями COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Интеграция с приложениями COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
