---
title: Практическое руководство. Обработка нескольких событий с помощью их свойств
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9f911f3a2783ec538ef628e10d5c1a4f9b06d0f
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469483"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="e8bf7-102">Практическое руководство. Обработка нескольких событий с помощью их свойств</span><span class="sxs-lookup"><span data-stu-id="e8bf7-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="e8bf7-103">Чтобы использовать свойства событий, следует определить свойства событий в классе, который вызывает события, а затем задать делегаты для свойств событий в классах, обрабатывающих события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="e8bf7-104">Для реализации нескольких свойств событий в классе класс должен хранить и обслуживать внутри себя делегата, определенного для каждого события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="e8bf7-105">Типичная стратегия заключается в реализации коллекции делегатов, которая индексируется по ключу события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="e8bf7-106">Для сохранения делегатов для каждого события можно воспользоваться классом <xref:System.ComponentModel.EventHandlerList> или реализовать собственную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="e8bf7-107">Класс коллекции должен предоставить методы для установки, извлечения делегата обработчика событий и доступа к нему по ключу события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="e8bf7-108">Например, можно использовать класс <xref:System.Collections.Hashtable> или извлечь пользовательский класс от класса <xref:System.Collections.DictionaryBase>.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="e8bf7-109">Сведения о реализации коллекции делегатов не обязательно предоставлять за пределами класса.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="e8bf7-110">Каждое свойство события внутри класса определяет метод доступа add и remove.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="e8bf7-111">Метод доступа add для свойства события добавляет входной экземпляр делегата в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="e8bf7-112">Метод доступа remove для свойства события удаляет входной экземпляр делегата из коллекции.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="e8bf7-113">Методы доступа к свойствам событий используют предопределенный ключ для свойства события, чтобы добавлять экземпляры в коллекцию делегатов и удалять их из нее.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="e8bf7-114">Обработка нескольких событий с помощью их свойств</span><span class="sxs-lookup"><span data-stu-id="e8bf7-114">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="e8bf7-115">Определите коллекцию делегатов внутри класса, который вызывает события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="e8bf7-116">Определите ключ для каждого события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-116">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="e8bf7-117">Определите свойства событий в классе, который вызывает события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-117">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="e8bf7-118">Используйте коллекцию делегатов для реализации методов доступа add и remove для свойств событий.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="e8bf7-119">Используйте открытые свойства событий делегатов обработчика событий добавления и удаления в классах, обрабатывающих эти события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bf7-120">Пример</span><span class="sxs-lookup"><span data-stu-id="e8bf7-120">Example</span></span>  
 <span data-ttu-id="e8bf7-121">В следующем примере C# реализуются свойства событий `MouseDown` и `MouseUp` с использованием объекта <xref:System.ComponentModel.EventHandlerList> для хранения делегата каждого события.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="e8bf7-122">Ключевые слова для конструкции свойств событий выделены жирным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-122">The keywords of the event property constructs are in bold type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8bf7-123">Свойства событий не поддерживаются в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8bf7-123">Event properties are not supported in Visual Basic.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="e8bf7-124">См. также</span><span class="sxs-lookup"><span data-stu-id="e8bf7-124">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="e8bf7-125">События</span><span class="sxs-lookup"><span data-stu-id="e8bf7-125">Events</span></span>](../../../docs/standard/events/index.md)
- <xref:System.Web.UI.Control.Events%2A>
- [<span data-ttu-id="e8bf7-126">Практическое руководство. Объявление пользовательских событий для экономии памяти</span><span class="sxs-lookup"><span data-stu-id="e8bf7-126">How to: Declare Custom Events To Conserve Memory</span></span>](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
