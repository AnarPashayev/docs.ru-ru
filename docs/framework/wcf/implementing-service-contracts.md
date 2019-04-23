---
title: Реализация контрактов служб
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196324"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="5634d-102">Реализация контрактов служб</span><span class="sxs-lookup"><span data-stu-id="5634d-102">Implementing Service Contracts</span></span>
<span data-ttu-id="5634d-103">Служба - это класс, который предоставляет клиентам имеющиеся функциональные возможности в одной или нескольких конечных точках.</span><span class="sxs-lookup"><span data-stu-id="5634d-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="5634d-104">Чтобы создать службу, напишите класс, реализующий контракт службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5634d-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="5634d-105">Это можно сделать одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="5634d-105">You can do this in one of two ways.</span></span> <span data-ttu-id="5634d-106">Во-первых, можно определить контракт отдельно в качестве интерфейса, а затем создать класс, реализующий этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5634d-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="5634d-107">Во-вторых, можно непосредственно создать класс и контракт, разместив атрибут <xref:System.ServiceModel.ServiceContractAttribute> в самом классе, а атрибут <xref:System.ServiceModel.OperationContractAttribute> - в методах, доступных клиентам службы.</span><span class="sxs-lookup"><span data-stu-id="5634d-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="5634d-108">Создание класса службы</span><span class="sxs-lookup"><span data-stu-id="5634d-108">Creating a service class</span></span>  
 <span data-ttu-id="5634d-109">Ниже приведен пример службы, реализующей отдельно определенный контракт `IMath`.</span><span class="sxs-lookup"><span data-stu-id="5634d-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="5634d-110">Кроме того, контракт может непосредственно предоставляться службой.</span><span class="sxs-lookup"><span data-stu-id="5634d-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="5634d-111">Ниже приведен пример класса службы, который определяет и реализует контракт `MathService`.</span><span class="sxs-lookup"><span data-stu-id="5634d-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="5634d-112">Обратите внимание, что описанные службы предоставляют разные контракты, так как имена контрактов различаются.</span><span class="sxs-lookup"><span data-stu-id="5634d-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="5634d-113">В первом случае предоставленный контракт называется "`IMath`", а во втором - "`MathService`".</span><span class="sxs-lookup"><span data-stu-id="5634d-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="5634d-114">Некоторые свойства (такие как параллелизм и создание экземпляров) можно задать на уровне реализации службы и операции.</span><span class="sxs-lookup"><span data-stu-id="5634d-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="5634d-115">Дополнительные сведения см. в разделе [проектирование и реализация служб](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="5634d-115">For more information, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="5634d-116">После реализации контракта службы необходимо создать для службы одну или более конечных точек.</span><span class="sxs-lookup"><span data-stu-id="5634d-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="5634d-117">Дополнительные сведения см. в разделе [Общие сведения о создании конечной точки](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5634d-117">For more information, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="5634d-118">Дополнительные сведения о запуске службы см. в разделе [размещение служб](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="5634d-118">For more information about how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5634d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="5634d-119">See also</span></span>

- [<span data-ttu-id="5634d-120">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="5634d-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="5634d-121">Практическое руководство. Создание службы с помощью класса контракта</span><span class="sxs-lookup"><span data-stu-id="5634d-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="5634d-122">Практическое руководство. Создание службы с помощью интерфейса контракта</span><span class="sxs-lookup"><span data-stu-id="5634d-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="5634d-123">Указание поведения службы во время выполнения</span><span class="sxs-lookup"><span data-stu-id="5634d-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
