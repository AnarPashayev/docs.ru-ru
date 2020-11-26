---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: dc47aa36b5a409c89aaf7963ce51f11cdf84b0fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247581"
---
# <a name="499---transferemitted"></a><span data-ttu-id="4257c-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="4257c-102">499 - TransferEmitted</span></span>

## <a name="properties"></a><span data-ttu-id="4257c-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="4257c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4257c-104">ID</span><span class="sxs-lookup"><span data-stu-id="4257c-104">ID</span></span>|<span data-ttu-id="4257c-105">499</span><span class="sxs-lookup"><span data-stu-id="4257c-105">499</span></span>|  
|<span data-ttu-id="4257c-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="4257c-106">Keywords</span></span>|<span data-ttu-id="4257c-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="4257c-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="4257c-108">Level</span><span class="sxs-lookup"><span data-stu-id="4257c-108">Level</span></span>|<span data-ttu-id="4257c-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="4257c-109">LogAlways</span></span>|  
|<span data-ttu-id="4257c-110">Канал</span><span class="sxs-lookup"><span data-stu-id="4257c-110">Channel</span></span>|<span data-ttu-id="4257c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4257c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4257c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="4257c-112">Description</span></span>  

 <span data-ttu-id="4257c-113">Это событие формируется при возникновении события передачи.</span><span class="sxs-lookup"><span data-stu-id="4257c-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4257c-114">Сообщение</span><span class="sxs-lookup"><span data-stu-id="4257c-114">Message</span></span>  

 <span data-ttu-id="4257c-115">Произошло событие передачи.</span><span class="sxs-lookup"><span data-stu-id="4257c-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4257c-116">Сведения</span><span class="sxs-lookup"><span data-stu-id="4257c-116">Details</span></span>  
  
|<span data-ttu-id="4257c-117">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="4257c-117">Data Item Name</span></span>|<span data-ttu-id="4257c-118">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="4257c-118">Data Item Type</span></span>|<span data-ttu-id="4257c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="4257c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4257c-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="4257c-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="4257c-121">Для служб, размещенных на веб-узле, это поле является уникальным идентификатором службы в веб-иерархии.</span><span class="sxs-lookup"><span data-stu-id="4257c-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4257c-122">Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="4257c-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4257c-123">Пример: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="4257c-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4257c-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="4257c-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4257c-125">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4257c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
