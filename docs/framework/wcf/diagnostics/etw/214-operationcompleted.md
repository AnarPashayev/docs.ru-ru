---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: 6147c70448efb122cb43a2b42a1e9b59980fab29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278951"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="2fca9-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="2fca9-102">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="2fca9-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="2fca9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fca9-104">ID</span><span class="sxs-lookup"><span data-stu-id="2fca9-104">ID</span></span>|<span data-ttu-id="2fca9-105">214</span><span class="sxs-lookup"><span data-stu-id="2fca9-105">214</span></span>|  
|<span data-ttu-id="2fca9-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="2fca9-106">Keywords</span></span>|<span data-ttu-id="2fca9-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2fca9-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2fca9-108">Level</span><span class="sxs-lookup"><span data-stu-id="2fca9-108">Level</span></span>|<span data-ttu-id="2fca9-109">Сведения</span><span class="sxs-lookup"><span data-stu-id="2fca9-109">Information</span></span>|  
|<span data-ttu-id="2fca9-110">Канал</span><span class="sxs-lookup"><span data-stu-id="2fca9-110">Channel</span></span>|<span data-ttu-id="2fca9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2fca9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2fca9-112">Описание</span><span class="sxs-lookup"><span data-stu-id="2fca9-112">Description</span></span>  

 <span data-ttu-id="2fca9-113">Данное событие создается, когда `OperationInvoker` по умолчанию модели завершает вызов метода, который не сформировал исключение.</span><span class="sxs-lookup"><span data-stu-id="2fca9-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2fca9-114">Сообщение</span><span class="sxs-lookup"><span data-stu-id="2fca9-114">Message</span></span>  

 <span data-ttu-id="2fca9-115">OperationInvoker завершил вызов метода «%1».</span><span class="sxs-lookup"><span data-stu-id="2fca9-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="2fca9-116">Длительность вызова метода составила «%2» мс.</span><span class="sxs-lookup"><span data-stu-id="2fca9-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2fca9-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="2fca9-117">Details</span></span>  
  
|<span data-ttu-id="2fca9-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="2fca9-118">Data Item Name</span></span>|<span data-ttu-id="2fca9-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="2fca9-119">Data Item Type</span></span>|<span data-ttu-id="2fca9-120">Описание</span><span class="sxs-lookup"><span data-stu-id="2fca9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2fca9-121">Имя метода</span><span class="sxs-lookup"><span data-stu-id="2fca9-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="2fca9-122">Имя CLR метода, который был вызван `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="2fca9-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="2fca9-123">Длительность</span><span class="sxs-lookup"><span data-stu-id="2fca9-123">Duration</span></span>|`xs:long`|<span data-ttu-id="2fca9-124">Время в миллисекундах, которое потребовалось `OperationInvoker`, чтобы вызвать метод.</span><span class="sxs-lookup"><span data-stu-id="2fca9-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="2fca9-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="2fca9-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="2fca9-126">Для служб, размещенных на сервере, это поле служит уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="2fca9-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2fca9-127">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="2fca9-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2fca9-128">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="2fca9-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2fca9-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="2fca9-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2fca9-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2fca9-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
