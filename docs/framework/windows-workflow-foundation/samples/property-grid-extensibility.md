---
title: Расширяемость сетки свойств - пример WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: f1cb64cb10e8d88359e8f94b57602ab127314cff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004878"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="172be-102">Расширяемость сетки свойств</span><span class="sxs-lookup"><span data-stu-id="172be-102">Property grid extensibility</span></span>

<span data-ttu-id="172be-103">Разработчик может настроить сетку свойств, которая будет отображаться при выборе в редакторе определенного действия.</span><span class="sxs-lookup"><span data-stu-id="172be-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="172be-104">Таким образом можно реализовать расширенные возможности редактирования.</span><span class="sxs-lookup"><span data-stu-id="172be-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="172be-105">Они показываются в данном образце.</span><span class="sxs-lookup"><span data-stu-id="172be-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="172be-106">Демонстрации</span><span class="sxs-lookup"><span data-stu-id="172be-106">Demonstrates</span></span>

<span data-ttu-id="172be-107">Расширяемость сетки свойств конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="172be-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="172be-108">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="172be-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="172be-109">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="172be-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="172be-110">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="172be-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="172be-111">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="172be-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="172be-112">Обсуждение</span><span class="sxs-lookup"><span data-stu-id="172be-112">Discussion</span></span>

<span data-ttu-id="172be-113">Чтобы расширить сетку свойств, разработчик может настроить встроенное представление редактора сетки свойств или реализовать диалоговое окно, которое будет отображать усовершенствованную область расширенного редактирования.</span><span class="sxs-lookup"><span data-stu-id="172be-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="172be-114">В этом образце демонстрируется работа двух разных редакторов: встроенного редактора и диалогового редактора.</span><span class="sxs-lookup"><span data-stu-id="172be-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="172be-115">Встроенный редактор</span><span class="sxs-lookup"><span data-stu-id="172be-115">Inline editor</span></span>

<span data-ttu-id="172be-116">В образце встроенного редактора показаны следующие действия.</span><span class="sxs-lookup"><span data-stu-id="172be-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="172be-117">Создает тип, производный от <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="172be-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="172be-118">В конструкторе <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> значение задается с помощью шаблона данных Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="172be-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="172be-119">Значение может быть привязано к XAML-шаблону, однако в этом образце для инициализации привязки данных используется код.</span><span class="sxs-lookup"><span data-stu-id="172be-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="172be-120">Шаблон данных имеет контекст данных значения <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> для элемента, отображаемого в сетке свойств.</span><span class="sxs-lookup"><span data-stu-id="172be-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="172be-121">Обратите внимание, что в приведенном ниже коде (файл CustomInlineEditor.cs) этот контекст привязывается к свойству `Value`.</span><span class="sxs-lookup"><span data-stu-id="172be-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="172be-122">Поскольку действие и конструктор находятся в одной сборке, регистрация атрибутов конструктора действий выполняется в статическом конструкторе самого действия, как показано в следующем примере из файла SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="172be-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="172be-123">редактор диалоговых окон</span><span class="sxs-lookup"><span data-stu-id="172be-123">Dialog editor</span></span>

<span data-ttu-id="172be-124">В образце диалогового редактора показаны следующие действия.</span><span class="sxs-lookup"><span data-stu-id="172be-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="172be-125">Создает тип, производный от <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="172be-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="172be-126">В конструкторе значение <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> задается при помощи шаблона данных [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="172be-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="172be-127">Значение может быть создано в XAML, однако в этом образце оно создается с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="172be-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="172be-128">Шаблон данных имеет контекст данных значения <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> для элемента, отображаемого в сетке свойств.</span><span class="sxs-lookup"><span data-stu-id="172be-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="172be-129">В следующем коде значение привязывается к свойству `Value`.</span><span class="sxs-lookup"><span data-stu-id="172be-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="172be-130">Важно также добавить кнопку <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> для обеспечения возможности вызова диалогового окна в файле FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="172be-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="172be-131">Переопределяет метод <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> в типе конструктора для управления отображением диалогового окна.</span><span class="sxs-lookup"><span data-stu-id="172be-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="172be-132">В этом образце показано базовое диалоговое окно <xref:System.Windows.Forms.FileDialog>.</span><span class="sxs-lookup"><span data-stu-id="172be-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="172be-133">Поскольку действие и конструктор находятся в одной сборке, регистрация атрибутов конструктора действий выполняется в статическом конструкторе самого действия, как показано в следующем примере из файла SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="172be-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="172be-134">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="172be-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="172be-135">Постройте решение и откройте файл Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="172be-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="172be-136">Перетащите **SimpleCodeActivity** из области элементов на холст конструктора.</span><span class="sxs-lookup"><span data-stu-id="172be-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="172be-137">Нажмите кнопку **SimpleCodeActivity** и откройте сетку свойств, где имеется элемент управления "ползунок" и элемент выбора файла.</span><span class="sxs-lookup"><span data-stu-id="172be-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="172be-138">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="172be-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="172be-139">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="172be-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="172be-140">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="172be-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="172be-141">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="172be-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`