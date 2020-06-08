---
title: Асинхронное программирование с использованием делегатов
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 82e0a57c3d8e180456aed48886e38ca466db16c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289971"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="ef8b5-102">Асинхронное программирование с использованием делегатов</span><span class="sxs-lookup"><span data-stu-id="ef8b5-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="ef8b5-103">Делегаты позволяют вызывать синхронные методы асинхронно.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="ef8b5-104">При синхронном вызове делегата метод `Invoke` вызывает целевой метод непосредственно в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="ef8b5-105">При вызове метода `BeginInvoke` среда CLR помещает запрос в очередь и сразу же передает управление вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="ef8b5-106">Целевой метод вызывается асинхронно в потоке из пула потоков.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="ef8b5-107">Исходный поток, отправивший этот запрос, продолжает выполняться параллельно с целевым методом.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="ef8b5-108">Если при вызове метода `BeginInvoke` был указан метод обратного вызова, то метод обратного вызова вызывается после завершения целевого метода.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="ef8b5-109">В методе обратного вызова метод `EndInvoke` получает возвращаемое значение и любые параметры ввода/вывода или только выходные параметры.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="ef8b5-110">Если при вызове `BeginInvoke` не указан метод обратного вызова, `EndInvoke` можно вызвать из потока, который вызвал `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef8b5-111">Компиляторы должны формировать классы делегатов с методами `Invoke`, `BeginInvoke`, и `EndInvoke` с использованием сигнатуры делегата, задаваемой пользователем.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="ef8b5-112">Методы `BeginInvoke` и `EndInvoke` должны быть объявлены как собственные.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="ef8b5-113">Поскольку эти методы помечены как собственные, среда CLR автоматически обеспечивает реализацию во время загрузки класса.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="ef8b5-114">Загрузчик проверяет, что эти методы не переопределены.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef8b5-115">Содержание</span><span class="sxs-lookup"><span data-stu-id="ef8b5-115">In This Section</span></span>  
 [<span data-ttu-id="ef8b5-116">Асинхронный вызов синхронных методов</span><span class="sxs-lookup"><span data-stu-id="ef8b5-116">Calling Synchronous Methods Asynchronously</span></span>](calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="ef8b5-117">Обсуждается использование делегатов для асинхронного вызова обычных методов, и приводятся примеры кода, демонстрирующие четыре способа ожидания возврата асинхронного вызова.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef8b5-118">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="ef8b5-118">Related Sections</span></span>  
 [<span data-ttu-id="ef8b5-119">Асинхронная модель на основе событий (EAP)</span><span class="sxs-lookup"><span data-stu-id="ef8b5-119">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="ef8b5-120">Описывается асинхронное программирование в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef8b5-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8b5-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ef8b5-121">See also</span></span>

- <xref:System.Delegate>
