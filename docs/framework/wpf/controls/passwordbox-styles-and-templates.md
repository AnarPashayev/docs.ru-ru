---
title: Стили и шаблоны элемента PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770647"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="eea27-102">Стили и шаблоны элемента PasswordBox</span><span class="sxs-lookup"><span data-stu-id="eea27-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="eea27-103">В этом разделе описываются стили и шаблоны для <xref:System.Windows.Controls.PasswordBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="eea27-104">Вы можете изменить значение по умолчанию <xref:System.Windows.Controls.ControlTemplate> предоставить уникальный внешний вид элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="eea27-105">Подробнее см. в разделе [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="eea27-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="eea27-106">Части PasswordBox</span><span class="sxs-lookup"><span data-stu-id="eea27-106">PasswordBox Parts</span></span>

<span data-ttu-id="eea27-107">В следующей таблице перечислены именованные части <xref:System.Windows.Controls.PasswordBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="eea27-108">Отделение</span><span class="sxs-lookup"><span data-stu-id="eea27-108">Part</span></span>|<span data-ttu-id="eea27-109">Тип</span><span class="sxs-lookup"><span data-stu-id="eea27-109">Type</span></span>|<span data-ttu-id="eea27-110">Описание</span><span class="sxs-lookup"><span data-stu-id="eea27-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="eea27-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="eea27-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="eea27-112">Визуальный элемент, который может содержать <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="eea27-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="eea27-113">Текст <xref:System.Windows.Controls.PasswordBox> отображается в этом элементе.</span><span class="sxs-lookup"><span data-stu-id="eea27-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="eea27-114">Состояния PasswordBox</span><span class="sxs-lookup"><span data-stu-id="eea27-114">PasswordBox States</span></span>

<span data-ttu-id="eea27-115">В следующей таблице перечислены визуальные состояния <xref:System.Windows.Controls.PasswordBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="eea27-116">Имя VisualState</span><span class="sxs-lookup"><span data-stu-id="eea27-116">VisualState Name</span></span>|<span data-ttu-id="eea27-117">Имя VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="eea27-117">VisualStateGroup Name</span></span>|<span data-ttu-id="eea27-118">Описание</span><span class="sxs-lookup"><span data-stu-id="eea27-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="eea27-119">Норм.</span><span class="sxs-lookup"><span data-stu-id="eea27-119">Normal</span></span>|<span data-ttu-id="eea27-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eea27-120">CommonStates</span></span>|<span data-ttu-id="eea27-121">Состояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="eea27-121">The default state.</span></span>|
|<span data-ttu-id="eea27-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="eea27-122">MouseOver</span></span>|<span data-ttu-id="eea27-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eea27-123">CommonStates</span></span>|<span data-ttu-id="eea27-124">Указатель мыши расположен над элементом управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="eea27-125">Отключено</span><span class="sxs-lookup"><span data-stu-id="eea27-125">Disabled</span></span>|<span data-ttu-id="eea27-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eea27-126">CommonStates</span></span>|<span data-ttu-id="eea27-127">Элемент управления отключен.</span><span class="sxs-lookup"><span data-stu-id="eea27-127">The control is disabled.</span></span>|
|<span data-ttu-id="eea27-128">Focused</span><span class="sxs-lookup"><span data-stu-id="eea27-128">Focused</span></span>|<span data-ttu-id="eea27-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eea27-129">FocusStates</span></span>|<span data-ttu-id="eea27-130">Элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="eea27-130">The control has focus.</span></span>|
|<span data-ttu-id="eea27-131">Без фокуса ввода</span><span class="sxs-lookup"><span data-stu-id="eea27-131">Unfocused</span></span>|<span data-ttu-id="eea27-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eea27-132">FocusStates</span></span>|<span data-ttu-id="eea27-133">Элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="eea27-133">The control does not have focus.</span></span>|
|<span data-ttu-id="eea27-134">Valid</span><span class="sxs-lookup"><span data-stu-id="eea27-134">Valid</span></span>|<span data-ttu-id="eea27-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eea27-135">ValidationStates</span></span>|<span data-ttu-id="eea27-136">Элемент управления использует <xref:System.Windows.Controls.Validation> класс и <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> присоединенное свойство `false`.</span><span class="sxs-lookup"><span data-stu-id="eea27-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="eea27-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="eea27-137">InvalidFocused</span></span>|<span data-ttu-id="eea27-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eea27-138">ValidationStates</span></span>|<span data-ttu-id="eea27-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="eea27-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="eea27-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="eea27-140">InvalidUnfocused</span></span>|<span data-ttu-id="eea27-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eea27-141">ValidationStates</span></span>|<span data-ttu-id="eea27-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="eea27-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="eea27-143">Пример шаблона элемента управления PasswordBox</span><span class="sxs-lookup"><span data-stu-id="eea27-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="eea27-144">В следующем примере показано определение <xref:System.Windows.Controls.ControlTemplate> для <xref:System.Windows.Controls.PasswordBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="eea27-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="eea27-145">В предыдущем примере используется один или несколько из следующих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="eea27-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="eea27-146">Полный пример см. в разделе [Пример задания стиля с помощью ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="eea27-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="eea27-147">См. также</span><span class="sxs-lookup"><span data-stu-id="eea27-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="eea27-148">Стили и шаблоны элемента управления</span><span class="sxs-lookup"><span data-stu-id="eea27-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="eea27-149">Настройка элементов управления</span><span class="sxs-lookup"><span data-stu-id="eea27-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="eea27-150">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="eea27-150">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="eea27-151">Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="eea27-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
