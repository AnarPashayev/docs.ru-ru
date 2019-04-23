---
title: Практическое руководство. Анимация прямоугольника с помощью ключевых кадров
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311348"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="34d65-102">Практическое руководство. Анимация прямоугольника с помощью ключевых кадров</span><span class="sxs-lookup"><span data-stu-id="34d65-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="34d65-103">В этом примере демонстрируется анимация <xref:System.Windows.Media.RectangleGeometry.Rect%2A> свойство <xref:System.Windows.Media.RectangleGeometry> с помощью ключевых кадров.</span><span class="sxs-lookup"><span data-stu-id="34d65-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d65-104">Пример</span><span class="sxs-lookup"><span data-stu-id="34d65-104">Example</span></span>  
 <span data-ttu-id="34d65-105">В следующем примере используется <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> класс для анимации <xref:System.Windows.Media.RectangleGeometry.Rect%2A> свойство <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="34d65-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="34d65-106">Эта анимация использует три ключевых кадра следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34d65-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="34d65-107">В течение первых двух секунд используется экземпляр <xref:System.Windows.Media.Animation.LinearRectKeyFrame> класс для анимации к плавному изменению в позицию, ширину и высоту прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="34d65-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="34d65-108">Линейные ключевые кадры, например <xref:System.Windows.Media.Animation.LinearRectKeyFrame> создать плавный линейный переход между значениями.</span><span class="sxs-lookup"><span data-stu-id="34d65-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="34d65-109">В конце следующей половины секунды используется экземпляр <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> класс для резкого уменьшения высоты прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="34d65-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="34d65-110">Дискретные ключевые кадры, например <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> создают резкие изменения значений, то есть, уменьшение высоты происходит быстро и не плавно.</span><span class="sxs-lookup"><span data-stu-id="34d65-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="34d65-111">В течение последних двух секунд используется экземпляр <xref:System.Windows.Media.Animation.SplineRectKeyFrame> класс, чтобы изменить прямоугольника обратно на исходный размер и положение.</span><span class="sxs-lookup"><span data-stu-id="34d65-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="34d65-112">Ключевые кадры сплайна, например <xref:System.Windows.Media.Animation.SplineRectKeyFrame> , создают переменный переход между значениями в соответствии со значениями из <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="34d65-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="34d65-113">В этом примере изменение начинается медленно и ускоряется экспоненциально к концу временного сегмента.</span><span class="sxs-lookup"><span data-stu-id="34d65-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="34d65-114">Описание полного примера см. в разделе [Пример анимации по ключевым кадрам](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="34d65-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d65-115">См. также</span><span class="sxs-lookup"><span data-stu-id="34d65-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="34d65-116">Общие сведения об анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="34d65-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="34d65-117">Практические руководства, посвященные анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="34d65-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
