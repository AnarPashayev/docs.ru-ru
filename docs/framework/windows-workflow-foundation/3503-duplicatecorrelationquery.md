---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755601"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="a3a78-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="a3a78-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="a3a78-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="a3a78-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3a78-104">ID</span><span class="sxs-lookup"><span data-stu-id="a3a78-104">ID</span></span>|<span data-ttu-id="a3a78-105">3503</span><span class="sxs-lookup"><span data-stu-id="a3a78-105">3503</span></span>|  
|<span data-ttu-id="a3a78-106">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="a3a78-106">Keywords</span></span>|<span data-ttu-id="a3a78-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a3a78-107">WFServices</span></span>|  
|<span data-ttu-id="a3a78-108">Уровень</span><span class="sxs-lookup"><span data-stu-id="a3a78-108">Level</span></span>|<span data-ttu-id="a3a78-109">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="a3a78-109">Warning</span></span>|  
|<span data-ttu-id="a3a78-110">Канал</span><span class="sxs-lookup"><span data-stu-id="a3a78-110">Channel</span></span>|<span data-ttu-id="a3a78-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a3a78-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3a78-112">Описание</span><span class="sxs-lookup"><span data-stu-id="a3a78-112">Description</span></span>  
 <span data-ttu-id="a3a78-113">Указывает, что обнаружен повторяющийся запрос CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="a3a78-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="a3a78-114">Повторяющийся запрос не будет использоваться при расчете корреляции.</span><span class="sxs-lookup"><span data-stu-id="a3a78-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3a78-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="a3a78-115">Message</span></span>  
 <span data-ttu-id="a3a78-116">Обнаружен повторяющийся запрос CorrelationQuery с параметром Where=«%1».</span><span class="sxs-lookup"><span data-stu-id="a3a78-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="a3a78-117">Это дубликат не будет использоваться при расчете корреляции.</span><span class="sxs-lookup"><span data-stu-id="a3a78-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3a78-118">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="a3a78-118">Details</span></span>  
  
|<span data-ttu-id="a3a78-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="a3a78-119">Data Item Name</span></span>|<span data-ttu-id="a3a78-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="a3a78-120">Data Item Type</span></span>|<span data-ttu-id="a3a78-121">Описание</span><span class="sxs-lookup"><span data-stu-id="a3a78-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3a78-122">Where</span><span class="sxs-lookup"><span data-stu-id="a3a78-122">Where</span></span>|<span data-ttu-id="a3a78-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3a78-123">xs:string</span></span>|<span data-ttu-id="a3a78-124">Часть Where в запросе корреляции.</span><span class="sxs-lookup"><span data-stu-id="a3a78-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="a3a78-125">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="a3a78-125">AppDomain</span></span>|<span data-ttu-id="a3a78-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3a78-126">xs:string</span></span>|<span data-ttu-id="a3a78-127">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a3a78-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
