---
title: Практическое руководство. Добавление элементов управления, для которых не существует пользовательского интерфейса, в формы Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987092"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="0d149-102">Практическое руководство. Добавление элементов управления, для которых не существует пользовательского интерфейса, в формы Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="0d149-103">Невизуальный элемент управления (или компонент) предоставляет приложению функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="0d149-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="0d149-104">В отличие от других элементов управления, компоненты не предоставляют пользователю пользовательский интерфейс и, таким образом, не должны отображаться на поверхности конструктор Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d149-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="0d149-105">При добавлении компонента в форму конструктор Windows Forms отображает область с изменяемым размером в нижней части формы, где отображаются все компоненты.</span><span class="sxs-lookup"><span data-stu-id="0d149-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="0d149-106">После добавления элемента управления в область компонентов можно выбрать компонент и задать его свойства так же, как любой другой элемент управления в форме.</span><span class="sxs-lookup"><span data-stu-id="0d149-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="0d149-107">Добавление компонента в форму Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="0d149-108">Откройте форму в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d149-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="0d149-109">Подробную информацию см. в разделе [Практическое руководство. Отображение Windows Forms в конструкторе](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d149-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="0d149-110">На **панели элементов** щелкните компонент и перетащите его на форму.</span><span class="sxs-lookup"><span data-stu-id="0d149-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="0d149-111">Ваш компонент появится в области компонентов.</span><span class="sxs-lookup"><span data-stu-id="0d149-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="0d149-112">Более того, компоненты можно добавлять в форму во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d149-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="0d149-113">Это распространенный сценарий, особенно потому, что компоненты не имеют визуального выражения, в отличие от элементов управления с пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="0d149-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="0d149-114">В приведенном ниже <xref:System.Windows.Forms.Timer> примере компонент добавляется во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d149-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="0d149-115">(Обратите внимание, что Visual Studio содержит ряд различных таймеров; в этом случае используйте компонент Windows Forms <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="0d149-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="0d149-116">Дополнительные сведения о различных таймерах в Visual Studio см. в статье [Введение в серверные таймеры](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0d149-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="0d149-117">Компоненты часто имеют особые свойства, которые должны быть заданы для их эффективной работы.</span><span class="sxs-lookup"><span data-stu-id="0d149-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="0d149-118">В случае использования компонента <xref:System.Windows.Forms.Timer> в приведенном ниже примере задается свойство `Interval`.</span><span class="sxs-lookup"><span data-stu-id="0d149-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="0d149-119">Убедитесь, что при добавлении компонентов в проект вы задаете необходимые свойства этих компонентов.</span><span class="sxs-lookup"><span data-stu-id="0d149-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="0d149-120">Добавление компонента в форму Windows программным способом</span><span class="sxs-lookup"><span data-stu-id="0d149-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="0d149-121">Создайте экземпляр класса <xref:System.Windows.Forms.Timer> в коде.</span><span class="sxs-lookup"><span data-stu-id="0d149-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="0d149-122">Задайте свойство `Interval` для определения времени между тактами таймера.</span><span class="sxs-lookup"><span data-stu-id="0d149-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="0d149-123">Настройте другие необходимые свойства для компонента.</span><span class="sxs-lookup"><span data-stu-id="0d149-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="0d149-124">В следующем коде показано создание <xref:System.Windows.Forms.Timer> и установка его свойства `Interval`.</span><span class="sxs-lookup"><span data-stu-id="0d149-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0d149-125">Создание ссылки на вредоносный элемент `UserControl` может поставить локальный компьютер под угрозу атаки по сети.</span><span class="sxs-lookup"><span data-stu-id="0d149-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="0d149-126">Это может произойти только в том случае, если злоумышленник создаст небезопасный пользовательский элемент управления, а затем вы по ошибке добавите его в проект.</span><span class="sxs-lookup"><span data-stu-id="0d149-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d149-127">См. также</span><span class="sxs-lookup"><span data-stu-id="0d149-127">See also</span></span>

- [<span data-ttu-id="0d149-128">Элементы управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0d149-129">Практическое руководство. Добавление элементов управления в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="0d149-130">Практическое руководство. Добавление элементов управления ActiveX в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="0d149-131">Размещение элементов управления в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="0d149-132">Создание меток и назначение сочетаний клавиш для элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="0d149-133">Элементы управления для использования в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="0d149-134">Функциональная классификация элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d149-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
