---
title: Конечные точки Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: d3281ac648ecb43ce5248fe86b6da1d268e382f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262155"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="9ffc0-102">Конечные точки Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9ffc0-102">Windows Communication Foundation Endpoints</span></span>

<span data-ttu-id="9ffc0-103">Все взаимодействия со службой Windows Communication Foundation (WCF) осуществляется через *конечные точки* службы.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="9ffc0-104">Конечные точки предоставляют клиентам доступ к функциональным возможностям, предлагаемым службой WCF.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="9ffc0-105">Общие сведения о создании конечной точки см. в разделе [Общие сведения о создании конечной точки](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9ffc0-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="9ffc0-106">Каждая конечная точка содержит:</span><span class="sxs-lookup"><span data-stu-id="9ffc0-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="9ffc0-107">адрес, показывающий, где можно найти конечную точку;</span><span class="sxs-lookup"><span data-stu-id="9ffc0-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="9ffc0-108">привязку, показывающую, как клиент может связаться с конечной точкой;</span><span class="sxs-lookup"><span data-stu-id="9ffc0-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="9ffc0-109">контракт, определяющий доступные методы.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="9ffc0-110">Дополнительные сведения по способам задания этих отдельных частей конечной точки см. в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="9ffc0-111">Задание адреса конечной точки</span><span class="sxs-lookup"><span data-stu-id="9ffc0-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="9ffc0-112">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="9ffc0-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="9ffc0-113">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="9ffc0-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="9ffc0-114">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="9ffc0-114">In This Section</span></span>  

 [<span data-ttu-id="9ffc0-115">Общие сведения о создании конечных точек</span><span class="sxs-lookup"><span data-stu-id="9ffc0-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="9ffc0-116">Описывает структуру конечной точки и общие шаги по определению конечной точки в конфигурации и в коде, а также по использованию конечных точек по умолчанию, привязок и поведений, предоставляемых средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="9ffc0-117">Задание адреса конечной точки</span><span class="sxs-lookup"><span data-stu-id="9ffc0-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="9ffc0-118">Описывает, как взаимодействие со службой WCF осуществляется через конечные точки.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="9ffc0-119">Практическое руководство. Создание конечной точки службы в конфигурации</span><span class="sxs-lookup"><span data-stu-id="9ffc0-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="9ffc0-120">Описание создания конечной точки службы в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="9ffc0-121">Практическое руководство. Создание конечной точки службы в коде</span><span class="sxs-lookup"><span data-stu-id="9ffc0-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="9ffc0-122">Описание создания конечной точки службы в коде.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="9ffc0-123">Публикация конечных точек метаданных</span><span class="sxs-lookup"><span data-stu-id="9ffc0-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="9ffc0-124">Описание публикации метаданных путем публикации конечных точек метаданных в конфигурации и в коде.</span><span class="sxs-lookup"><span data-stu-id="9ffc0-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9ffc0-125">Справочник</span><span class="sxs-lookup"><span data-stu-id="9ffc0-125">Reference</span></span>  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="9ffc0-126">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="9ffc0-126">Related Sections</span></span>  

 [<span data-ttu-id="9ffc0-127">Базовый жизненный цикл программирования</span><span class="sxs-lookup"><span data-stu-id="9ffc0-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
