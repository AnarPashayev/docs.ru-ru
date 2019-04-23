---
title: Практическое руководство. Создание надстройки, возвращающей пользовательский интерфейс
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115756"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="4952e-102">Практическое руководство. Создание надстройки, возвращающей пользовательский интерфейс</span><span class="sxs-lookup"><span data-stu-id="4952e-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="4952e-103">В этом примере показано, как создать надстройку, возвращающий Windows Presentation Foundation (WPF) на узел автономного приложения WPF.</span><span class="sxs-lookup"><span data-stu-id="4952e-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="4952e-104">Надстройка возвращает пользовательский Интерфейс, который является пользовательский элемент управления WPF.</span><span class="sxs-lookup"><span data-stu-id="4952e-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="4952e-105">Содержимое пользовательского элемента управления составляет одна кнопка, при нажатии которой отображается окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="4952e-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="4952e-106">Автономное приложение WPF размещает надстройку и отображает пользовательский элемент управления (возвращенный надстройкой) как содержимое главного окна приложения.</span><span class="sxs-lookup"><span data-stu-id="4952e-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="4952e-107">**Необходимые компоненты**</span><span class="sxs-lookup"><span data-stu-id="4952e-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="4952e-108">В этом примере представлены расширения WPF модель надстроек платформы .NET Framework, реализовать этот сценарий и предполагается следующее:</span><span class="sxs-lookup"><span data-stu-id="4952e-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="4952e-109">Знание модели надстроек платформы .NET Framework, включая конвейер, надстройка и разработку основного приложения.</span><span class="sxs-lookup"><span data-stu-id="4952e-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="4952e-110">Если вы не знакомы с этими понятиями, см. в разделе [надстройки и расширения](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="4952e-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="4952e-111">Учебник, в котором демонстрируется реализация конвейера, надстройки и ведущего приложения, см. в разделе [Пошаговое руководство: Создание расширяемого приложения](../../add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="4952e-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="4952e-112">Знание расширений WPF в .NET Framework модель надстроек, которые можно найти здесь: [Общие сведения о надстройках WPF](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4952e-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4952e-113">Пример</span><span class="sxs-lookup"><span data-stu-id="4952e-113">Example</span></span>  
 <span data-ttu-id="4952e-114">Создание надстройки, возвращающей пользовательский Интерфейс WPF требуется специальный код для каждого сегмента конвейера, надстройки и ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="4952e-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="4952e-115">Реализация сегмента конвейера контракта</span><span class="sxs-lookup"><span data-stu-id="4952e-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="4952e-116">Метод должен быть определен контрактом для возвращения пользовательского интерфейса и его возвращаемое значение должно быть типа <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="4952e-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="4952e-117">Это демонстрируется путем `GetAddInUI` метод `IWPFAddInContract` контракта в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4952e-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="4952e-118">Реализация сегмента конвейера представления надстройки</span><span class="sxs-lookup"><span data-stu-id="4952e-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="4952e-119">Поскольку надстройка реализует [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] предоставляет в качестве подклассов <xref:System.Windows.FrameworkElement>, метод представления надстройки, которое связано с `IWPFAddInView.GetAddInUI` должен возвращать значение типа <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="4952e-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="4952e-120">В следующем коде показано представление надстройки контракта, реализованное как интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4952e-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="4952e-121">Реализация сегмента конвейера адаптера надстройки</span><span class="sxs-lookup"><span data-stu-id="4952e-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="4952e-122">Метод контракта возвращает <xref:System.AddIn.Contract.INativeHandleContract>, но Надстройка возвращает <xref:System.Windows.FrameworkElement> (как указано представлением надстройки).</span><span class="sxs-lookup"><span data-stu-id="4952e-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="4952e-123">Следовательно <xref:System.Windows.FrameworkElement> должны быть преобразованы в <xref:System.AddIn.Contract.INativeHandleContract> перед пересечением границы изоляции.</span><span class="sxs-lookup"><span data-stu-id="4952e-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="4952e-124">Эту работу выполняет адаптер стороне надстройки, вызвав <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4952e-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="4952e-125">Реализация сегмента конвейера представления в основном приложении</span><span class="sxs-lookup"><span data-stu-id="4952e-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="4952e-126">Так как основное приложение будет отображать <xref:System.Windows.FrameworkElement>, метод представления главного приложения, которое связано с `IWPFAddInHostView.GetAddInUI` должен возвращать значение типа <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="4952e-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="4952e-127">В следующем коде показано представление контракта в основном приложении, реализованное как интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4952e-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="4952e-128">Реализация сегмента конвейера адаптера приложения</span><span class="sxs-lookup"><span data-stu-id="4952e-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="4952e-129">Метод контракта возвращает <xref:System.AddIn.Contract.INativeHandleContract>, но основное приложение ожидает <xref:System.Windows.FrameworkElement> (как указано представлением узла).</span><span class="sxs-lookup"><span data-stu-id="4952e-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="4952e-130">Следовательно <xref:System.AddIn.Contract.INativeHandleContract> должны быть преобразованы в <xref:System.Windows.FrameworkElement> после пересечения границы изоляции.</span><span class="sxs-lookup"><span data-stu-id="4952e-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="4952e-131">Эту работу выполняет адаптер на стороне узла, вызвав <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4952e-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="4952e-132">Реализация надстройки</span><span class="sxs-lookup"><span data-stu-id="4952e-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="4952e-133">Адаптер на стороне надстройки и надстройка созданного представления надстройки (`WPFAddIn1.AddIn`) должен реализовывать `IWPFAddInView.GetAddInUI` метод для возврата <xref:System.Windows.FrameworkElement> объекта ( <xref:System.Windows.Controls.UserControl> в этом примере).</span><span class="sxs-lookup"><span data-stu-id="4952e-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="4952e-134">Реализация <xref:System.Windows.Controls.UserControl>, `AddInUI`, показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="4952e-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="4952e-135">Реализация `IWPFAddInView.GetAddInUI` надстройкой просто должен возвращать новый экземпляр класса `AddInUI`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="4952e-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="4952e-136">Реализация ведущего приложения</span><span class="sxs-lookup"><span data-stu-id="4952e-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="4952e-137">Адаптер и созданного представления узла, ведущее приложение может использовать модель надстроек платформы .NET Framework, чтобы открыть конвейер, получить серверное представление надстройки, и вызовите `IWPFAddInHostView.GetAddInUI` метод.</span><span class="sxs-lookup"><span data-stu-id="4952e-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="4952e-138">Эти действия показаны в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4952e-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="4952e-139">См. также</span><span class="sxs-lookup"><span data-stu-id="4952e-139">See also</span></span>

- <span data-ttu-id="4952e-140">[Надстройки и расширения среды](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="4952e-140">[Add-ins and Extensibility](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="4952e-141">Общие сведения о надстройках WPF</span><span class="sxs-lookup"><span data-stu-id="4952e-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
