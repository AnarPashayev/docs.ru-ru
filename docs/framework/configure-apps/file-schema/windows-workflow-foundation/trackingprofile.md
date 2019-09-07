---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 3120d6f5d1bb5a5cf452567e96766231534f3f41
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398593"
---
# <a name="trackingprofile"></a><span data-ttu-id="b4069-101">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b4069-101">\<trackingProfile></span></span>
<span data-ttu-id="b4069-102">Представляет раздел конфигурации для создания подписки на записи отслеживания рабочих процессов в участнике отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b4069-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="b4069-103">Профиль отслеживания содержит запросы отслеживания, позволяющие участнику отслеживания подписываться на события рабочего процесса, формируемые во время выполнения при изменении состояния экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b4069-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b4069-104">Запросы, заданные в разделе профиля отслеживания, определяют виды событий, возвращаемых подпиской.</span><span class="sxs-lookup"><span data-stu-id="b4069-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="b4069-105">Дополнительные сведения об отслеживании рабочих процессов и его конфигурации см. в разделе [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Track Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b4069-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b4069-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4069-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4069-107">&nbsp;&nbsp;[ **\<системой. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b4069-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b4069-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Отслеживание >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="b4069-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="b4069-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="b4069-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4069-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4069-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4069-111">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b4069-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b4069-112">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b4069-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4069-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b4069-113">Attributes</span></span>  
  
|<span data-ttu-id="b4069-114">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b4069-114">Attribute</span></span>|<span data-ttu-id="b4069-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b4069-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4069-116">имя</span><span class="sxs-lookup"><span data-stu-id="b4069-116">name</span></span>|<span data-ttu-id="b4069-117">Строка, задающая имя профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b4069-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4069-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b4069-118">Child Elements</span></span>  
  
|<span data-ttu-id="b4069-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4069-119">Element</span></span>|<span data-ttu-id="b4069-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b4069-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4069-121">\<Участники ></span><span class="sxs-lookup"><span data-stu-id="b4069-121">\<participants></span></span>](participants.md)|<span data-ttu-id="b4069-122">Элемент конфигурации, содержащий все запросы для определенного рабочего процесса, обозначенного свойством <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4069-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4069-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b4069-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b4069-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4069-124">Element</span></span>|<span data-ttu-id="b4069-125">Описание</span><span class="sxs-lookup"><span data-stu-id="b4069-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4069-126">\<Отслеживание ></span><span class="sxs-lookup"><span data-stu-id="b4069-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="b4069-127">Представляет раздел конфигурации для определения настроек отслеживания для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b4069-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4069-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="b4069-128">Remarks</span></span>  
 <span data-ttu-id="b4069-129">Профиль отслеживания содержит запросы отслеживания, которые позволяют участнику подписываться на события рабочего потока, создаваемые при изменении состояния экземпляра рабочего процесса в ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="b4069-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="b4069-130">Исходя из потребностей, можно написать профиль с низкой детализацией, который будет подписан на небольшой набор изменений состояния высокого уровня в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="b4069-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b4069-131">И наоборот, можно создать очень детальный профиль, результирующие события которого будут достаточно подробными для последующего воспроизведения всего потока выполнения.</span><span class="sxs-lookup"><span data-stu-id="b4069-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="b4069-132">Профили отслеживания структурированы в форме объявляющих подписок на записи отслеживания, которые позволяют выполнять запросы к среде выполнения рабочего процесса в отношении определенных записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b4069-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="b4069-133">Существует несколько типов запросов, которые позволяют подписываться на разные классы <xref:System.Activities.Tracking.TrackingRecord> объектов.</span><span class="sxs-lookup"><span data-stu-id="b4069-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="b4069-134">Полный список запросов см. в разделе [ \<Участники >](participants.md) и [Профили отслеживания](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b4069-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="b4069-135">В следующем примере показан профиль отслеживания в файле конфигурации, который позволяет участнику отслеживания подписываться `Started` на события рабочего процесса и. `Completed`</span><span class="sxs-lookup"><span data-stu-id="b4069-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4069-136">См. также</span><span class="sxs-lookup"><span data-stu-id="b4069-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="b4069-137">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="b4069-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b4069-138">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="b4069-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
