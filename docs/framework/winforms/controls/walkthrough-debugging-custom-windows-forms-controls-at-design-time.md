---
title: Пошаговое руководство. Отладка пользовательских элементов управления Windows Forms во время разработки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: db6266f30c4fb62364f3c40a75a4a11ef853c1cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325362"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="d7339-102">Пошаговое руководство. Отладка пользовательских элементов управления Windows Forms во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="d7339-103">При создании пользовательского элемента управления, вам будет часто понадобиться для отладки его поведение во время разработки.</span><span class="sxs-lookup"><span data-stu-id="d7339-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="d7339-104">Это особенно верно в случае, если вы создаете пользовательский конструктор для элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="d7339-105">Дополнительные сведения см. в разделе [Пошаговое руководство: Создание Windows Forms элемент управления, который использует преимущества средств разработки Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="d7339-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="d7339-106">Можно выполнять отладку пользовательских элементов управления с помощью Visual Studio, так же, как отладка любого других классов .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7339-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="d7339-107">Разница заключается в том, что необходимо отладить отдельный экземпляр Visual Studio, на котором выполняется код настраиваемого элемента управления</span><span class="sxs-lookup"><span data-stu-id="d7339-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="d7339-108">В данном пошаговом руководстве представлены следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="d7339-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d7339-109">Создание проекта Windows Forms для размещения пользовательского элемента управления</span><span class="sxs-lookup"><span data-stu-id="d7339-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="d7339-110">Создание проекта библиотеки элементов управления</span><span class="sxs-lookup"><span data-stu-id="d7339-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="d7339-111">Добавление свойства в элемент управления</span><span class="sxs-lookup"><span data-stu-id="d7339-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="d7339-112">Добавление элемента управления в форму</span><span class="sxs-lookup"><span data-stu-id="d7339-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="d7339-113">Настройка проекта для отладки во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="d7339-114">Отладка пользовательского элемента управления во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="d7339-115">Когда вы закончите, вы получите представление о задачи, необходимые для отладки поведения времени разработки пользовательского элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7339-116">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="d7339-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d7339-117">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="d7339-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d7339-118">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d7339-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d7339-119">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="d7339-119">Creating the Project</span></span>  
 <span data-ttu-id="d7339-120">Первым шагом является создание проекта приложения.</span><span class="sxs-lookup"><span data-stu-id="d7339-120">The first step is to create the application project.</span></span> <span data-ttu-id="d7339-121">Этот проект будет использован для построения приложения, на котором размещается пользовательский элемент управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d7339-122">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="d7339-122">To create the project</span></span>  
  
-   <span data-ttu-id="d7339-123">Создайте проект приложения Windows с именем «DebuggingExample» (**файл** > **New** > **проекта**  >  **Visual C#** или **Visual Basic** > **классический рабочий стол** > **Windows Forms Application**).</span><span class="sxs-lookup"><span data-stu-id="d7339-123">Create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="d7339-124">Создание проекта библиотеки элементов управления</span><span class="sxs-lookup"><span data-stu-id="d7339-124">Creating a Control Library Project</span></span>  
 <span data-ttu-id="d7339-125">Следующим шагом является создание проекта библиотеки элементов управления и настройка пользовательского элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-125">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="d7339-126">Чтобы создать проект библиотеки элементов управления</span><span class="sxs-lookup"><span data-stu-id="d7339-126">To create the control library project</span></span>  
  
1. <span data-ttu-id="d7339-127">Добавить **Windows Control Library** проекта к решению.</span><span class="sxs-lookup"><span data-stu-id="d7339-127">Add a **Windows Control Library** project to the solution.</span></span>  
  
2. <span data-ttu-id="d7339-128">Добавьте новый **UserControl** DebugControlLibrary проект.</span><span class="sxs-lookup"><span data-stu-id="d7339-128">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="d7339-129">Подробную информацию см. в разделе [Практическое руководство. Добавление новых элементов проекта](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d7339-129">For details, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="d7339-130">Предоставить новый исходный файл «DebugControl» базовым именем.</span><span class="sxs-lookup"><span data-stu-id="d7339-130">Give the new source file a base name of "DebugControl".</span></span>  
  
3. <span data-ttu-id="d7339-131">С помощью **обозревателе решений**, удалите элемент управления проекта по умолчанию путем удаления файла с базовым именем "`UserControl1`«.</span><span class="sxs-lookup"><span data-stu-id="d7339-131">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="d7339-132">Подробную информацию см. в разделе [Практическое руководство. Удалить, удаление и исключить элементы](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d7339-132">For details, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>  
  
4. <span data-ttu-id="d7339-133">Постройте решение.</span><span class="sxs-lookup"><span data-stu-id="d7339-133">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="d7339-134">Контрольная точка</span><span class="sxs-lookup"><span data-stu-id="d7339-134">Checkpoint</span></span>  
 <span data-ttu-id="d7339-135">На этом этапе вы сможете для пользовательского элемента управления в см. в разделе **элементов**.</span><span class="sxs-lookup"><span data-stu-id="d7339-135">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="d7339-136">Чтобы проверить ход</span><span class="sxs-lookup"><span data-stu-id="d7339-136">To check your progress</span></span>  
  
-   <span data-ttu-id="d7339-137">Найдите новый вкладку с именем **компоненты DebugControlLibrary** и установите его.</span><span class="sxs-lookup"><span data-stu-id="d7339-137">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="d7339-138">Когда она откроется, вы увидите в списке управления **DebugControl** со значком по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d7339-138">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="d7339-139">Добавление свойства в элемент управления</span><span class="sxs-lookup"><span data-stu-id="d7339-139">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="d7339-140">Чтобы продемонстрировать, выполнение кода пользовательского элемента управления во время разработки, будет добавить свойство и установите точку останова в коде, который реализует свойство.</span><span class="sxs-lookup"><span data-stu-id="d7339-140">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="d7339-141">Добавление свойства в элемент управления</span><span class="sxs-lookup"><span data-stu-id="d7339-141">To add a property to your custom control</span></span>  
  
1. <span data-ttu-id="d7339-142">Откройте **DebugControl** в **редактор кода**.</span><span class="sxs-lookup"><span data-stu-id="d7339-142">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="d7339-143">Добавьте следующий код в определение класса:</span><span class="sxs-lookup"><span data-stu-id="d7339-143">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="d7339-144">Постройте решение.</span><span class="sxs-lookup"><span data-stu-id="d7339-144">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="d7339-145">Добавление элемента управления в форму</span><span class="sxs-lookup"><span data-stu-id="d7339-145">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="d7339-146">Для отладки поведения времени разработки пользовательского элемента управления, поместите экземпляр класса пользовательского элемента управления в форму.</span><span class="sxs-lookup"><span data-stu-id="d7339-146">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="d7339-147">Чтобы добавить пользовательский элемент управления в форму</span><span class="sxs-lookup"><span data-stu-id="d7339-147">To add your custom control to the host form</span></span>  
  
1. <span data-ttu-id="d7339-148">В проекте «DebuggingExample», откройте форму Form1 в **конструктор Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="d7339-148">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2. <span data-ttu-id="d7339-149">В **элементов**откройте **компоненты DebugControlLibrary** вкладку и перетащите **DebugControl** экземпляра на форму.</span><span class="sxs-lookup"><span data-stu-id="d7339-149">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3. <span data-ttu-id="d7339-150">Найти `DemoString` пользовательское свойство в **свойства** окна.</span><span class="sxs-lookup"><span data-stu-id="d7339-150">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="d7339-151">Обратите внимание на то, что его значение можно изменить, как любое другое свойство.</span><span class="sxs-lookup"><span data-stu-id="d7339-151">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="d7339-152">Также Обратите внимание, что при `DemoString` было выбрано свойство, строка описания свойства отображается в нижней части **свойства** окна.</span><span class="sxs-lookup"><span data-stu-id="d7339-152">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="d7339-153">Настройка проекта для отладки во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-153">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="d7339-154">Для отладки поведения пользовательского элемента управления во время разработки, необходимо отладить отдельный экземпляр Visual Studio, на котором выполняется код настраиваемого элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-154">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="d7339-155">Чтобы настроить проект для отладки во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-155">To set up the project for design-time debugging</span></span>  
  
1. <span data-ttu-id="d7339-156">Щелкните правой кнопкой мыши **DebugControlLibrary** в проекте **обозревателе решений** и выберите **свойства**.</span><span class="sxs-lookup"><span data-stu-id="d7339-156">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2. <span data-ttu-id="d7339-157">В **DebugControlLibrary** свойств, выберите **Отладка** вкладки.</span><span class="sxs-lookup"><span data-stu-id="d7339-157">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="d7339-158">В **действие при запуске** выберите **запуск внешней программы**.</span><span class="sxs-lookup"><span data-stu-id="d7339-158">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="d7339-159">Вы будете отладка отдельного экземпляра Visual Studio, поэтому нажмите кнопку с многоточием (![экрана VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) чтобы перейти в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7339-159">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="d7339-160">Имя исполняемого файла — **devenv.exe**, и если вы установили в расположение по умолчанию, его путь — 9.0\Common7\IDE\devenv.exe %programfiles%\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7339-160">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3. <span data-ttu-id="d7339-161">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="d7339-161">Click **OK** to close the dialog box.</span></span>  
  
4. <span data-ttu-id="d7339-162">Щелкните правой кнопкой мыши **DebugControlLibrary** проекта и выберите **Назначить запускаемым проектом** включить конфигурацию отладки.</span><span class="sxs-lookup"><span data-stu-id="d7339-162">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="d7339-163">Отладка пользовательского элемента управления во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-163">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="d7339-164">Теперь вы готовы к отладке пользовательского элемента управления в режиме конструктора.</span><span class="sxs-lookup"><span data-stu-id="d7339-164">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="d7339-165">При запуске сеанса отладки, будет создан новый экземпляр Visual Studio, и он будет использоваться для загрузки решения «DebuggingExample».</span><span class="sxs-lookup"><span data-stu-id="d7339-165">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="d7339-166">При открытии Form1 в **конструктор форм**, экземпляр пользовательского элемента управления будет создан и запущен.</span><span class="sxs-lookup"><span data-stu-id="d7339-166">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="d7339-167">Отладка пользовательского элемента управления во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-167">To debug your custom control at design time</span></span>  
  
1. <span data-ttu-id="d7339-168">Откройте **DebugControl** исходный файл в **редактор кода** и поместите точку останова на `Set` метод доступа `DemoString` свойство.</span><span class="sxs-lookup"><span data-stu-id="d7339-168">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2. <span data-ttu-id="d7339-169">Нажмите клавишу F5, чтобы запустить сеанс отладки.</span><span class="sxs-lookup"><span data-stu-id="d7339-169">Press F5 to start the debugging session.</span></span> <span data-ttu-id="d7339-170">Обратите внимание на то, что создается новый экземпляр Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7339-170">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="d7339-171">Может различать экземпляры двумя способами:</span><span class="sxs-lookup"><span data-stu-id="d7339-171">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="d7339-172">Экземпляр отладки имеет слово **под управлением** в заголовке окна</span><span class="sxs-lookup"><span data-stu-id="d7339-172">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="d7339-173">У экземпляра отладки **запустить** кнопку на его **Отладка** инструментов отключена</span><span class="sxs-lookup"><span data-stu-id="d7339-173">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="d7339-174">Точка останова устанавливается в экземпляре отладки.</span><span class="sxs-lookup"><span data-stu-id="d7339-174">Your breakpoint is set in the debugging instance.</span></span>  
  
3. <span data-ttu-id="d7339-175">В новом экземпляре Visual Studio откройте решение «DebuggingExample».</span><span class="sxs-lookup"><span data-stu-id="d7339-175">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="d7339-176">Решение можно легко найти, выбрав **последние проекты** из **файл** меню.</span><span class="sxs-lookup"><span data-stu-id="d7339-176">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="d7339-177">Файл решения «DebuggingExample.sln» отображаются как последних использовавшихся файлов.</span><span class="sxs-lookup"><span data-stu-id="d7339-177">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4. <span data-ttu-id="d7339-178">Откройте форму Form1 в **конструктор форм** и выберите **DebugControl** элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-178">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5. <span data-ttu-id="d7339-179">Измените значение свойства `DemoString` .</span><span class="sxs-lookup"><span data-stu-id="d7339-179">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="d7339-180">Обратите внимание, что при фиксации изменений, отладочный экземпляр Visual Studio получает фокус, и выполнение остановится в точке останова.</span><span class="sxs-lookup"><span data-stu-id="d7339-180">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="d7339-181">Вы можете пошагово выполнить метод доступа к свойству так же, как к любой другой код.</span><span class="sxs-lookup"><span data-stu-id="d7339-181">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6. <span data-ttu-id="d7339-182">Когда вы закончите с сеанс отладки, можно выйти из закрыв второй экземпляр Visual Studio или щелкнув **остановить отладку** кнопки в экземпляре отладки.</span><span class="sxs-lookup"><span data-stu-id="d7339-182">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d7339-183">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="d7339-183">Next Steps</span></span>  
 <span data-ttu-id="d7339-184">Теперь, когда можно отлаживать пользовательские элементы управления во время разработки, существует множество возможностей для расширения взаимодействия элемента управления с помощью Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="d7339-184">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="d7339-185">Можно использовать <xref:System.ComponentModel.Component.DesignMode%2A> свойство <xref:System.ComponentModel.Component> для написания кода, который будет выполняться только во время разработки.</span><span class="sxs-lookup"><span data-stu-id="d7339-185">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="d7339-186">Дополнительные сведения см. в разделе <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7339-186">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="d7339-187">Существует несколько атрибутов можно применить к свойствам элемента управления для управления взаимодействием элемента управления с помощью конструктора.</span><span class="sxs-lookup"><span data-stu-id="d7339-187">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="d7339-188">Вы найдете эти атрибуты в <xref:System.ComponentModel?displayProperty=nameWithType> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="d7339-188">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="d7339-189">Можно написать пользовательский конструктор для элемента управления.</span><span class="sxs-lookup"><span data-stu-id="d7339-189">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="d7339-190">Это дает полный контроль над разработкой с помощью расширяемой инфраструктуры конструкторов в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7339-190">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="d7339-191">Дополнительные сведения см. в разделе [Пошаговое руководство: Создание Windows Forms элемент управления, который использует преимущества средств разработки Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="d7339-191">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7339-192">См. также</span><span class="sxs-lookup"><span data-stu-id="d7339-192">See also</span></span>

- [<span data-ttu-id="d7339-193">Пошаговое руководство: Создание элемента управления Windows Forms, используются преимущества функций Visual Studio во время разработки</span><span class="sxs-lookup"><span data-stu-id="d7339-193">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
- <span data-ttu-id="d7339-194">[Практическое руководство. Доступа к службам времени разработки](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d7339-194">[How to: Access Design-Time Services](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))</span></span>
- <span data-ttu-id="d7339-195">[Практическое руководство. Поддержка разработки доступа в Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d7339-195">[How to: Access Design-Time Support in Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))</span></span>
