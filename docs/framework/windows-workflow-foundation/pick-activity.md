---
title: Действие Pick
description: В Workflow Foundation действие выбор упрощает моделирование набора триггеров событий, за которыми следуют соответствующие обработчики.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: eb59dc20919ed2d30a48f920ad154d4b0d99c41f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421466"
---
# <a name="pick-activity"></a><span data-ttu-id="c04bd-103">Действие Pick</span><span class="sxs-lookup"><span data-stu-id="c04bd-103">Pick Activity</span></span>
<span data-ttu-id="c04bd-104">Действие <xref:System.Activities.Statements.Pick> позволяет упростить моделирование набора триггеров событий, а затем соответствующих обработчиков.</span><span class="sxs-lookup"><span data-stu-id="c04bd-104">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="c04bd-105">Действие содержит <xref:System.Activities.Statements.Pick> коллекцию действий <xref:System.Activities.Statements.PickBranch>, в которой все элементы <xref:System.Activities.Statements.PickBranch> являются парами, состоящими из действия <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действия <xref:System.Activities.Statements.PickBranch.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-105">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="c04bd-106">Во время выполнения триггеры для всех ветвей выполняются параллельно.</span><span class="sxs-lookup"><span data-stu-id="c04bd-106">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="c04bd-107">Когда срабатывает один триггер, выполняется соответствующее действие, а остальные триггеры отменяются.</span><span class="sxs-lookup"><span data-stu-id="c04bd-107">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="c04bd-108">Поведение [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> действия аналогично действию .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> .</span><span class="sxs-lookup"><span data-stu-id="c04bd-108">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="c04bd-109">На следующем снимке экрана из примера пакета SDK [Использование действия Pick](./samples/using-the-pick-activity.md) показано действие Pick с двумя ветвями.</span><span class="sxs-lookup"><span data-stu-id="c04bd-109">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="c04bd-110">В одной ветви есть триггер с именем **Read input** — настраиваемое действие, считывающее входные данные из командной строки.</span><span class="sxs-lookup"><span data-stu-id="c04bd-110">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="c04bd-111">Во второй ветви имеется триггер действия <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-111">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="c04bd-112">Если действие **Read input** получает данные до <xref:System.Activities.Statements.Delay> завершения действия, <xref:System.Activities.Statements.Delay> задержка будет отменена и приветствие будет записано на консоль.</span><span class="sxs-lookup"><span data-stu-id="c04bd-112">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="c04bd-113">В противном случае, если действие **Read input** не получает данные в отведенное время, это действие отменяется, и в консоль выводится сообщение об окончании времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="c04bd-113">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="c04bd-114">Это стандартный прием для добавления периода времени ожидания к любому действию.</span><span class="sxs-lookup"><span data-stu-id="c04bd-114">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Действие Pick](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="c04bd-116">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="c04bd-116">Best practices</span></span>  
 <span data-ttu-id="c04bd-117">При использовании действия Pick выполняемой ветвью действия становится ветвь, триггеры которой первыми завершат выполнение.</span><span class="sxs-lookup"><span data-stu-id="c04bd-117">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="c04bd-118">Теоретически, все триггеры выполняются параллельно, и один триггер может выполнить большую часть свой логики до того, как будет отменен из-за завершения работы другого.</span><span class="sxs-lookup"><span data-stu-id="c04bd-118">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="c04bd-119">С учетом этого необходимо соблюдать следующие инструкции при работе с действием Pick: работать с триггером, как если бы он представлял одно событие, и помещать в него минимально возможный объем логики.</span><span class="sxs-lookup"><span data-stu-id="c04bd-119">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="c04bd-120">В идеале триггер должен содержать объем логики, достаточный лишь для получения события, и обработка этого события должна выполняться в действии этой ветви.</span><span class="sxs-lookup"><span data-stu-id="c04bd-120">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="c04bd-121">Этот метод минимизирует объем перекрытия при выполнении триггеров.</span><span class="sxs-lookup"><span data-stu-id="c04bd-121">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="c04bd-122">Для примера можно представить <xref:System.Activities.Statements.Pick> с двумя триггерами, где каждый триггер содержит действие <xref:System.ServiceModel.Activities.Receive> с дополнительной логикой.</span><span class="sxs-lookup"><span data-stu-id="c04bd-122">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="c04bd-123">Если дополнительная логика представляет точку бездействия, то существует вероятность успешного завершения обоих действий <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-123">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="c04bd-124">Один триггер будет полностью выполнен, а второй будет выполнен частично.</span><span class="sxs-lookup"><span data-stu-id="c04bd-124">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="c04bd-125">В определенных ситуациях принятие сообщения и последующее частичное выполнение его обработки недопустимо.</span><span class="sxs-lookup"><span data-stu-id="c04bd-125">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="c04bd-126">Следовательно, что касается применения таких встроенных действий обмена сообщениями WF, как <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply>, то <xref:System.ServiceModel.Activities.Receive> часто используется в триггерах, а <xref:System.ServiceModel.Activities.SendReply> и другая логика должны быть при любой возможности помещены в действие.</span><span class="sxs-lookup"><span data-stu-id="c04bd-126">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="c04bd-127">Использование действия Pick в конструкторе</span><span class="sxs-lookup"><span data-stu-id="c04bd-127">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="c04bd-128">Чтобы использовать Pick в конструкторе, найдите **Pick** и **PickBranch** на панели элементов.</span><span class="sxs-lookup"><span data-stu-id="c04bd-128">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="c04bd-129">Перетащите **Pick** на холст.</span><span class="sxs-lookup"><span data-stu-id="c04bd-129">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="c04bd-130">По умолчанию новое действие **Pick** в конструкторе будет содержать две ветви.</span><span class="sxs-lookup"><span data-stu-id="c04bd-130">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="c04bd-131">Чтобы добавить дополнительные ветви, перетащите действие **PickBranch** в область рядом с существующими ветвями.</span><span class="sxs-lookup"><span data-stu-id="c04bd-131">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="c04bd-132">Действия можно перетаскивать в действие **Pick** в области **Trigger** или область **Action** любого действия **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="c04bd-132">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="c04bd-133">Использование действия Pick в коде</span><span class="sxs-lookup"><span data-stu-id="c04bd-133">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="c04bd-134">Действие <xref:System.Activities.Statements.Pick> используется при заполнении его коллекции <xref:System.Activities.Statements.Pick.Branches%2A> действиями <xref:System.Activities.Statements.PickBranch>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-134">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="c04bd-135">Все действия <xref:System.Activities.Statements.PickBranch> имеют свойство <xref:System.Activities.Statements.PickBranch.Trigger%2A> типа <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-135">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="c04bd-136">После завершения выполнения указанного действия выполняется <xref:System.Activities.Statements.PickBranch.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="c04bd-136">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="c04bd-137">В следующем примере кода показано использование действия <xref:System.Activities.Statements.Pick> для реализации времени ожидания для действия, которое считывает строку с консоли.</span><span class="sxs-lookup"><span data-stu-id="c04bd-137">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine
                   {
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +
                           name.Get(ctx))
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
