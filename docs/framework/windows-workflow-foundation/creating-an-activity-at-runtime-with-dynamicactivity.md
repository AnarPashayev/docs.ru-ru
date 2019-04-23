---
title: Создание действия в среде выполнения с динамическим действием
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321238"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="2bdf5-102">Создание действия в среде выполнения с динамическим действием</span><span class="sxs-lookup"><span data-stu-id="2bdf5-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="2bdf5-103"><xref:System.Activities.DynamicActivity> представляет собой конкретный запечатанный класс с открытым конструктором.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="2bdf5-104"><xref:System.Activities.DynamicActivity> может использоваться для объединения функций действий во время выполнения с помощью действия DOM.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="2bdf5-105">Возможности DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="2bdf5-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="2bdf5-106"><xref:System.Activities.DynamicActivity> имеет доступ к свойствам, аргументам и переменным выполнения, но не имеет доступа к службам среды выполнения, таким как дочерние действия планирования и отслеживание.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="2bdf5-107">Значения свойств верхнего уровня можно задавать при помощи объектов рабочих процессов <xref:System.Activities.Argument>.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="2bdf5-108">В императивном коде эти аргументы создаются при помощи свойств среды CLR в новом типе.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="2bdf5-109">На языке XAML такие аргументы объявляются при помощи тегов `x:Class` и `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="2bdf5-110">Действия, построенные при помощи интерфейса <xref:System.Activities.DynamicActivity> в конструкторе, использующем <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="2bdf5-111">Действия, созданные в конструкторе, можно загружать динамически с помощью <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, как показано в следующей процедуре.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="2bdf5-112">Создание действия во время выполнения при помощи императивного кода</span><span class="sxs-lookup"><span data-stu-id="2bdf5-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="2bdf5-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2bdf5-114">Выберите **файл**, **новый**, **проекта**.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2bdf5-115">Выберите **Workflow 4.0** под **Visual C#** в **типы проектов** затем выберите **v2010** узла.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2bdf5-116">Выберите **консольного приложения последовательного рабочего процесса** в **шаблоны** окна.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2bdf5-117">Задайте имя для нового проекта DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2bdf5-118">Щелкните правой кнопкой мыши файл Workflow1.xaml в проекте HelloActivity и выберите **удалить**.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="2bdf5-119">Откройте файл Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-119">Open Program.cs.</span></span> <span data-ttu-id="2bdf5-120">Добавьте следующую директиву в начало файла.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="2bdf5-121">Замените содержимое метода `Main` следующим кодом, который создаст действие <xref:System.Activities.Statements.Sequence>, содержащее отдельное действие <xref:System.Activities.Statements.WriteLine>, и назначит его свойству <xref:System.Activities.DynamicActivity.Implementation%2A> нового динамического действия.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. <span data-ttu-id="2bdf5-122">Выполните приложение.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-122">Execute the application.</span></span> <span data-ttu-id="2bdf5-123">Окно консоли с текстом «Hello World!»</span><span class="sxs-lookup"><span data-stu-id="2bdf5-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2bdf5-124">Отображает.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="2bdf5-125">Создание действия во время выполнения при помощи языка XAML</span><span class="sxs-lookup"><span data-stu-id="2bdf5-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="2bdf5-126">Откройте Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2bdf5-127">Выберите **файл**, **новый**, **проекта**.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2bdf5-128">Выберите **Workflow 4.0** под **Visual C#** в **типы проектов** затем выберите **v2010** узла.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2bdf5-129">Выберите **консольное приложение рабочего процесса** в **шаблоны** окна.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2bdf5-130">Задайте имя для нового проекта DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2bdf5-131">Откройте файл Workflow1.xaml в проекте HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="2bdf5-132">Нажмите кнопку **аргументы** в нижней части конструктора.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="2bdf5-133">Создайте новый аргумент `In`, вызываемый методом `TextToWrite` типа `String`.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="2bdf5-134">Перетащите **WriteLine** действия из **примитивы** разделе области элементов в область конструктора.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="2bdf5-135">Назначьте `TextToWrite` для **текст** свойства действия.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="2bdf5-136">Откройте файл Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-136">Open Program.cs.</span></span> <span data-ttu-id="2bdf5-137">Добавьте следующую директиву в начало файла.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="2bdf5-138">Замените содержимое метода `Main` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="2bdf5-139">Выполните приложение.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-139">Execute the application.</span></span> <span data-ttu-id="2bdf5-140">Окно консоли с текстом «Hello World!»</span><span class="sxs-lookup"><span data-stu-id="2bdf5-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2bdf5-141">отображается.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-141">appears.</span></span>  
  
8. <span data-ttu-id="2bdf5-142">Щелкните правой кнопкой мыши файл Workflow1.xaml в **обозревателе решений** и выберите **Просмотр кода**.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="2bdf5-143">Следует отметить, что класс действия создается при помощи `x:Class`, а свойство - при помощи `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="2bdf5-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bdf5-144">См. также</span><span class="sxs-lookup"><span data-stu-id="2bdf5-144">See also</span></span>

- [<span data-ttu-id="2bdf5-145">Разработка рабочих процессов, действий и выражений с использованием императивного кода</span><span class="sxs-lookup"><span data-stu-id="2bdf5-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
