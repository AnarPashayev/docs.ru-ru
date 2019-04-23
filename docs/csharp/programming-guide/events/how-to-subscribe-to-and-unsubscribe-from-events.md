---
title: Как выполнить Руководство по программированию на C#. Подписка и отмена подписки на события
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: d1442e02d651cd283e5ff63d28f3cfe80e99cc7d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306603"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="b5621-102">Как выполнить Руководство по программированию на C#. Подписка и отмена подписки на события</span><span class="sxs-lookup"><span data-stu-id="b5621-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="b5621-103">Необходимость подписки на событие, опубликованное другим классом, может возникнуть, когда требуется написать пользовательский код, вызываемый при инициировании такого события.</span><span class="sxs-lookup"><span data-stu-id="b5621-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="b5621-104">Например, можно подписаться на событие кнопки `click`, чтобы приложение выполняло некоторое действие при нажатии пользователем кнопки.</span><span class="sxs-lookup"><span data-stu-id="b5621-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="b5621-105">Подписка на события в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b5621-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="b5621-106">Если окно **Свойства** закрыто, в представлении **Конструктор** щелкните правой кнопкой мыши форму или элемент управления, для которого требуется создать обработчик событий, и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="b5621-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="b5621-107">Вверху окна **Свойства** щелкните значок **События**.</span><span class="sxs-lookup"><span data-stu-id="b5621-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="b5621-108">Дважды щелкните событие, которое требуется создать, например событие `Load`.</span><span class="sxs-lookup"><span data-stu-id="b5621-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="b5621-109">Visual C# создаст пустой метод обработчика событий и добавит его в код.</span><span class="sxs-lookup"><span data-stu-id="b5621-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="b5621-110">Код можно также добавить вручную в представлении **Код**.</span><span class="sxs-lookup"><span data-stu-id="b5621-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="b5621-111">Например, приведенные ниже строки кода объявляют метод обработчика событий, который будет выполнен при вызове классом `Form` события `Load`.</span><span class="sxs-lookup"><span data-stu-id="b5621-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="b5621-112">Строка кода, требуемая для подписки на событие, также создается автоматически в методе `InitializeComponent` в файле Form1.Designer.cs проекта.</span><span class="sxs-lookup"><span data-stu-id="b5621-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="b5621-113">Она имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="b5621-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="b5621-114">Подписка на события программными средствами</span><span class="sxs-lookup"><span data-stu-id="b5621-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="b5621-115">Определите метод обработчика событий, сигнатура которого соответствует сигнатуре делегата для события.</span><span class="sxs-lookup"><span data-stu-id="b5621-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="b5621-116">Например, если событие основано на типе делегата <xref:System.EventHandler>, то следующий код представляет заглушку метода:</span><span class="sxs-lookup"><span data-stu-id="b5621-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="b5621-117">Чтобы присоединить обработчик событий к событию, используйте оператор присваивания сложения (`+=`).</span><span class="sxs-lookup"><span data-stu-id="b5621-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="b5621-118">В приведенном ниже примере предположим, что объект с именем `publisher` имеет событие с именем `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="b5621-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="b5621-119">Обратите внимание на то, что классу подписчика требуется ссылка на класс издателя, чтобы подписаться на его события.</span><span class="sxs-lookup"><span data-stu-id="b5621-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="b5621-120">Обратите внимание, что приведенный выше синтаксис появился только в C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="b5621-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="b5621-121">Он в точности соответствует синтаксису C# 1.0, в котором с помощью ключевого слова `new` должен быть явно создан инкапсулирующий делегат.</span><span class="sxs-lookup"><span data-stu-id="b5621-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="b5621-122">Для добавления обработчика событий можно также использовать лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="b5621-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="b5621-123">Дополнительные сведения см. в разделе [Как Руководство по программированию на C#. Использование лямбда-выражений вне LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b5621-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="b5621-124">Подписка на события с помощью анонимного метода</span><span class="sxs-lookup"><span data-stu-id="b5621-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="b5621-125">Если не нужно будет позже отменять подписку на событие, можно использовать оператор присваивания сложения (`+=`) для прикрепления к событию анонимного метода.</span><span class="sxs-lookup"><span data-stu-id="b5621-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="b5621-126">В следующем примере предположим, что объект с именем `publisher` имеет событие с именем `RaiseCustomEvent` и что класс `CustomEventArgs` также был определен и содержит некие относящиеся к событию сведения.</span><span class="sxs-lookup"><span data-stu-id="b5621-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="b5621-127">Обратите внимание на то, что классу подписчика требуется ссылка на `publisher`, чтобы подписаться на его события.</span><span class="sxs-lookup"><span data-stu-id="b5621-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="b5621-128">Важно отметить, что отменить подписку на событие не так просто, если для подписки на него использовалась анонимная функция.</span><span class="sxs-lookup"><span data-stu-id="b5621-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="b5621-129">Чтобы отменить подписку в этом случае, необходимо вернуться к коду, в котором была выполнена подписка на событие, сохранить анонимный метод в переменной делегата, а затем добавить делегат к событию.</span><span class="sxs-lookup"><span data-stu-id="b5621-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="b5621-130">Как правило, мы рекомендуем не использовать анонимных функций для подписки на события, если предполагается, что в будущем будет нужно отменять подписку на событие.</span><span class="sxs-lookup"><span data-stu-id="b5621-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="b5621-131">Дополнительные сведения об анонимных функциях см. в разделе [Анонимные функции](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b5621-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="b5621-132">Отмена подписки</span><span class="sxs-lookup"><span data-stu-id="b5621-132">Unsubscribing</span></span>  
 <span data-ttu-id="b5621-133">Чтобы предотвратить вызов обработчика событий при инициировании события, подписку на событие необходимо отменить.</span><span class="sxs-lookup"><span data-stu-id="b5621-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="b5621-134">Во избежание утечки ресурсов отменять подписку на события следует до удаления объекта подписчика.</span><span class="sxs-lookup"><span data-stu-id="b5621-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="b5621-135">До тех пор пока подписка на событие не отменена, делегат многоадресной рассылки, лежащий в основе события в публикующем объекте, будет ссылаться на делегат, инкапсулирующий обработчик событий подписчика.</span><span class="sxs-lookup"><span data-stu-id="b5621-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="b5621-136">Если ссылка присутствует в публикующем объекте, объект подписчика не будет удален при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="b5621-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="b5621-137">Отмена подписки на событие</span><span class="sxs-lookup"><span data-stu-id="b5621-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="b5621-138">Чтобы отменить подписку на событие, воспользуйтесь оператором присваивания вычитания (`-=`).</span><span class="sxs-lookup"><span data-stu-id="b5621-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="b5621-139">Если подписка на событие отменена для всех подписчиков, экземпляр события в классе издателя получает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b5621-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5621-140">См. также</span><span class="sxs-lookup"><span data-stu-id="b5621-140">See also</span></span>

- [<span data-ttu-id="b5621-141">События</span><span class="sxs-lookup"><span data-stu-id="b5621-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="b5621-142">event</span><span class="sxs-lookup"><span data-stu-id="b5621-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)
- [<span data-ttu-id="b5621-143">Практическое руководство. Публикация событий в соответствии с руководствами по .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5621-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="b5621-144">Оператор -= (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="b5621-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="b5621-145">Оператор +=</span><span class="sxs-lookup"><span data-stu-id="b5621-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)
