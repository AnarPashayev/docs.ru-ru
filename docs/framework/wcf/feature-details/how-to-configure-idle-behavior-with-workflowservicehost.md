---
title: Практическое руководство. Как настроить неактивное поведение с помощью WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: a676f03b4e6f9dd210b843a6f3bf00c735889500
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330159"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="c8137-102">Практическое руководство. Как настроить неактивное поведение с помощью WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c8137-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="c8137-103">Рабочие процессы переходят в режим бездействия, когда обнаруживают закладку, выполнение которой должно быть возобновлено по внешнему сигналу, например когда экземпляр рабочего процесса ожидает доставки сообщения с помощью действия <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="c8137-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> <span data-ttu-id="c8137-104">Это поведение, которое позволяет указать время между переходом экземпляра службы в состояние бездействия и сохранением или выгрузкой экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c8137-104">is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="c8137-105">Содержит два свойства, которые позволяют задавать значения для этих периодов времени.</span><span class="sxs-lookup"><span data-stu-id="c8137-105">It contains two properties that enable you to set these time spans.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> <span data-ttu-id="c8137-106">Указывает интервал времени между переходом экземпляра службы рабочего процесса в состояние бездействия и сохранением экземпляра службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="c8137-106">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <span data-ttu-id="c8137-107">Указывает период времени между когда экземпляру службы рабочего процесса переходит в состояние бездействия и при выгрузке экземпляра службы рабочего процесса, где выгрузка означает сохранение экземпляра в хранилище экземпляров и удаление его из памяти.</span><span class="sxs-lookup"><span data-stu-id="c8137-107">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="c8137-108">В этом разделе описана настройка <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c8137-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="c8137-109">Настройка WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="c8137-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="c8137-110">Добавьте <`workflowIdle`> элемента <`behavior`> элемента <`serviceBehaviors`> элемента, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c8137-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="c8137-111">Атрибут `timeToUnload` определяет период времени между переходом экземпляра службы рабочего процесса в состояние бездействия и выгрузкой службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="c8137-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="c8137-112">Атрибут `timeToPersist` определяет период времени между переходом экземпляра службы рабочего процесса в состояние бездействия и сохранением экземпляра службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="c8137-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="c8137-113">Значение `timeToUnload` по умолчанию составляет 1 минуту.</span><span class="sxs-lookup"><span data-stu-id="c8137-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="c8137-114">По умолчанию для объекта `timeToPersist` установлено значение <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="c8137-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="c8137-115">Если ожидающие экземпляры нужно оставить в памяти, но сохранить для надежности, задайте значения так, чтобы выполнялось неравенство `timeToPersist` < `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="c8137-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="c8137-116">Если требуется, чтобы ожидающие экземпляры не выгружались, задайте параметру `timeToUnload` значение <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="c8137-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="c8137-117">Дополнительные сведения о <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, см. в разделе [расширяемость узла службы рабочего процесса](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="c8137-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8137-118">В предыдущем образце конфигурации используется упрощенная конфигурация.</span><span class="sxs-lookup"><span data-stu-id="c8137-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="c8137-119">Дополнительные сведения см. в разделе [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c8137-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="c8137-120">Изменение поведения во время ожидания в коде</span><span class="sxs-lookup"><span data-stu-id="c8137-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="c8137-121">В следующем примере программным способом изменяется время ожидания перед сохранением и выгрузкой.</span><span class="sxs-lookup"><span data-stu-id="c8137-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c8137-122">См. также</span><span class="sxs-lookup"><span data-stu-id="c8137-122">See also</span></span>

- [<span data-ttu-id="c8137-123">Расширяемость узла службы рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="c8137-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="c8137-124">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="c8137-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="c8137-125">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="c8137-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
