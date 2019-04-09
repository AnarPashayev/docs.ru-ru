---
title: Стили и шаблоны элемента Slider
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 385a69ad2bd17ae4c51437245915109aad446bdf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103198"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="00b15-102">Стили и шаблоны элемента Slider</span><span class="sxs-lookup"><span data-stu-id="00b15-102">Slider Styles and Templates</span></span>
<span data-ttu-id="00b15-103">В этом разделе описываются стили и шаблоны для <xref:System.Windows.Controls.Slider> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="00b15-104">Вы можете изменить значение по умолчанию <xref:System.Windows.Controls.ControlTemplate> предоставить уникальный внешний вид элемента управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="00b15-105">Подробнее см. в разделе [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="00b15-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="00b15-106">Ползунок частей</span><span class="sxs-lookup"><span data-stu-id="00b15-106">Slider Parts</span></span>  
 <span data-ttu-id="00b15-107">В следующей таблице перечислены именованные части <xref:System.Windows.Controls.Slider> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="00b15-108">Отделение</span><span class="sxs-lookup"><span data-stu-id="00b15-108">Part</span></span>|<span data-ttu-id="00b15-109">Тип</span><span class="sxs-lookup"><span data-stu-id="00b15-109">Type</span></span>|<span data-ttu-id="00b15-110">Описание</span><span class="sxs-lookup"><span data-stu-id="00b15-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="00b15-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="00b15-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="00b15-112">Контейнер для элемента, который указывает положение <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="00b15-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="00b15-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="00b15-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="00b15-114">Элемент, отображаемый диапазон выбора вдоль <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="00b15-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="00b15-115">Диапазон выбора отображается только если <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> свойство `true`.</span><span class="sxs-lookup"><span data-stu-id="00b15-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="00b15-116">Состояния "ползунок"</span><span class="sxs-lookup"><span data-stu-id="00b15-116">Slider States</span></span>  
 <span data-ttu-id="00b15-117">В следующей таблице перечислены визуальные состояния <xref:System.Windows.Controls.Slider> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="00b15-118">Имя VisualState</span><span class="sxs-lookup"><span data-stu-id="00b15-118">VisualState Name</span></span>|<span data-ttu-id="00b15-119">Имя VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="00b15-119">VisualStateGroup Name</span></span>|<span data-ttu-id="00b15-120">Описание</span><span class="sxs-lookup"><span data-stu-id="00b15-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="00b15-121">Норм.</span><span class="sxs-lookup"><span data-stu-id="00b15-121">Normal</span></span>|<span data-ttu-id="00b15-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00b15-122">CommonStates</span></span>|<span data-ttu-id="00b15-123">Состояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="00b15-123">The default state.</span></span>|  
|<span data-ttu-id="00b15-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="00b15-124">MouseOver</span></span>|<span data-ttu-id="00b15-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00b15-125">CommonStates</span></span>|<span data-ttu-id="00b15-126">Указатель мыши расположен над элементом управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="00b15-127">Отключено</span><span class="sxs-lookup"><span data-stu-id="00b15-127">Disabled</span></span>|<span data-ttu-id="00b15-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00b15-128">CommonStates</span></span>|<span data-ttu-id="00b15-129">Элемент управления отключен.</span><span class="sxs-lookup"><span data-stu-id="00b15-129">The control is disabled.</span></span>|  
|<span data-ttu-id="00b15-130">Focused</span><span class="sxs-lookup"><span data-stu-id="00b15-130">Focused</span></span>|<span data-ttu-id="00b15-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="00b15-131">FocusStates</span></span>|<span data-ttu-id="00b15-132">Элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="00b15-132">The control has focus.</span></span>|  
|<span data-ttu-id="00b15-133">Без фокуса ввода</span><span class="sxs-lookup"><span data-stu-id="00b15-133">Unfocused</span></span>|<span data-ttu-id="00b15-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="00b15-134">FocusStates</span></span>|<span data-ttu-id="00b15-135">Элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="00b15-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="00b15-136">Valid</span><span class="sxs-lookup"><span data-stu-id="00b15-136">Valid</span></span>|<span data-ttu-id="00b15-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00b15-137">ValidationStates</span></span>|<span data-ttu-id="00b15-138">Элемент управления использует <xref:System.Windows.Controls.Validation> класс и <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> присоединенное свойство `false`.</span><span class="sxs-lookup"><span data-stu-id="00b15-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="00b15-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="00b15-139">InvalidFocused</span></span>|<span data-ttu-id="00b15-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00b15-140">ValidationStates</span></span>|<span data-ttu-id="00b15-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="00b15-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="00b15-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="00b15-142">InvalidUnfocused</span></span>|<span data-ttu-id="00b15-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00b15-143">ValidationStates</span></span>|<span data-ttu-id="00b15-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="00b15-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="00b15-145">Пример шаблона элемента управления "ползунок"</span><span class="sxs-lookup"><span data-stu-id="00b15-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="00b15-146">В следующем примере показано определение <xref:System.Windows.Controls.ControlTemplate> для <xref:System.Windows.Controls.Slider> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="00b15-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="00b15-147">В предыдущем примере используется один или несколько из следующих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="00b15-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="00b15-148">Полный пример см. в разделе [Пример задания стиля с помощью ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="00b15-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b15-149">См. также</span><span class="sxs-lookup"><span data-stu-id="00b15-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="00b15-150">Стили и шаблоны элемента Control</span><span class="sxs-lookup"><span data-stu-id="00b15-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="00b15-151">Настройка элементов управления</span><span class="sxs-lookup"><span data-stu-id="00b15-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="00b15-152">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="00b15-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="00b15-153">Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="00b15-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
