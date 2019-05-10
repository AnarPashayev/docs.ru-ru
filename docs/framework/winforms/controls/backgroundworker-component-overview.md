---
title: Общие сведения о компоненте BackgroundWorker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: da1d87464ef30fb549a2c201170e81c45cbdf6fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587743"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="05027-102">Общие сведения о компоненте BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="05027-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="05027-103">Выполнение многих часто выполняемых операций может занимать длительное время.</span><span class="sxs-lookup"><span data-stu-id="05027-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="05027-104">Пример:</span><span class="sxs-lookup"><span data-stu-id="05027-104">For example:</span></span>  
  
- <span data-ttu-id="05027-105">Загрузка изображений</span><span class="sxs-lookup"><span data-stu-id="05027-105">Image downloads</span></span>  
  
- <span data-ttu-id="05027-106">Вызовы веб-служб</span><span class="sxs-lookup"><span data-stu-id="05027-106">Web service invocations</span></span>  
  
- <span data-ttu-id="05027-107">Скачивание и загрузка файлов (в т. ч. через одноранговые приложения)</span><span class="sxs-lookup"><span data-stu-id="05027-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="05027-108">Сложные локальные вычисления</span><span class="sxs-lookup"><span data-stu-id="05027-108">Complex local computations</span></span>  
  
- <span data-ttu-id="05027-109">Транзакции баз данных</span><span class="sxs-lookup"><span data-stu-id="05027-109">Database transactions</span></span>  
  
- <span data-ttu-id="05027-110">Обращение к локальному диску в случае низкой скорости по сравнению с доступом к памяти</span><span class="sxs-lookup"><span data-stu-id="05027-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="05027-111">Запуск таких операций может замедлить работу пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="05027-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="05027-112">Если вы хотите получить отзывчивый пользовательский интерфейс, но столкнулись с длительными задержками в результате выполнения таких операций, удобным решением станет компонент <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="05027-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="05027-113">Компонент <xref:System.ComponentModel.BackgroundWorker> позволяет выполнять длительные операции асинхронно (в фоновом режиме), т. е. в потоке, отличающемся от основного потока пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="05027-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="05027-114">Для использование компонента <xref:System.ComponentModel.BackgroundWorker> необходимо только указать, какой рабочий метод обработки длительных операций будет выполняться в фоновом режиме, а затем вызвать метод <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="05027-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="05027-115">Вызывающий поток продолжает работать нормально, в то время как рабочий метод работает асинхронно.</span><span class="sxs-lookup"><span data-stu-id="05027-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="05027-116">Когда метод закончит работу, компонент <xref:System.ComponentModel.BackgroundWorker> предупредит вызывающий поток событием <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, которое может содержать результаты операции.</span><span class="sxs-lookup"><span data-stu-id="05027-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="05027-117"><xref:System.ComponentModel.BackgroundWorker> Компонент предоставляется компанией **элементов**в **компоненты** вкладки. Чтобы добавить компонент <xref:System.ComponentModel.BackgroundWorker> в форму, перетащите компонент <xref:System.ComponentModel.BackgroundWorker> в соответствующую форму.</span><span class="sxs-lookup"><span data-stu-id="05027-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="05027-118">Он отображается в области компонентов, и ее свойства появились на **свойства** окна.</span><span class="sxs-lookup"><span data-stu-id="05027-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="05027-119">Для запуска асинхронной работы используйте метод <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="05027-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="05027-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> принимает необязательный `object` параметр, который может использоваться для передачи аргументов рабочему методу.</span><span class="sxs-lookup"><span data-stu-id="05027-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="05027-121">Класс <xref:System.ComponentModel.BackgroundWorker> показывает событие <xref:System.ComponentModel.BackgroundWorker.DoWork>, к которому обработчик событий <xref:System.ComponentModel.BackgroundWorker.DoWork> прикрепляет рабочий поток.</span><span class="sxs-lookup"><span data-stu-id="05027-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="05027-122">Обработчик событий <xref:System.ComponentModel.BackgroundWorker.DoWork> задействует параметр <xref:System.ComponentModel.DoWorkEventArgs> со свойством <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>.</span><span class="sxs-lookup"><span data-stu-id="05027-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="05027-123">Данное свойство получает параметр из <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> и может быть передано в рабочий метод, который будет вызываться в обработчике событий <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="05027-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="05027-124">В следующем примере показан способ назначения результата из рабочего метода, который называется `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="05027-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="05027-125">Он является частью большего примера, который можно найти в [как: Реализация формы, в который выполняется фоновая операция](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="05027-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="05027-126">Дополнительные сведения об использовании обработчиков событий см. в разделе [события](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="05027-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="05027-127">При использовании любой многопоточности существует потенциальная возможность возникновения серьезных ошибок.</span><span class="sxs-lookup"><span data-stu-id="05027-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="05027-128">Перед реализацией любого решения, в котором используется многопоточность, ознакомьтесь с разделом [Рекомендации по работе с потоками](../../../standard/threading/managed-threading-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="05027-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="05027-129">Дополнительные сведения об использовании <xref:System.ComponentModel.BackgroundWorker> , представлена в разделе [как: Фоновое выполнение операции](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="05027-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05027-130">См. также</span><span class="sxs-lookup"><span data-stu-id="05027-130">See also</span></span>

- [<span data-ttu-id="05027-131">Управляемая поточность</span><span class="sxs-lookup"><span data-stu-id="05027-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="05027-132">Обзор асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="05027-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="05027-133">Практическое руководство. Реализация формы, в которой выполняется фоновая операция</span><span class="sxs-lookup"><span data-stu-id="05027-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
