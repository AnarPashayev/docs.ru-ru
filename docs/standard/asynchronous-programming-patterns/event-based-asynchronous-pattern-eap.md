---
title: Асинхронная модель на основе событий (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 604e7a944579a284004817009b06c11b268d5daf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289438"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="df1e3-102">Асинхронная модель на основе событий (EAP)</span><span class="sxs-lookup"><span data-stu-id="df1e3-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="df1e3-103">Существует несколько способов предоставить асинхронные возможности клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="df1e3-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="df1e3-104">Асинхронная модель на основе событий задает для классов рекомендуемый способ работы в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="df1e3-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df1e3-105">Начиная с версии .NET Framework 4 библиотека параллельных задач предоставляет новую модель для асинхронного и параллельного программирования.</span><span class="sxs-lookup"><span data-stu-id="df1e3-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="df1e3-106">Дополнительные сведения см. в разделах [Библиотека параллельных задач (TPL)](../parallel-programming/task-parallel-library-tpl.md) и [Асинхронная модель на основе задач (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="df1e3-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="df1e3-107">Содержание</span><span class="sxs-lookup"><span data-stu-id="df1e3-107">In This Section</span></span>

 [<span data-ttu-id="df1e3-108">Обзор асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="df1e3-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="df1e3-109">Описывает, как асинхронная модель на основе событий позволяет использовать преимущества многопоточных приложений и устраняет многие сложности, присущие многопоточности.</span><span class="sxs-lookup"><span data-stu-id="df1e3-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="df1e3-110">Реализация асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="df1e3-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-111">Описывает стандартизированный способ упаковки класса, имеющего асинхронные возможности.</span><span class="sxs-lookup"><span data-stu-id="df1e3-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="df1e3-112">Рекомендации по реализации асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="df1e3-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-113">Описывает требования для предоставления асинхронных возможностей в соответствии с асинхронной моделью на основе событий.</span><span class="sxs-lookup"><span data-stu-id="df1e3-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="df1e3-114">Определение, когда следует реализовать асинхронную модель, основанную на событиях</span><span class="sxs-lookup"><span data-stu-id="df1e3-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-115">Описывает, в каких случаях следует реализовать асинхронную модель на основе событий вместо шаблона <xref:System.IAsyncResult>, представленного [асинхронной моделью программирования (APM)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="df1e3-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="df1e3-116">Практическое руководство. Реализация компонента, поддерживающего асинхронную модель на основе событий</span><span class="sxs-lookup"><span data-stu-id="df1e3-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-117">Описывает, как создать компонент, реализующий асинхронную модель на основе событий.</span><span class="sxs-lookup"><span data-stu-id="df1e3-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="df1e3-118">Она реализуется с использованием вспомогательных классов из пространства имен <xref:System.ComponentModel?displayProperty=nameWithType>, что обеспечивает правильную работу компонента при любой модели приложения.</span><span class="sxs-lookup"><span data-stu-id="df1e3-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="df1e3-119">Практическое руководство. Реализация клиента асинхронной модели на основе событий</span><span class="sxs-lookup"><span data-stu-id="df1e3-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-120">Описывает, как создать клиент, который использует компонент, реализующий асинхронную модель на основе событий.</span><span class="sxs-lookup"><span data-stu-id="df1e3-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="df1e3-121">Практическое руководство. Использование компонентов, поддерживающих асинхронную модель, основанную на событиях</span><span class="sxs-lookup"><span data-stu-id="df1e3-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="df1e3-122">Описывает использование компонента, поддерживающего асинхронную модель на основе событий.</span><span class="sxs-lookup"><span data-stu-id="df1e3-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="df1e3-123">Справочник</span><span class="sxs-lookup"><span data-stu-id="df1e3-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="df1e3-124">Описывает класс <xref:System.ComponentModel.AsyncOperation> и содержит ссылки на все его члены.</span><span class="sxs-lookup"><span data-stu-id="df1e3-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="df1e3-125">Описывает класс <xref:System.ComponentModel.AsyncOperationManager> и содержит ссылки на все его члены.</span><span class="sxs-lookup"><span data-stu-id="df1e3-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="df1e3-126">Описывает компонент <xref:System.ComponentModel.BackgroundWorker> и содержит ссылки на все его члены.</span><span class="sxs-lookup"><span data-stu-id="df1e3-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="df1e3-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="df1e3-127">Related Sections</span></span>

 [<span data-ttu-id="df1e3-128">Библиотека параллельных задач (TPL)</span><span class="sxs-lookup"><span data-stu-id="df1e3-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="df1e3-129">Описание модели программирования для асинхронных и параллельных операций.</span><span class="sxs-lookup"><span data-stu-id="df1e3-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="df1e3-130">Работа с потоками</span><span class="sxs-lookup"><span data-stu-id="df1e3-130">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="df1e3-131">Описывает многопоточные функциональные возможности в .NET.</span><span class="sxs-lookup"><span data-stu-id="df1e3-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1e3-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="df1e3-132">See also</span></span>

- [<span data-ttu-id="df1e3-133">Рекомендации по работе с потоками</span><span class="sxs-lookup"><span data-stu-id="df1e3-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="df1e3-134">События</span><span class="sxs-lookup"><span data-stu-id="df1e3-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="df1e3-135">Шаблоны асинхронного программирования</span><span class="sxs-lookup"><span data-stu-id="df1e3-135">Asynchronous Programming Design Patterns</span></span>](index.md)
