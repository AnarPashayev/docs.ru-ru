---
title: Стили и шаблоны элемента ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: 1cbb8d54a544b70b4a484c06c6bb2e9ca25029da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156329"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="35dec-102">Стили и шаблоны элемента ToolBar</span><span class="sxs-lookup"><span data-stu-id="35dec-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="35dec-103">В этом разделе описываются стили и шаблоны для <xref:System.Windows.Controls.ToolBar> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="35dec-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="35dec-104">Вы можете изменить значение по умолчанию <xref:System.Windows.Controls.ControlTemplate> предоставить уникальный внешний вид элемента управления.</span><span class="sxs-lookup"><span data-stu-id="35dec-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="35dec-105">Подробнее см. в разделе [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="35dec-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="35dec-106">Части панели инструментов</span><span class="sxs-lookup"><span data-stu-id="35dec-106">ToolBar Parts</span></span>  
 <span data-ttu-id="35dec-107">В следующей таблице перечислены именованные части <xref:System.Windows.Controls.ToolBar> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="35dec-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="35dec-108">Отделение</span><span class="sxs-lookup"><span data-stu-id="35dec-108">Part</span></span>|<span data-ttu-id="35dec-109">Тип</span><span class="sxs-lookup"><span data-stu-id="35dec-109">Type</span></span>|<span data-ttu-id="35dec-110">Описание</span><span class="sxs-lookup"><span data-stu-id="35dec-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="35dec-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="35dec-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="35dec-112">Объект, содержащий элементы управления на <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="35dec-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="35dec-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="35dec-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="35dec-114">Объект, содержащий элементы, находящиеся в области переполнения <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="35dec-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="35dec-115">При создании <xref:System.Windows.Controls.ControlTemplate> для <xref:System.Windows.Controls.ToolBar>, шаблон может содержать <xref:System.Windows.Controls.ItemsPresenter> в <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="35dec-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="35dec-116">( <xref:System.Windows.Controls.ItemsPresenter> Отображает каждый элемент в <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> дает возможность прокрутки в элементе управления).</span><span class="sxs-lookup"><span data-stu-id="35dec-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="35dec-117">Если <xref:System.Windows.Controls.ItemsPresenter> не является прямым потомком <xref:System.Windows.Controls.ScrollViewer>, необходимо предоставить <xref:System.Windows.Controls.ItemsPresenter> имя `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="35dec-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="35dec-118">Состояния панели инструментов</span><span class="sxs-lookup"><span data-stu-id="35dec-118">ToolBar States</span></span>  
 <span data-ttu-id="35dec-119">В следующей таблице перечислены визуальные состояния <xref:System.Windows.Controls.ToolBar> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="35dec-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="35dec-120">Имя VisualState</span><span class="sxs-lookup"><span data-stu-id="35dec-120">VisualState Name</span></span>|<span data-ttu-id="35dec-121">Имя VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="35dec-121">VisualStateGroup Name</span></span>|<span data-ttu-id="35dec-122">Описание</span><span class="sxs-lookup"><span data-stu-id="35dec-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="35dec-123">Valid</span><span class="sxs-lookup"><span data-stu-id="35dec-123">Valid</span></span>|<span data-ttu-id="35dec-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35dec-124">ValidationStates</span></span>|<span data-ttu-id="35dec-125">Элемент управления использует <xref:System.Windows.Controls.Validation> класс и <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> присоединенное свойство `false`.</span><span class="sxs-lookup"><span data-stu-id="35dec-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="35dec-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="35dec-126">InvalidFocused</span></span>|<span data-ttu-id="35dec-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35dec-127">ValidationStates</span></span>|<span data-ttu-id="35dec-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="35dec-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="35dec-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="35dec-129">InvalidUnfocused</span></span>|<span data-ttu-id="35dec-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35dec-130">ValidationStates</span></span>|<span data-ttu-id="35dec-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="35dec-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="35dec-132">Пример шаблона элемента управления панели инструментов</span><span class="sxs-lookup"><span data-stu-id="35dec-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="35dec-133">В следующем примере показано определение <xref:System.Windows.Controls.ControlTemplate> для <xref:System.Windows.Controls.ToolBar> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="35dec-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="35dec-134">В предыдущем примере используется один или несколько из следующих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="35dec-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="35dec-135">Полный пример см. в разделе [Пример задания стиля с помощью ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="35dec-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35dec-136">См. также</span><span class="sxs-lookup"><span data-stu-id="35dec-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="35dec-137">Стили и шаблоны элемента Control</span><span class="sxs-lookup"><span data-stu-id="35dec-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="35dec-138">Настройка элементов управления</span><span class="sxs-lookup"><span data-stu-id="35dec-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="35dec-139">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="35dec-139">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="35dec-140">Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="35dec-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
