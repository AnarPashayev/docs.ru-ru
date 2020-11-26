---
title: Обработка ошибок WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 72db5db9f6b4a3cd2ba62fe938fcfeed2dfda1e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240944"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="d3b5f-102">Обработка ошибок WCF</span><span class="sxs-lookup"><span data-stu-id="d3b5f-102">WCF Error Handling</span></span>

<span data-ttu-id="d3b5f-103">Ошибки, с которыми столкнулось приложение WCF, относится к одной из трех групп:</span><span class="sxs-lookup"><span data-stu-id="d3b5f-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="d3b5f-104">Ошибки обмена данными</span><span class="sxs-lookup"><span data-stu-id="d3b5f-104">Communication Errors</span></span>  
  
2. <span data-ttu-id="d3b5f-105">Ошибки прокси-сервера/канала</span><span class="sxs-lookup"><span data-stu-id="d3b5f-105">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="d3b5f-106">Ошибки приложения</span><span class="sxs-lookup"><span data-stu-id="d3b5f-106">Application Errors</span></span>  
  
 <span data-ttu-id="d3b5f-107">Ошибки обмена данными возникают, когда сеть недоступна, клиент использует неверный адрес или узел службы не прослушивает входящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="d3b5f-108">Ошибки данного типа возвращаются клиенту в виде производных классов <xref:System.ServiceModel.CommunicationException> или <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="d3b5f-109">Ошибки прокси-сервера/канала - это ошибки, возникающие непосредственно в канале или на прокси-сервере.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="d3b5f-110">К ошибкам этого типа относятся попытка использовать прокси-сервер или канал, который был закрыт, несоответствие контракта между клиентом и службой или отклонение службой учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="d3b5f-111">Относящихся к этой категории ошибок различных типов настолько много, что их невозможно здесь перечислить.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="d3b5f-112">Ошибки этого типа возвращаются клиенту в исходном виде (какие-либо преобразования над объектами исключений не выполняются).</span><span class="sxs-lookup"><span data-stu-id="d3b5f-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="d3b5f-113">Ошибки приложения возникают во время выполнения одной из операций службы.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="d3b5f-114">Ошибки такого рода передаются клиенту как <xref:System.ServiceModel.FaultException> или <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="d3b5f-115">Обработка ошибок в WCF выполняется одним или несколькими методами из следующих:</span><span class="sxs-lookup"><span data-stu-id="d3b5f-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="d3b5f-116">Непосредственная обработка возникшего исключения.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="d3b5f-117">Этот метод применяется только для ошибок обмена данными и ошибок прокси-сервера/канала.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-117">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="d3b5f-118">Использование контрактов сбоя</span><span class="sxs-lookup"><span data-stu-id="d3b5f-118">Using fault contracts</span></span>  
  
- <span data-ttu-id="d3b5f-119">Реализация интерфейса <xref:System.ServiceModel.Dispatcher.IErrorHandler></span><span class="sxs-lookup"><span data-stu-id="d3b5f-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="d3b5f-120">Обработка событий <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="d3b5f-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="d3b5f-121">Контракты сбоя</span><span class="sxs-lookup"><span data-stu-id="d3b5f-121">Fault Contracts</span></span>  

 <span data-ttu-id="d3b5f-122">Контракты сбоев позволяют определять ошибки, которые могут возникать во время выполнения работы службы, независимо от платформы.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="d3b5f-123">По умолчанию все ошибки, возникающие при работе службы, возвращаются клиенту в виде объекта <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="d3b5f-124">Объект <xref:System.ServiceModel.FaultException> содержит очень мало сведений.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="d3b5f-125">Для управления тем, какие сведения передаются клиенту, можно определить контракт сбоя и возвращать ошибки в виде исключения <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="d3b5f-126">Дополнительные сведения см. [в разделе Указание и обработка ошибок в контрактах и службах](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="d3b5f-126">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="d3b5f-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="d3b5f-127">IErrorHandler</span></span>  

 <span data-ttu-id="d3b5f-128">Интерфейс <xref:System.ServiceModel.Dispatcher.IErrorHandler> обеспечивает больший контроль над тем, как приложение WCF будет реагировать на ошибки.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="d3b5f-129">Он предоставляет разработчику полный доступ над содержанием сообщений об ошибках, которые возвращаются клиенту, и позволяет выполнять пользовательскую обработку ошибок, например ведение журнала.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="d3b5f-130">Дополнительные сведения о <xref:System.ServiceModel.Dispatcher.IErrorHandler> и [расширении управления обработкой ошибок и созданием отчетов](./samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="d3b5f-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="d3b5f-131">События ServiceHost</span><span class="sxs-lookup"><span data-stu-id="d3b5f-131">ServiceHost Events</span></span>  

 <span data-ttu-id="d3b5f-132">Класс <xref:System.ServiceModel.ServiceHost> применяется для размещения служб и определяет несколько событий, которые могут потребоваться для обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="d3b5f-133">Пример:</span><span class="sxs-lookup"><span data-stu-id="d3b5f-133">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="d3b5f-134">Дополнительные сведения см. в разделе <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-134">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
