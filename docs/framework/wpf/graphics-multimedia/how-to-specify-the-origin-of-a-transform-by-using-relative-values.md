---
title: Практическое руководство. Определение источника преобразования с помощью относительных значений
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 48b3b0df8dab8516873495a996074eae57ffe00f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651146"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="d6d76-102">Практическое руководство. Определение источника преобразования с помощью относительных значений</span><span class="sxs-lookup"><span data-stu-id="d6d76-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="d6d76-103">В этом примере показано, как использовать относительные значения для указания источника <xref:System.Windows.UIElement.RenderTransform%2A> , применяемый к <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="d6d76-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="d6d76-104">При повороте, масштабирование или наклон <xref:System.Windows.FrameworkElement> с помощью <xref:System.Windows.UIElement.RenderTransform%2A> свойство, значение по умолчанию применяет преобразование в верхний левый угол элемента.</span><span class="sxs-lookup"><span data-stu-id="d6d76-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="d6d76-105">Если требуется выполнить поворот, масштабирование или наклон в центре элемента, можно скорректировать действие, задав центр преобразования в центре элемента.</span><span class="sxs-lookup"><span data-stu-id="d6d76-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="d6d76-106">Но для этого способа требуется знание размера элемента.</span><span class="sxs-lookup"><span data-stu-id="d6d76-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="d6d76-107">Более простой способ применить преобразование к центру элемента является установка его <xref:System.Windows.UIElement.RenderTransformOrigin%2A> значение (0,5, 0,5), а не задавать значение центра преобразования.</span><span class="sxs-lookup"><span data-stu-id="d6d76-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6d76-108">Пример</span><span class="sxs-lookup"><span data-stu-id="d6d76-108">Example</span></span>  
 <span data-ttu-id="d6d76-109">В следующем примере используется <xref:System.Windows.Media.RotateTransform> для поворота <xref:System.Windows.Controls.Button> 45 градусов по часовой стрелке.</span><span class="sxs-lookup"><span data-stu-id="d6d76-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="d6d76-110">Так как в примере не задана центральная точка, то кнопка поворачивается вокруг точки (0, 0), т. е. левого верхнего угла.</span><span class="sxs-lookup"><span data-stu-id="d6d76-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="d6d76-111"><xref:System.Windows.Media.RotateTransform> Применяется к <xref:System.Windows.UIElement.RenderTransform%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="d6d76-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="d6d76-112">Ниже показан результат преобразования для следующего примера.</span><span class="sxs-lookup"><span data-stu-id="d6d76-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="d6d76-113">![Кнопка, преобразованная с использованием RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="d6d76-113">![A button transformed using RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="d6d76-114">Поворот по часовой стрелке на 45 градусов с использованием свойства RenderTransform</span><span class="sxs-lookup"><span data-stu-id="d6d76-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="d6d76-115">В следующем примере также используется <xref:System.Windows.Media.RotateTransform> для поворота <xref:System.Windows.Controls.Button> 45 градусов по часовой стрелке, однако в этом примере устанавливается <xref:System.Windows.UIElement.RenderTransformOrigin%2A> кнопки значение (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="d6d76-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="d6d76-116">В результате кнопка поворачивается вокруг центра, а не вокруг левого верхнего угла.</span><span class="sxs-lookup"><span data-stu-id="d6d76-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="d6d76-117">Ниже показан результат преобразования для следующего примера.</span><span class="sxs-lookup"><span data-stu-id="d6d76-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="d6d76-118">![Кнопка, преобразованная относительно ее центра](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="d6d76-118">![A button transformed about its center](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="d6d76-119">Поворот на 45 градусов с использованием свойства RenderTransform с заданным для RenderTransformOrigin значением (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="d6d76-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="d6d76-120">Дополнительные сведения о преобразовании <xref:System.Windows.FrameworkElement> объектов, см. в разделе [Общие сведения о преобразованиях](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d6d76-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d76-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d6d76-121">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="d6d76-122">Общие сведения о классах Transform</span><span class="sxs-lookup"><span data-stu-id="d6d76-122">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="d6d76-123">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="d6d76-123">How-to Topics</span></span>](transformations-how-to-topics.md)
