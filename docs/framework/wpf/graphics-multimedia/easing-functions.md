---
title: Функции плавности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763142"
---
# <a name="easing-functions"></a><span data-ttu-id="29ce5-102">Функции плавности</span><span class="sxs-lookup"><span data-stu-id="29ce5-102">Easing Functions</span></span>
<span data-ttu-id="29ce5-103">Функции плавности позволяют применять к анимациям настраиваемые математические формулы.</span><span class="sxs-lookup"><span data-stu-id="29ce5-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="29ce5-104">Например, требуется реалистичный отскок объекта или его поведение так, словно он подвешен на пружине.</span><span class="sxs-lookup"><span data-stu-id="29ce5-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="29ce5-105">Для приблизительного воспроизведения этих эффектов можно использовать анимацию по ключевым кадрам или даже анимацию From/To/By, но это потребует значительного объема работы, и анимация будет менее точна, чем при использовании математических формул.</span><span class="sxs-lookup"><span data-stu-id="29ce5-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="29ce5-106">Помимо создания собственной функции плавности путем наследования от <xref:System.Windows.Media.Animation.EasingFunctionBase>, можно использовать один из функций плавности, предоставляемых средой выполнения для создания распространенных эффектов.</span><span class="sxs-lookup"><span data-stu-id="29ce5-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="29ce5-107"><xref:System.Windows.Media.Animation.BackEase>: Возвращающую движение анимации немного, прежде чем она начнет выполняться по заданному пути.</span><span class="sxs-lookup"><span data-stu-id="29ce5-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="29ce5-108"><xref:System.Windows.Media.Animation.BounceEase>: Создает эффект отскока.</span><span class="sxs-lookup"><span data-stu-id="29ce5-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="29ce5-109"><xref:System.Windows.Media.Animation.CircleEase>: Создает анимацию, которая ускоряется и замедляется с помощью тригонометрической функции.</span><span class="sxs-lookup"><span data-stu-id="29ce5-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="29ce5-110"><xref:System.Windows.Media.Animation.CubicEase>: Создает анимацию, которая ускоряется и/или замедляется по формуле *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="29ce5-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="29ce5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Создает анимацию, которая напоминает пружину, и обратно до до полного успокоения.</span><span class="sxs-lookup"><span data-stu-id="29ce5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="29ce5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Создает анимацию, которая ускоряется и замедляется с помощью экспоненциальной формулы.</span><span class="sxs-lookup"><span data-stu-id="29ce5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="29ce5-113"><xref:System.Windows.Media.Animation.PowerEase>: Создает анимацию, которая ускоряется и/или замедляется по формуле *f*(*t*) = *t*<sup>p</sup> где p равно значению <xref:System.Windows.Media.Animation.PowerEase.Power%2A>свойство.</span><span class="sxs-lookup"><span data-stu-id="29ce5-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="29ce5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Создает анимацию, которая ускоряется и/или замедляется по формуле *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="29ce5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="29ce5-115"><xref:System.Windows.Media.Animation.QuarticEase>: Создает анимацию, которая ускоряется и/или замедляется по формуле *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="29ce5-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="29ce5-116"><xref:System.Windows.Media.Animation.QuinticEase>: Создать анимацию, которая ускоряется и/или замедляется по формуле *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="29ce5-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="29ce5-117"><xref:System.Windows.Media.Animation.SineEase>: Создает анимацию, которая ускоряется и/или замедляется по формуле синуса.</span><span class="sxs-lookup"><span data-stu-id="29ce5-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="29ce5-118">Для применения функции плавности к анимации, используйте `EasingFunction` свойства анимации указания функции плавности для применения к анимации.</span><span class="sxs-lookup"><span data-stu-id="29ce5-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="29ce5-119">В следующем примере применяется <xref:System.Windows.Media.Animation.BounceEase> функцию для реалистичной анимации <xref:System.Windows.Media.Animation.DoubleAnimation> для создания эффекта отскока.</span><span class="sxs-lookup"><span data-stu-id="29ce5-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="29ce5-120">В предыдущем примере функция плавности применялась к анимации From/To/By.</span><span class="sxs-lookup"><span data-stu-id="29ce5-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="29ce5-121">Эти функции плавности можно применять и к анимации по ключевым кадрам.</span><span class="sxs-lookup"><span data-stu-id="29ce5-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="29ce5-122">В следующем примере показано, как использовать ключевые кадры с функциями плавности для создания анимации прямоугольника, который сокращается вверх, замедляется вниз, затем расширяется вниз (как будто падает), а затем подпрыгивает до остановки.</span><span class="sxs-lookup"><span data-stu-id="29ce5-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="29ce5-123">Можно использовать <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> свойство для изменения, как функция плавности ведет себя, то есть изменить способ интерполяции анимации.</span><span class="sxs-lookup"><span data-stu-id="29ce5-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="29ce5-124">Существует три возможных значения, можно задать для <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="29ce5-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="29ce5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Интерполяция следует математической формуле, связанной с функцией плавности.</span><span class="sxs-lookup"><span data-stu-id="29ce5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="29ce5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Интерполяция следует 100-процентную интерполяцию за вычетом выходного значения формулы, связанной с функцией плавности.</span><span class="sxs-lookup"><span data-stu-id="29ce5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="29ce5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Интерполяция использует <xref:System.Windows.Media.Animation.EasingMode.EaseIn> для первой половины анимации и <xref:System.Windows.Media.Animation.EasingMode.EaseOut> во второй половине.</span><span class="sxs-lookup"><span data-stu-id="29ce5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="29ce5-128">На следующих диаграммах показаны различные значения <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> где *f*(*x*) обозначает ход анимации и *t* представляет время.</span><span class="sxs-lookup"><span data-stu-id="29ce5-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="29ce5-129">![Схемы BackEase EasingMode.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="29ce5-130">![Схемы BounceEase EasingMode.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="29ce5-131">![Схемы CircleEase EasingMode.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="29ce5-132">![Схемы CubicEase EasingMode.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="29ce5-133">![Схемы ElasticEase для различных значений EasingMode.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="29ce5-134">![Схемы ExponentialEase для различных значений EasingMode.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="29ce5-135">![Схемы QuarticEase для различных значений EasingMode.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="29ce5-136">![Схемы QuadraticEase для различных значений EasingMode.](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="29ce5-137">![Схемы QuarticEase для различных значений EasingMode.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="29ce5-138">![Схемы QuinticEase для различных значений EasingMode.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="29ce5-139">![Схемы SineEase для различных значений EasingMode.](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="29ce5-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29ce5-140">Можно использовать <xref:System.Windows.Media.Animation.PowerEase> создать то же поведение, что <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, и <xref:System.Windows.Media.Animation.QuinticEase> с помощью <xref:System.Windows.Media.Animation.PowerEase.Power%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="29ce5-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="29ce5-141">Например, если вы хотите использовать <xref:System.Windows.Media.Animation.PowerEase> для замены <xref:System.Windows.Media.Animation.CubicEase>, укажите <xref:System.Windows.Media.Animation.PowerEase.Power%2A> значение 3.</span><span class="sxs-lookup"><span data-stu-id="29ce5-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="29ce5-142">Помимо использования функций плавности, входящих в среду выполнения, можно создать собственные функции плавности путем наследования от <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="29ce5-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="29ce5-143">В следующем примере показано создание простой пользовательской функции плавности.</span><span class="sxs-lookup"><span data-stu-id="29ce5-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="29ce5-144">Можно добавить свою собственную математическую логику для поведение функции плавности путем переопределения <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="29ce5-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
