---
title: Шаблоны слабых событий
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991791"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="8a0bf-102">Шаблоны слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-102">Weak Event Patterns</span></span>
<span data-ttu-id="8a0bf-103">В приложениях возможно, что обработчики, присоединенные к источникам событий, не будут уничтожены в координации с объектом прослушивателя, который присоединил обработчик к источнику.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="8a0bf-104">Такая ситуация может привести к утечке памяти.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="8a0bf-105">представляет шаблон проектирования, который можно использовать для решения этой проблемы, предоставляя выделенный класс Manager для конкретных событий и реализуя интерфейс для прослушивателей этого события.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="8a0bf-106">Этот шаблон разработки известен как *шаблон слабых событий*.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="8a0bf-107">Зачем реализовывать шаблон слабых событий?</span><span class="sxs-lookup"><span data-stu-id="8a0bf-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="8a0bf-108">Прослушивание событий может привести к утечке памяти.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="8a0bf-109">Типичным приемом для прослушивания события является использование синтаксиса, зависящего от языка, который прикрепляет обработчик к событию в источнике.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="8a0bf-110">Например, в C#используется следующий синтаксис: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="8a0bf-111">Этот метод создает строгую ссылку из источника событий в прослушиватель событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="8a0bf-112">Обычно присоединение обработчика событий для прослушивателя приводит к тому, что прослушиватель имеет время существования объекта, на которое влияет время существования объекта источника (если только обработчик событий не удаляется явным образом).</span><span class="sxs-lookup"><span data-stu-id="8a0bf-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="8a0bf-113">Но в некоторых случаях может потребоваться, чтобы время существования объекта прослушивателя управлялось другими факторами, например, если он принадлежит визуальному дереву приложения, а не времени существования источника.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="8a0bf-114">Каждый раз, когда время существования исходного объекта выходит за пределы времени существования объекта прослушивателя, шаблон обычного события приводит к утечке памяти: прослушиватель поддерживается дольше, чем планировалось.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="8a0bf-115">Шаблон слабых событий предназначен для решения этой проблемы утечки памяти.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="8a0bf-116">Шаблон слабых событий можно использовать всякий раз, когда прослушивателю необходимо зарегистрироваться для события, но прослушиватель не знает, когда следует отменять регистрацию.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="8a0bf-117">Шаблон слабых событий также можно использовать всякий раз, когда время существования объекта источника превышает полезное время существования объекта прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="8a0bf-118">(В этом случае *полезно* определить.) Шаблон слабых событий позволяет прослушивателю регистрироваться и принимать события, не влияя на характеристики времени существования объекта прослушивателя любым способом.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="8a0bf-119">Фактически неявная ссылка из источника не определяет, подходит ли прослушиватель для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="8a0bf-120">Ссылка является слабой ссылкой, то есть наименованием шаблона слабых событий и связанных с ним API.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="8a0bf-121">Прослушиватель может быть собран или удален сборщиком мусора, и источник можно продолжить без удержания ссылок на Несобираемые обработчики на уже уничтоженный объект.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="8a0bf-122">Кто должен реализовывать шаблон слабых событий?</span><span class="sxs-lookup"><span data-stu-id="8a0bf-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="8a0bf-123">Реализация шаблона слабых событий является наиболее интересной в основном для авторов элементов управления.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="8a0bf-124">Как автор элемента управления, вы в основном отвечаете за поведение и включение элемента управления и влияние его на приложения, в которых он вставлен.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="8a0bf-125">Это включает в себя поведение времени существования управляющего объекта, в частности, обработку описанной проблемы утечки памяти.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="8a0bf-126">Некоторые сценарии изначально предоставляются для применения шаблона слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="8a0bf-127">Одним из таких сценариев является привязка данных.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-127">One such scenario is data binding.</span></span> <span data-ttu-id="8a0bf-128">В привязке данных обычно исходный объект полностью независим от объекта listener, который является целевым объектом привязки.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="8a0bf-129">Многие аспекты [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] привязки данных уже имеют шаблон слабых событий, применяемый в способе реализации событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="8a0bf-130">Реализация шаблона слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="8a0bf-131">Существует три способа реализации шаблона слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="8a0bf-132">В следующей таблице перечислены три подхода и приведены некоторые рекомендации по их использованию.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="8a0bf-133">Подход</span><span class="sxs-lookup"><span data-stu-id="8a0bf-133">Approach</span></span>|<span data-ttu-id="8a0bf-134">Когда следует реализовывать</span><span class="sxs-lookup"><span data-stu-id="8a0bf-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="8a0bf-135">Использование существующего класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="8a0bf-136">Если событие, на которое нужно подписываться, имеет <xref:System.Windows.WeakEventManager>соответствующее значение, используйте существующий диспетчер слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="8a0bf-137">Список слабых диспетчеров событий, входящих в состав WPF, см. в разделе Иерархия наследования в <xref:System.Windows.WeakEventManager> классе.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="8a0bf-138">Поскольку входящие диспетчеры событий ограничены, вам, вероятно, потребуется выбрать один из других подходов.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="8a0bf-139">Использование универсального класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="8a0bf-140">Использовать универсальный <xref:System.Windows.WeakEventManager%602> , если существующий <xref:System.Windows.WeakEventManager> объект недоступен, вы хотите легко реализовать и не беспокоиться об эффективности.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="8a0bf-141">Универсальный <xref:System.Windows.WeakEventManager%602> объект менее эффективен, чем существующий или пользовательский диспетчер слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="8a0bf-142">Например, универсальный класс делает больше отражения для обнаружения события в заданном имени события.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="8a0bf-143">Кроме того, код для регистрации события с помощью универсального <xref:System.Windows.WeakEventManager%602> типа является более подробным, чем использование существующего или пользовательского. <xref:System.Windows.WeakEventManager></span><span class="sxs-lookup"><span data-stu-id="8a0bf-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="8a0bf-144">Создание пользовательского класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="8a0bf-145">Создание настраиваемого <xref:System.Windows.WeakEventManager> объекта, если <xref:System.Windows.WeakEventManager> существующий объект недоступен и требуется лучшая эффективность.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="8a0bf-146">Использование настраиваемого <xref:System.Windows.WeakEventManager> объекта для подписки на событие будет более эффективным, однако стоимость написания кода в начале не взимается.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="8a0bf-147">Использование стороннего диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="8a0bf-148">NuGet имеет [несколько диспетчеров слабых событий](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) , а многие платформы WPF также поддерживают шаблон (например, см. [документацию по Prism по слабо связанной подписке на события](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="8a0bf-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="8a0bf-149">В следующих разделах описывается реализация шаблона слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="8a0bf-150">В рамках этого обсуждения событие, для которого подписывается, имеет следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="8a0bf-151">Имя события — `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="8a0bf-152">Событие вызывается `EventSource` классом.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="8a0bf-153">Обработчик событий имеет тип: `SomeEventEventHandler` (или `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="8a0bf-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="8a0bf-154">Событие передает параметр типа `SomeEventEventArgs` в обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="8a0bf-155">Использование существующего класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="8a0bf-156">Найдите существующий диспетчер слабых событий.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="8a0bf-157">Список слабых диспетчеров событий, входящих в состав WPF, см. в разделе Иерархия наследования в <xref:System.Windows.WeakEventManager> классе.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="8a0bf-158">Используйте новый диспетчер слабых событий вместо обычного подключения к событию.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="8a0bf-159">Например, если в коде для подписки на событие используется следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="8a0bf-160">Измените его на следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-160">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="8a0bf-161">Аналогично, если в коде используется следующий шаблон для отмены подписки на событие:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="8a0bf-162">Измените его на следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-162">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="8a0bf-163">Использование универсального класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="8a0bf-164">Используйте универсальный <xref:System.Windows.WeakEventManager%602> класс вместо обычной подписки на событие.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="8a0bf-165">При использовании <xref:System.Windows.WeakEventManager%602> для регистрации прослушивателей событий необходимо указать источник события и <xref:System.EventArgs> тип в качестве параметров типа для класса и вызвать <xref:System.Windows.WeakEventManager%602.AddHandler%2A> , как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="8a0bf-166">Создание пользовательского класса диспетчера слабых событий</span><span class="sxs-lookup"><span data-stu-id="8a0bf-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="8a0bf-167">Скопируйте следующий шаблон класса в проект.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="8a0bf-168">Этот класс наследуется от <xref:System.Windows.WeakEventManager> класса.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="8a0bf-169">`SomeEventWeakEventManager` Замените имя своим именем.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="8a0bf-170">Замените три имени, описанные выше, соответствующими именами для события.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="8a0bf-171">(`SomeEvent`, `EventSource`и )`SomeEventEventArgs`</span><span class="sxs-lookup"><span data-stu-id="8a0bf-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="8a0bf-172">Задайте для свойства Visibility (открытый/внутренний/частный) класс диспетчера событий ту же видимость, что и управляемое им событие.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="8a0bf-173">Используйте новый диспетчер слабых событий вместо обычного подключения к событию.</span><span class="sxs-lookup"><span data-stu-id="8a0bf-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="8a0bf-174">Например, если в коде для подписки на событие используется следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="8a0bf-175">Измените его на следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-175">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="8a0bf-176">Аналогично, если в коде используется следующий шаблон для отмены подписки на событие:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="8a0bf-177">Измените его на следующий шаблон:</span><span class="sxs-lookup"><span data-stu-id="8a0bf-177">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a0bf-178">См. также</span><span class="sxs-lookup"><span data-stu-id="8a0bf-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="8a0bf-179">Общие сведения о перенаправленных событиях</span><span class="sxs-lookup"><span data-stu-id="8a0bf-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="8a0bf-180">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="8a0bf-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
