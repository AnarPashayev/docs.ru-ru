---
title: Практическое руководство. Анимация типа Double с помощью ключевых кадров
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 73cbeab8aee566313bad8e8a18a5500374287de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010206"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="21e1a-102">Практическое руководство. Анимация типа Double с помощью ключевых кадров</span><span class="sxs-lookup"><span data-stu-id="21e1a-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="21e1a-103">В этом примере демонстрируется анимация значения свойства, которое принимает <xref:System.Double> с помощью ключевых кадров.</span><span class="sxs-lookup"><span data-stu-id="21e1a-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e1a-104">Пример</span><span class="sxs-lookup"><span data-stu-id="21e1a-104">Example</span></span>  
 <span data-ttu-id="21e1a-105">В следующем примере прямоугольник перемещается по экрану.</span><span class="sxs-lookup"><span data-stu-id="21e1a-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="21e1a-106">В примере используется <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> класс для анимации <xref:System.Windows.Media.TranslateTransform.X%2A> свойство <xref:System.Windows.Media.TranslateTransform> применяется к <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="21e1a-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="21e1a-107">Эта анимация, которая бесконечно повторяется, использует три ключевых кадра следующим образом:</span><span class="sxs-lookup"><span data-stu-id="21e1a-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="21e1a-108">В течение первых трех секунд используется экземпляр <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> класс для перемещения прямоугольника вдоль пути с постоянной скоростью из его начальной позиции в позицию 500.</span><span class="sxs-lookup"><span data-stu-id="21e1a-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="21e1a-109">Линейные ключевые кадры, например <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> создать плавный линейный переход между значениями.</span><span class="sxs-lookup"><span data-stu-id="21e1a-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="21e1a-110">В конце четвертой секунды используется экземпляр <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> класс для резкого перемещения прямоугольника в следующую позицию.</span><span class="sxs-lookup"><span data-stu-id="21e1a-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="21e1a-111">Дискретные ключевые кадры, например <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> , создают скачкообразные переходы между значениями.</span><span class="sxs-lookup"><span data-stu-id="21e1a-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="21e1a-112">В этом примере прямоугольник находится в начальной позиции, а затем внезапно появляется в позиции 500.</span><span class="sxs-lookup"><span data-stu-id="21e1a-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="21e1a-113">В последних двух секунд используется экземпляр <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> класс для перемещения прямоугольника обратно в исходное положение.</span><span class="sxs-lookup"><span data-stu-id="21e1a-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="21e1a-114">Ключевые кадры сплайна, например <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> , создают переменный переход между значениями согласно значению <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="21e1a-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="21e1a-115">В этом примере прямоугольник начинает двигаться медленно и ускоряется экспоненциально к концу временного отрезка.</span><span class="sxs-lookup"><span data-stu-id="21e1a-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="21e1a-116">Описание полного примера см. в разделе [Пример анимации по ключевым кадрам](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="21e1a-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="21e1a-117">Для обеспечения согласованности с другими примерами анимации версии кода этого примера используют <xref:System.Windows.Media.Animation.Storyboard> объекта для применения <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="21e1a-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="21e1a-118">Кроме того, при применении в коде одной анимации, проще использовать <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> метода вместо использования <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="21e1a-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="21e1a-119">Пример см. в разделе [Анимация свойства без использования раскадровки](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="21e1a-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e1a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="21e1a-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="21e1a-121">Общие сведения об анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="21e1a-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="21e1a-122">Практические руководства, посвященные анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="21e1a-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
