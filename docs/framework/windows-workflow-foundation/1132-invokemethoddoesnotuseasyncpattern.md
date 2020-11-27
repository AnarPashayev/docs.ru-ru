---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294161"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="299be-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="299be-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="299be-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="299be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="299be-104">ID</span><span class="sxs-lookup"><span data-stu-id="299be-104">ID</span></span>|<span data-ttu-id="299be-105">1132</span><span class="sxs-lookup"><span data-stu-id="299be-105">1132</span></span>|  
|<span data-ttu-id="299be-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="299be-106">Keywords</span></span>|<span data-ttu-id="299be-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="299be-107">WFRuntime</span></span>|  
|<span data-ttu-id="299be-108">Level</span><span class="sxs-lookup"><span data-stu-id="299be-108">Level</span></span>|<span data-ttu-id="299be-109">Сведения</span><span class="sxs-lookup"><span data-stu-id="299be-109">Information</span></span>|  
|<span data-ttu-id="299be-110">Канал</span><span class="sxs-lookup"><span data-stu-id="299be-110">Channel</span></span>|<span data-ttu-id="299be-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="299be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="299be-112">Описание</span><span class="sxs-lookup"><span data-stu-id="299be-112">Description</span></span>  

 <span data-ttu-id="299be-113">На шаге CacheMetadata действие InvokeMethod указывает, что при вызове метода не используется асинхронный шаблон.</span><span class="sxs-lookup"><span data-stu-id="299be-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="299be-114">Сообщение</span><span class="sxs-lookup"><span data-stu-id="299be-114">Message</span></span>  

 <span data-ttu-id="299be-115">Метод InvokeMethod «%1»: в методе не используется асинхронная модель.</span><span class="sxs-lookup"><span data-stu-id="299be-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="299be-116">Сведения</span><span class="sxs-lookup"><span data-stu-id="299be-116">Details</span></span>  
  
|<span data-ttu-id="299be-117">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="299be-117">Data Item Name</span></span>|<span data-ttu-id="299be-118">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="299be-118">Data Item Type</span></span>|<span data-ttu-id="299be-119">Описание</span><span class="sxs-lookup"><span data-stu-id="299be-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="299be-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="299be-120">InvokeMethod</span></span>|<span data-ttu-id="299be-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="299be-121">xs:string</span></span>|<span data-ttu-id="299be-122">Отображаемое имя действия InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="299be-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="299be-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="299be-123">AppDomain</span></span>|<span data-ttu-id="299be-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="299be-124">xs:string</span></span>|<span data-ttu-id="299be-125">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="299be-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
