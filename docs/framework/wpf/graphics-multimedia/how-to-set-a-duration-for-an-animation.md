---
title: Практическое руководство. Определение длительности анимации
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651159"
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="a1e37-102">Практическое руководство. Определение длительности анимации</span><span class="sxs-lookup"><span data-stu-id="a1e37-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="a1e37-103">Объект <xref:System.Windows.Media.Animation.Timeline> представляет сегмент времени и длина этого сегмента определяется временной шкалы <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="a1e37-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="a1e37-104">Когда <xref:System.Windows.Media.Animation.Timeline> достигает окончания своей длительности, воспроизведение прекращается.</span><span class="sxs-lookup"><span data-stu-id="a1e37-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="a1e37-105">Если <xref:System.Windows.Media.Animation.Timeline> имеет дочерние временные шкалы, их воспроизведение также останавливается.</span><span class="sxs-lookup"><span data-stu-id="a1e37-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="a1e37-106">В случае анимации <xref:System.Windows.Duration> указывает, сколько требуется для анимации перехода от начального к конечному значению.</span><span class="sxs-lookup"><span data-stu-id="a1e37-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="a1e37-107">Можно указать <xref:System.Windows.Duration> с определенным, ограниченным временем или специальных значений <xref:System.Windows.Duration.Automatic%2A> или <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1e37-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="a1e37-108">Длительность анимации должна включать значение времени, так как анимации всегда должны иметь определенную, ограниченную длину — в противном случае анимации не известно, как выполнять переход между значениями.</span><span class="sxs-lookup"><span data-stu-id="a1e37-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="a1e37-109">Временные шкалы контейнера (<xref:System.Windows.Media.Animation.TimelineGroup> объекты), такие как <xref:System.Windows.Media.Animation.Storyboard> и <xref:System.Windows.Media.Animation.ParallelTimeline>, имеют по умолчанию продолжительность <xref:System.Windows.Duration.Automatic%2A>, то есть они автоматически завершаются после последнего дочернего останавливает воспроизведение.</span><span class="sxs-lookup"><span data-stu-id="a1e37-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="a1e37-110">В следующем примере, ширину, высоту и заливки цвет <xref:System.Windows.Shapes.Rectangle> анимируется.</span><span class="sxs-lookup"><span data-stu-id="a1e37-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="a1e37-111">Длительность, установленная для временных шкал анимации и контейнер, приводит к эффекты анимации, включая управление скоростью анимации и переопределение продолжительность дочерних шкал времени длительностью временной шкалы контейнера.</span><span class="sxs-lookup"><span data-stu-id="a1e37-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1e37-112">Пример</span><span class="sxs-lookup"><span data-stu-id="a1e37-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a1e37-113">См. также</span><span class="sxs-lookup"><span data-stu-id="a1e37-113">See also</span></span>

- <xref:System.Windows.Duration>
- [<span data-ttu-id="a1e37-114">Общие сведения об эффектах анимации</span><span class="sxs-lookup"><span data-stu-id="a1e37-114">Animation Overview</span></span>](animation-overview.md)
