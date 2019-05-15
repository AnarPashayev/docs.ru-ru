---
title: Пошаговое руководство. Применение стилей к содержимому WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: b689bb7299d541708db7ae786bff62a1007608e5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557892"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="4ef51-102">Пошаговое руководство. Стиль содержимого WPF</span><span class="sxs-lookup"><span data-stu-id="4ef51-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="4ef51-103">В этом пошаговом руководстве показано, как применить стили к элементу управления Windows Presentation Foundation (WPF), размещенному на форме Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4ef51-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="4ef51-104">В руководстве выполняются следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4ef51-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="4ef51-105">Создание проекта.</span><span class="sxs-lookup"><span data-stu-id="4ef51-105">Create the project.</span></span>

- <span data-ttu-id="4ef51-106">создание элемента управления WPF;</span><span class="sxs-lookup"><span data-stu-id="4ef51-106">Create the WPF control type.</span></span>

- <span data-ttu-id="4ef51-107">Применение стиля к WPF control.a</span><span class="sxs-lookup"><span data-stu-id="4ef51-107">Apply a style to the WPF control.a</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ef51-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4ef51-108">Prerequisites</span></span>

<span data-ttu-id="4ef51-109">Для выполнения шагов, описанных в этом руководстве, вам понадобится Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ef51-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="4ef51-110">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="4ef51-110">Create the project</span></span>

<span data-ttu-id="4ef51-111">Откройте Visual Studio и создайте новый проект приложения Windows Forms в Visual Basic или Visual C# с именем `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="4ef51-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="4ef51-112">При размещении содержимого WPF поддерживаются только проекты C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ef51-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="4ef51-113">Создание типов элемента управления WPF</span><span class="sxs-lookup"><span data-stu-id="4ef51-113">Create the WPF control types</span></span>

<span data-ttu-id="4ef51-114">После добавления в проект типа элемента управления WPF можно разместить его в элементе управления <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="4ef51-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="4ef51-115">Добавьте в решение новый проект WPF <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="4ef51-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="4ef51-116">Используйте имя по умолчанию для этого типа элемента управления (`UserControl1.xaml`).</span><span class="sxs-lookup"><span data-stu-id="4ef51-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="4ef51-117">Дополнительные сведения см. в разделе [Пошаговое руководство: Создание нового содержимого WPF в формах Windows Forms во время разработки](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="4ef51-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="4ef51-118">Убедитесь в том, что элемент `UserControl1` выбран в представлении конструирования.</span><span class="sxs-lookup"><span data-stu-id="4ef51-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="4ef51-119">Дополнительные сведения см. в разделе [Практическое руководство. Выберите и перемещать элементы в области конструктора](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4ef51-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="4ef51-120">В **свойства** окна, установите для параметра <xref:System.Windows.FrameworkElement.Width%2A> и <xref:System.Windows.FrameworkElement.Height%2A> свойства `200`.</span><span class="sxs-lookup"><span data-stu-id="4ef51-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="4ef51-121">Добавить <xref:System.Windows.Controls.Button?displayProperty=nameWithType> управления <xref:System.Windows.Controls.UserControl> и установите для параметра <xref:System.Windows.Controls.ContentControl.Content%2A> свойства **отменить**.</span><span class="sxs-lookup"><span data-stu-id="4ef51-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="4ef51-122">Добавьте второй <xref:System.Windows.Controls.Button?displayProperty=nameWithType> управления <xref:System.Windows.Controls.UserControl> и установите для параметра <xref:System.Windows.Controls.ContentControl.Content%2A> свойства **ОК**.</span><span class="sxs-lookup"><span data-stu-id="4ef51-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="4ef51-123">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="4ef51-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="4ef51-124">Применение стиля к элементу управления WPF</span><span class="sxs-lookup"><span data-stu-id="4ef51-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="4ef51-125">Для изменения внешнего вида и поведения элемента управления WPF к нему можно применить различные стили.</span><span class="sxs-lookup"><span data-stu-id="4ef51-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="4ef51-126">Откройте `Form1` в конструкторе Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4ef51-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="4ef51-127">В **элементов**, дважды щелкните `UserControl1` для создания экземпляра `UserControl1` в форме.</span><span class="sxs-lookup"><span data-stu-id="4ef51-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="4ef51-128">Экземпляр `UserControl1` размещается в новом элементе управления <xref:System.Windows.Forms.Integration.ElementHost> с именем `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="4ef51-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="4ef51-129">В панели смарт-тега для `elementHost1`, нажмите кнопку **редактировать содержимое** из раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="4ef51-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="4ef51-130">`UserControl1` откроется в [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ef51-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="4ef51-131">В представлении XAML вставьте следующий код XAML после открывающего тега `<UserControl>` .</span><span class="sxs-lookup"><span data-stu-id="4ef51-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="4ef51-132">Этот код XAML создает градиент с контрастной градиентной границей.</span><span class="sxs-lookup"><span data-stu-id="4ef51-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="4ef51-133">При нажатии на элемент управления градиенты изменяются, формируя образ нажатой кнопки.</span><span class="sxs-lookup"><span data-stu-id="4ef51-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="4ef51-134">Более подробную информацию см. в разделе [Стилизация и использование шаблонов](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="4ef51-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="4ef51-135">Примените стиль `SimpleButton`, определенный на предыдущем шаге, к кнопке "Отмена", вставив следующий код XAML в `<Button>` тег кнопки "Отмена".</span><span class="sxs-lookup"><span data-stu-id="4ef51-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="4ef51-136">Объявление кнопки будет напоминать следующий XAML:</span><span class="sxs-lookup"><span data-stu-id="4ef51-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="4ef51-137">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="4ef51-137">Build the project.</span></span>

1. <span data-ttu-id="4ef51-138">Откройте `Form1` в конструкторе Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4ef51-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="4ef51-139">Новый стиль применяется для элемента управления button.</span><span class="sxs-lookup"><span data-stu-id="4ef51-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="4ef51-140">Из **Отладка** меню, выберите **начать отладку** для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="4ef51-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="4ef51-141">Нажмите кнопки OK и Отмена и просмотрите  различия.</span><span class="sxs-lookup"><span data-stu-id="4ef51-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ef51-142">См. также</span><span class="sxs-lookup"><span data-stu-id="4ef51-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="4ef51-143">Миграция и взаимодействие систем</span><span class="sxs-lookup"><span data-stu-id="4ef51-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="4ef51-144">Использование элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="4ef51-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="4ef51-145">Проектирование XAML в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ef51-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="4ef51-146">Общие сведения о языке XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="4ef51-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="4ef51-147">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="4ef51-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
