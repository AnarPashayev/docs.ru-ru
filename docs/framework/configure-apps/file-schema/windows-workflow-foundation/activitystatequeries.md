---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 90acda7277fd276f43a619a014fbce103261aa1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790407"
---
# <a name="activitystatequeries"></a><span data-ttu-id="30ed7-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="30ed7-101">\<activityStateQueries></span></span>
<span data-ttu-id="30ed7-102">Представляет коллекцию запросов, которые используются для отслеживания изменений жизненного цикла действий, составляющих экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="30ed7-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="30ed7-103">Например можно хранить список всякий раз по завершении действия «Send E-Mail» внутри рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="30ed7-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="30ed7-104">Этот запрос необходим, чтобы участник отслеживания мог подписываться на объекты записей состояния действия.</span><span class="sxs-lookup"><span data-stu-id="30ed7-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="30ed7-105">Состояния, доступные для подписки, указаны в ActivtyStates.</span><span class="sxs-lookup"><span data-stu-id="30ed7-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="30ed7-106">Дополнительные сведения о запросах профиля отслеживания см. в разделе [профили отслеживания](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="30ed7-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="30ed7-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30ed7-107">\<system.serviceModel></span></span>  
<span data-ttu-id="30ed7-108">\<Отслеживание ></span><span class="sxs-lookup"><span data-stu-id="30ed7-108">\<tracking></span></span>  
<span data-ttu-id="30ed7-109">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="30ed7-109">\<trackingProfile></span></span>  
<span data-ttu-id="30ed7-110">\<рабочий процесс ></span><span class="sxs-lookup"><span data-stu-id="30ed7-110">\<workflow></span></span>  
<span data-ttu-id="30ed7-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="30ed7-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ed7-112">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30ed7-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30ed7-113">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="30ed7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="30ed7-114">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="30ed7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30ed7-115">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="30ed7-115">Attributes</span></span>  
 <span data-ttu-id="30ed7-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="30ed7-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30ed7-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="30ed7-117">Child Elements</span></span>  
  
|<span data-ttu-id="30ed7-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="30ed7-118">Element</span></span>|<span data-ttu-id="30ed7-119">Описание</span><span class="sxs-lookup"><span data-stu-id="30ed7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30ed7-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="30ed7-120">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="30ed7-121">Запрос, который используется для отслеживания обработки ошибок, возникающих в рамках действия.</span><span class="sxs-lookup"><span data-stu-id="30ed7-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="30ed7-122">Это событие возникает каждый раз, когда FaultHandler обрабатывает ошибку.</span><span class="sxs-lookup"><span data-stu-id="30ed7-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30ed7-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="30ed7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="30ed7-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="30ed7-124">Element</span></span>|<span data-ttu-id="30ed7-125">Описание</span><span class="sxs-lookup"><span data-stu-id="30ed7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30ed7-126">\<рабочий процесс ></span><span class="sxs-lookup"><span data-stu-id="30ed7-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="30ed7-127">Элемент конфигурации, содержащий все запросы для конкретного рабочего процесса, обозначенного **activityDefinitionId** свойство.</span><span class="sxs-lookup"><span data-stu-id="30ed7-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30ed7-128">См. также</span><span class="sxs-lookup"><span data-stu-id="30ed7-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="30ed7-129">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="30ed7-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="30ed7-130">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="30ed7-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
