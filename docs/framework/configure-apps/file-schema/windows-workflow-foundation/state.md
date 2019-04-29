---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796166"
---
# <a name="state"></a><span data-ttu-id="1f798-101">\<Состояние ></span><span class="sxs-lookup"><span data-stu-id="1f798-101">\<state></span></span>
<span data-ttu-id="1f798-102">Представляет коллекцию состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1f798-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1f798-103">Дополнительные сведения о запросах профиля отслеживания см. в разделе [профили отслеживания](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1f798-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1f798-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1f798-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1f798-105">\<Отслеживание ></span><span class="sxs-lookup"><span data-stu-id="1f798-105">\<tracking></span></span>  
<span data-ttu-id="1f798-106">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1f798-106">\<trackingProfile></span></span>  
<span data-ttu-id="1f798-107">\<рабочий процесс ></span><span class="sxs-lookup"><span data-stu-id="1f798-107">\<workflow></span></span>  
<span data-ttu-id="1f798-108">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="1f798-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="1f798-109">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="1f798-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="1f798-110">\<состояния ></span><span class="sxs-lookup"><span data-stu-id="1f798-110">\<states></span></span>  
<span data-ttu-id="1f798-111">\<Состояние ></span><span class="sxs-lookup"><span data-stu-id="1f798-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f798-112">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f798-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f798-113">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1f798-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1f798-114">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1f798-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f798-115">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f798-115">Attributes</span></span>  
  
|<span data-ttu-id="1f798-116">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1f798-116">Attribute</span></span>|<span data-ttu-id="1f798-117">Описание</span><span class="sxs-lookup"><span data-stu-id="1f798-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f798-118">имя</span><span class="sxs-lookup"><span data-stu-id="1f798-118">name</span></span>|<span data-ttu-id="1f798-119">Строка, указывающая состояние подписки отслеживаемого экземпляра рабочего потока в момент создания записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1f798-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f798-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1f798-120">Child Elements</span></span>  
 <span data-ttu-id="1f798-121">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1f798-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f798-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1f798-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1f798-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f798-123">Element</span></span>|<span data-ttu-id="1f798-124">Описание</span><span class="sxs-lookup"><span data-stu-id="1f798-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f798-125">\<состояния ></span><span class="sxs-lookup"><span data-stu-id="1f798-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1f798-126">Коллекция состояний, на которые установлена подписка, из отслеживаемого экземпляра рабочего процесса в момент создания записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="1f798-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f798-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f798-127">Remarks</span></span>  
 <span data-ttu-id="1f798-128">Возвращаемые записи фильтруются по состояниям в этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="1f798-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="1f798-129">Допустимые значения состояния описаны в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="1f798-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1f798-130">Регион</span><span class="sxs-lookup"><span data-stu-id="1f798-130">State</span></span>|<span data-ttu-id="1f798-131">Описание</span><span class="sxs-lookup"><span data-stu-id="1f798-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f798-132">Прерывание</span><span class="sxs-lookup"><span data-stu-id="1f798-132">Aborted</span></span>|<span data-ttu-id="1f798-133">Экземпляр рабочего процесса прерван.</span><span class="sxs-lookup"><span data-stu-id="1f798-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1f798-134">Завершено</span><span class="sxs-lookup"><span data-stu-id="1f798-134">Completed</span></span>|<span data-ttu-id="1f798-135">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="1f798-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1f798-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="1f798-136">Deleted</span></span>|<span data-ttu-id="1f798-137">Экземпляр рабочего процесса удален.</span><span class="sxs-lookup"><span data-stu-id="1f798-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1f798-138">Бездействие</span><span class="sxs-lookup"><span data-stu-id="1f798-138">Idle</span></span>|<span data-ttu-id="1f798-139">Экземпляр рабочего процесса простаивает.</span><span class="sxs-lookup"><span data-stu-id="1f798-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1f798-140">Сохранение</span><span class="sxs-lookup"><span data-stu-id="1f798-140">Persisted</span></span>|<span data-ttu-id="1f798-141">Экземпляр рабочего процесса сохранен.</span><span class="sxs-lookup"><span data-stu-id="1f798-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1f798-142">Возобновление</span><span class="sxs-lookup"><span data-stu-id="1f798-142">Resumed</span></span>|<span data-ttu-id="1f798-143">Экземпляр рабочего процесса возобновлен.</span><span class="sxs-lookup"><span data-stu-id="1f798-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1f798-144">Запуск</span><span class="sxs-lookup"><span data-stu-id="1f798-144">Started</span></span>|<span data-ttu-id="1f798-145">Экземпляр рабочего процесса запущен.</span><span class="sxs-lookup"><span data-stu-id="1f798-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1f798-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1f798-146">UnhandledException</span></span>|<span data-ttu-id="1f798-147">Экземпляр рабочего процесса встретил необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="1f798-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1f798-148">Выгружен</span><span class="sxs-lookup"><span data-stu-id="1f798-148">Unloaded</span></span>|<span data-ttu-id="1f798-149">Экземпляр рабочего процесса выгружен.</span><span class="sxs-lookup"><span data-stu-id="1f798-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1f798-150">Отменено</span><span class="sxs-lookup"><span data-stu-id="1f798-150">Canceled</span></span>|<span data-ttu-id="1f798-151">Выполнение экземпляра рабочего процесса отменено.</span><span class="sxs-lookup"><span data-stu-id="1f798-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1f798-152">Приостановлена</span><span class="sxs-lookup"><span data-stu-id="1f798-152">Suspended</span></span>|<span data-ttu-id="1f798-153">Выполнение экземпляра рабочего процесса приостановлено.</span><span class="sxs-lookup"><span data-stu-id="1f798-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1f798-154">Завершение</span><span class="sxs-lookup"><span data-stu-id="1f798-154">Terminated</span></span>|<span data-ttu-id="1f798-155">Выполнение экземпляра рабочего процесса завершено.</span><span class="sxs-lookup"><span data-stu-id="1f798-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1f798-156">Возобновлено</span><span class="sxs-lookup"><span data-stu-id="1f798-156">Unsuspended</span></span>|<span data-ttu-id="1f798-157">Выполнение экземпляра рабочего процесса возобновлено.</span><span class="sxs-lookup"><span data-stu-id="1f798-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f798-158">Пример</span><span class="sxs-lookup"><span data-stu-id="1f798-158">Example</span></span>  
 <span data-ttu-id="1f798-159">При использовании следующей конфигурации устанавливается подписка на записи отслеживания рабочего процесса на уровне экземпляра для состояния экземпляра `Started` при помощи данного запроса.</span><span class="sxs-lookup"><span data-stu-id="1f798-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f798-160">См. также</span><span class="sxs-lookup"><span data-stu-id="1f798-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1f798-161">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="1f798-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f798-162">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="1f798-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
