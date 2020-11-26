---
title: Корреляция запросов и ответов
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: da7739af7368cd7ebb55ed0ea2511e10f0bcb3f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239072"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="82dd3-102">Корреляция запросов и ответов</span><span class="sxs-lookup"><span data-stu-id="82dd3-102">Request-Reply Correlation</span></span>

<span data-ttu-id="82dd3-103">Корреляция "запрос-ответ" используется с <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> парой для реализации двусторонней операции в службе рабочего процесса и с <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> парой, которая вызывает двустороннюю операцию в другой веб-службе.</span><span class="sxs-lookup"><span data-stu-id="82dd3-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="82dd3-104">При вызове двусторонней операции в службе WCF служба может быть традиционной процедурой Windows Communication Foundation (WCF) на основе кода или службой рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="82dd3-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="82dd3-105">Чтобы использовать корреляцию «запрос-ответ», необходимо использовать двустороннюю привязку, например <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="82dd3-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="82dd3-106">Шаги инициализации корреляции, связанные с вызовом или реализацией двусторонней операции, похожи и описаны в данном разделе.</span><span class="sxs-lookup"><span data-stu-id="82dd3-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="82dd3-107">Использование корреляции в двусторонней операции с действиями Receive/SendReply</span><span class="sxs-lookup"><span data-stu-id="82dd3-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  

 <span data-ttu-id="82dd3-108"><xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Пара используется для реализации двусторонней операции в службе рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="82dd3-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="82dd3-109">Среда выполнения использует корреляцию «запрос-ответ» для обеспечения отправки ответа нужному вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="82dd3-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="82dd3-110">Если рабочий процесс размещен при помощи объекта <xref:System.ServiceModel.Activities.WorkflowServiceHost>, как бывает со службами рабочего процесса, то достаточно инициализации корреляции по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="82dd3-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="82dd3-111">В этом сценарии в <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> рабочем процессе используется пара, и никакой конкретной конфигурации корреляции не требуется.</span><span class="sxs-lookup"><span data-stu-id="82dd3-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="82dd3-112">Явная инициализация корреляции «запрос-ответ»</span><span class="sxs-lookup"><span data-stu-id="82dd3-112">Explicitly Initializing Request-Reply Correlation</span></span>  

 <span data-ttu-id="82dd3-113">Если параллельно работают другие двусторонние операции, корреляция должна быть явно настроена.</span><span class="sxs-lookup"><span data-stu-id="82dd3-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="82dd3-114">Это можно сделать, указав <xref:System.ServiceModel.Activities.CorrelationHandle> и <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> , или поместив <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> внутри <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="82dd3-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="82dd3-115">В этом примере корреляция типа "запрос-ответ" настраивается для <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> пары.</span><span class="sxs-lookup"><span data-stu-id="82dd3-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="82dd3-116">Вместо явной настройки корреляции можно использовать действие <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="82dd3-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="82dd3-117"><xref:System.ServiceModel.Activities.CorrelationScope> предоставляет явный объект <xref:System.ServiceModel.Activities.CorrelationHandle> содержащимся в нем действиям обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="82dd3-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="82dd3-118">В этом примере <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> пара содержится внутри <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="82dd3-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="82dd3-119">Явная настройка корреляции не требуется.</span><span class="sxs-lookup"><span data-stu-id="82dd3-119">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="82dd3-120">Если требуются дополнительные корреляции, их можно настроить с помощью свойства <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> соответствующих действий по обмену сообщениями, использующих нужные типы `CorrelationInitializer`.</span><span class="sxs-lookup"><span data-stu-id="82dd3-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="82dd3-121">Использование корреляции в двусторонней операции с действиями Send/ReceiveReply</span><span class="sxs-lookup"><span data-stu-id="82dd3-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  

 <span data-ttu-id="82dd3-122">Хотя <xref:System.ServiceModel.Activities.Receive> действие может использоваться только в службе рабочего процесса, размещенной в <xref:System.ServiceModel.Activities.WorkflowServiceHost> , <xref:System.ServiceModel.Activities.Send> а <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> пара может использоваться в любом рабочем процессе, который должен вызывать метод в веб-службе.</span><span class="sxs-lookup"><span data-stu-id="82dd3-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="82dd3-123">Если рабочий процесс размещен при помощи <xref:System.ServiceModel.Activities.WorkflowServiceHost>, то действует по умолчанию корреляция, описанная в предыдущем разделе; в противном случае корреляцию необходимо настроить либо явно при помощи желаемого <xref:System.ServiceModel.Activities.CorrelationInitializer> и <xref:System.ServiceModel.Activities.CorrelationHandle>, либо при помощи неявного управления обработкой <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="82dd3-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="82dd3-124">При использовании **Добавление ссылки на службу** для службы с двусторонними операциями создаются действия, которые заключают <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> действие пары "запрос-ответ" внутренним образом с явно указанными корреляцией.</span><span class="sxs-lookup"><span data-stu-id="82dd3-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
