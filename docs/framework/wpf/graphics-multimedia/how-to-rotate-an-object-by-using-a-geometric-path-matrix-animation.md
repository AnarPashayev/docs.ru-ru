---
title: Практическое руководство. Поворот объекта с использованием геометрического пути (матрица анимации)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 8f1b0ac42ea7509f8bc22b0bd2f50e2f96b5bee5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087890"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="4f491-102">Практическое руководство. Поворот объекта с использованием геометрического пути (матрица анимации)</span><span class="sxs-lookup"><span data-stu-id="4f491-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="4f491-103">В этом примере показано, как использовать <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> и <xref:System.Windows.Media.MatrixTransform> для поворота (вращения) объекта вдоль геометрического пути, определенного <xref:System.Windows.Media.PathGeometry> объекта.</span><span class="sxs-lookup"><span data-stu-id="4f491-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f491-104">Пример</span><span class="sxs-lookup"><span data-stu-id="4f491-104">Example</span></span>  
 <span data-ttu-id="4f491-105">В следующем примере используется <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> анимируемого объекта <xref:System.Windows.Media.MatrixTransform.Matrix%2A> свойство <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="4f491-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="4f491-106"><xref:System.Windows.Media.MatrixTransform> Применяется к кнопке и приводит к перемещению вдоль изогнутого пути.</span><span class="sxs-lookup"><span data-stu-id="4f491-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="4f491-107">Так как <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> свойству `true`, прямоугольник поворачивается по касательной к пути.</span><span class="sxs-lookup"><span data-stu-id="4f491-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="4f491-108">Полный пример см. в разделе [Пример анимации вдоль пути](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="4f491-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="4f491-109">В версии кода в предыдущем примере используется <xref:System.Windows.Media.Animation.Storyboard> для анимации <xref:System.Windows.Media.EllipseGeometry>, несмотря на то, что была применена всего одна анимация.</span><span class="sxs-lookup"><span data-stu-id="4f491-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="4f491-110">Более простой способ применения одной анимации к свойству в коде является использование <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="4f491-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="4f491-111">Пример см. в разделе [Анимация свойства без использования раскадровки](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="4f491-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f491-112">См. также</span><span class="sxs-lookup"><span data-stu-id="4f491-112">See also</span></span>

- [<span data-ttu-id="4f491-113">Общие сведения об эффектах анимации</span><span class="sxs-lookup"><span data-stu-id="4f491-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4f491-114">Практические руководства, посвященные анимации пути</span><span class="sxs-lookup"><span data-stu-id="4f491-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="4f491-115">Пример анимации вдоль пути</span><span class="sxs-lookup"><span data-stu-id="4f491-115">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
