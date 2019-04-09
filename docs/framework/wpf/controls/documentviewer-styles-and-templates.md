---
title: Стили и шаблоны элемента DocumentViewer
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: 4e91a640b36e4793567c9e728fd71ec8ce596743
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158422"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="c6281-102">Стили и шаблоны элемента DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c6281-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="c6281-103">В этом разделе описываются стили и шаблоны для <xref:System.Windows.Controls.DocumentViewer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="c6281-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="c6281-104">Вы можете изменить значение по умолчанию <xref:System.Windows.Controls.ControlTemplate> предоставить уникальный внешний вид элемента управления.</span><span class="sxs-lookup"><span data-stu-id="c6281-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c6281-105">Подробнее см. в разделе [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c6281-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="c6281-106">Части DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c6281-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="c6281-107">В следующей таблице перечислены именованные части <xref:System.Windows.Controls.DocumentViewer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="c6281-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="c6281-108">Отделение</span><span class="sxs-lookup"><span data-stu-id="c6281-108">Part</span></span>|<span data-ttu-id="c6281-109">Тип</span><span class="sxs-lookup"><span data-stu-id="c6281-109">Type</span></span>|<span data-ttu-id="c6281-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c6281-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c6281-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="c6281-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="c6281-112">Содержимое и область прокрутки.</span><span class="sxs-lookup"><span data-stu-id="c6281-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="c6281-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="c6281-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="c6281-114">Поле поиска в нижней по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c6281-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="c6281-115">Состояния DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c6281-115">DocumentViewer States</span></span>  
 <span data-ttu-id="c6281-116">В следующей таблице перечислены визуальные состояния <xref:System.Windows.Controls.DocumentViewer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="c6281-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="c6281-117">Имя VisualState</span><span class="sxs-lookup"><span data-stu-id="c6281-117">VisualState Name</span></span>|<span data-ttu-id="c6281-118">Имя VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c6281-118">VisualStateGroup Name</span></span>|<span data-ttu-id="c6281-119">Описание</span><span class="sxs-lookup"><span data-stu-id="c6281-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c6281-120">Valid</span><span class="sxs-lookup"><span data-stu-id="c6281-120">Valid</span></span>|<span data-ttu-id="c6281-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c6281-121">ValidationStates</span></span>|<span data-ttu-id="c6281-122">Элемент управления использует <xref:System.Windows.Controls.Validation> класс и <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> присоединенное свойство `false`.</span><span class="sxs-lookup"><span data-stu-id="c6281-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c6281-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c6281-123">InvalidFocused</span></span>|<span data-ttu-id="c6281-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c6281-124">ValidationStates</span></span>|<span data-ttu-id="c6281-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления имеет фокус.</span><span class="sxs-lookup"><span data-stu-id="c6281-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c6281-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c6281-126">InvalidUnfocused</span></span>|<span data-ttu-id="c6281-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c6281-127">ValidationStates</span></span>|<span data-ttu-id="c6281-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Присоединенное свойство `true` имеет элемент управления не имеет фокуса.</span><span class="sxs-lookup"><span data-stu-id="c6281-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="c6281-129">Пример шаблона элемента управления DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="c6281-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="c6281-130">В следующем примере показано определение <xref:System.Windows.Controls.ControlTemplate> для <xref:System.Windows.Controls.DocumentViewer> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="c6281-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="c6281-131">В предыдущем примере используется один или несколько из следующих ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c6281-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c6281-132">Полный пример см. в разделе [Пример задания стиля с помощью ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c6281-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6281-133">См. также</span><span class="sxs-lookup"><span data-stu-id="c6281-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c6281-134">Стили и шаблоны элемента Control</span><span class="sxs-lookup"><span data-stu-id="c6281-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c6281-135">Настройка элементов управления</span><span class="sxs-lookup"><span data-stu-id="c6281-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c6281-136">Стилизация и использование шаблонов</span><span class="sxs-lookup"><span data-stu-id="c6281-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="c6281-137">Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c6281-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
