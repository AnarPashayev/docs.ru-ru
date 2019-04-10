---
title: Пошаговое руководство. Применение стилей к содержимому WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 887a157494c2992c1ae5868229c442f31fafb276
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312154"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="6c3f2-102">Пошаговое руководство. Применение стилей к содержимому WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="6c3f2-103">В этом пошаговом руководстве показано, как применить стили к элементу управления Windows Presentation Foundation (WPF), размещенному на форме Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="6c3f2-104">В руководстве выполняются следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="6c3f2-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="6c3f2-105">Создание проекта.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-105">Create the project.</span></span>

-   <span data-ttu-id="6c3f2-106">создание элемента управления WPF;</span><span class="sxs-lookup"><span data-stu-id="6c3f2-106">Create the WPF control type.</span></span>

-   <span data-ttu-id="6c3f2-107">применение стиля к элементу управления WPF.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-107">Apply a style to the WPF control.</span></span>

> [!NOTE]
>  <span data-ttu-id="6c3f2-108">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6c3f2-109">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="6c3f2-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6c3f2-110">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="6c3f2-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c3f2-111">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6c3f2-111">Prerequisites</span></span>  
 <span data-ttu-id="6c3f2-112">Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-112">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="6c3f2-113">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-113">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6c3f2-114">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="6c3f2-114">Creating the Project</span></span>  
 <span data-ttu-id="6c3f2-115">Первым шагом является создание проекта Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c3f2-116">При размещении содержимого WPF поддерживаются только проекты C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6c3f2-117">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="6c3f2-117">To create the project</span></span>  
  
-   <span data-ttu-id="6c3f2-118">Создание нового проекта приложения Windows Forms в Visual Basic или Visual C# с именем `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="6c3f2-119">Создание типов элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="6c3f2-120">После добавления в проект типа элемента управления WPF можно разместить его в элементе управления <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="6c3f2-121">Создание типов элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-121">To create WPF control types</span></span>  
  
1. <span data-ttu-id="6c3f2-122">Добавьте в решение новый проект WPF <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="6c3f2-123">Используйте имя по умолчанию для этого типа элемента управления (`UserControl1.xaml`).</span><span class="sxs-lookup"><span data-stu-id="6c3f2-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6c3f2-124">Дополнительные сведения см. в разделе [Пошаговое руководство: Создание нового содержимого WPF в формах Windows Forms во время разработки](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6c3f2-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="6c3f2-125">Убедитесь в том, что элемент `UserControl1` выбран в представлении конструирования.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="6c3f2-126">Дополнительные сведения см. в разделе [Как Выберите и перемещать элементы в области конструктора](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6c3f2-126">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="6c3f2-127">В **свойства** окна, установите для параметра <xref:System.Windows.FrameworkElement.Width%2A> и <xref:System.Windows.FrameworkElement.Height%2A> свойства `200`.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="6c3f2-128">Добавить <xref:System.Windows.Controls.Button?displayProperty=nameWithType> управления <xref:System.Windows.Controls.UserControl> и установите для параметра <xref:System.Windows.Controls.ContentControl.Content%2A> свойства **отменить**.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5. <span data-ttu-id="6c3f2-129">Добавьте второй <xref:System.Windows.Controls.Button?displayProperty=nameWithType> управления <xref:System.Windows.Controls.UserControl> и установите для параметра <xref:System.Windows.Controls.ContentControl.Content%2A> свойства **ОК**.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6. <span data-ttu-id="6c3f2-130">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="6c3f2-131">Применение стиля к элементу управления WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="6c3f2-132">Для изменения внешнего вида и поведения элемента управления WPF к нему можно применить различные стили.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="6c3f2-133">Применение стиля к элементу управления WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-133">To apply a style to a WPF control</span></span>  
  
1. <span data-ttu-id="6c3f2-134">Откройте `Form1` в конструкторе Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="6c3f2-135">В **элементов**, дважды щелкните `UserControl1` для создания экземпляра `UserControl1` в форме.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="6c3f2-136">Экземпляр `UserControl1` размещается в новом элементе управления <xref:System.Windows.Forms.Integration.ElementHost> с именем `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3. <span data-ttu-id="6c3f2-137">В панели смарт-тега для `elementHost1`, нажмите кнопку **редактировать содержимое** из раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     `UserControl1` <span data-ttu-id="6c3f2-138">Открывает в [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c3f2-138">opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="6c3f2-139">В представлении XAML вставьте следующий код XAML после открывающего тега `<UserControl>` .</span><span class="sxs-lookup"><span data-stu-id="6c3f2-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="6c3f2-140">Этот код XAML создает градиент с контрастной градиентной границей.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="6c3f2-141">При нажатии на элемент управления градиенты изменяются, формируя образ нажатой кнопки.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="6c3f2-142">Более подробную информацию см. в разделе [Стилизация и использование шаблонов](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="6c3f2-142">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1. <span data-ttu-id="6c3f2-143">Примените стиль `SimpleButton`, определенный на предыдущем шаге, к кнопке "Отмена", вставив следующий код XAML в `<Button>` тег кнопки "Отмена".</span><span class="sxs-lookup"><span data-stu-id="6c3f2-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="6c3f2-144">Объявление кнопки будет выглядеть так, как в XAML ниже.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1. <span data-ttu-id="6c3f2-145">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-145">Build the project.</span></span>  
  
2. <span data-ttu-id="6c3f2-146">Откройте `Form1` в конструкторе Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3. <span data-ttu-id="6c3f2-147">Новый стиль применяется для элемента управления button.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-147">The new style is applied to the button control.</span></span>  
  
4. <span data-ttu-id="6c3f2-148">Из **Отладка** меню, выберите **начать отладку** для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5. <span data-ttu-id="6c3f2-149">Нажмите кнопки OK и Отмена и просмотрите  различия.</span><span class="sxs-lookup"><span data-stu-id="6c3f2-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3f2-150">См. также</span><span class="sxs-lookup"><span data-stu-id="6c3f2-150">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6c3f2-151">Миграция и взаимодействие систем</span><span class="sxs-lookup"><span data-stu-id="6c3f2-151">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="6c3f2-152">Использование элементов управления WPF</span><span class="sxs-lookup"><span data-stu-id="6c3f2-152">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="6c3f2-153">Проектирование XAML в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c3f2-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="6c3f2-154">Обзор XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="6c3f2-154">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="6c3f2-155">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="6c3f2-155">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
