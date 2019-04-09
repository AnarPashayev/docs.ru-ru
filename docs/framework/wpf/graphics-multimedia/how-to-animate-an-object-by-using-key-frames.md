---
title: Практическое руководство. Анимация объекта с помощью ключевых кадров
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0b2b517410c6cbc4f3deca13e5948c8de583fd3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177805"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="f1fab-102">Практическое руководство. Анимация объекта с помощью ключевых кадров</span><span class="sxs-lookup"><span data-stu-id="f1fab-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="f1fab-103">В этом примере показано, как анимировать объект, который в этом примере является <xref:System.Windows.Controls.Page.Background%2A> свойство <xref:System.Windows.Controls.Page> элемента управления, с помощью ключевых кадров.</span><span class="sxs-lookup"><span data-stu-id="f1fab-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1fab-104">Пример</span><span class="sxs-lookup"><span data-stu-id="f1fab-104">Example</span></span>  
 <span data-ttu-id="f1fab-105">В следующем примере используется <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> изменения в класс анимация цвета <xref:System.Windows.Controls.Page.Background%2A> свойство <xref:System.Windows.Controls.Page> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="f1fab-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="f1fab-106">Пример изменяется цвет кисти фона с регулярными интервалами.</span><span class="sxs-lookup"><span data-stu-id="f1fab-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="f1fab-107">Эта анимация использует <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> класс, чтобы создать три различных ключевых кадров.</span><span class="sxs-lookup"><span data-stu-id="f1fab-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="f1fab-108">Анимация использует ключевых кадра следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f1fab-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="f1fab-109">В конце первой секунды, анимирует экземпляр <xref:System.Windows.Media.LinearGradientBrush> класса.</span><span class="sxs-lookup"><span data-stu-id="f1fab-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="f1fab-110">В этом разделе примере применяется линейный градиент к цвету фона, таким образом, чтобы переход цвета с желтого на оранжевый, красный.</span><span class="sxs-lookup"><span data-stu-id="f1fab-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="f1fab-111">В конце следующей секунды, анимирует экземпляр <xref:System.Windows.Media.RadialGradientBrush> класса.</span><span class="sxs-lookup"><span data-stu-id="f1fab-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="f1fab-112">Этот раздел примера относится радиального градиента к цвет фона, определяющий цвет переход от белого к синему на черный.</span><span class="sxs-lookup"><span data-stu-id="f1fab-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="f1fab-113">В конце третьей секунды, анимирует экземпляр <xref:System.Windows.Media.DrawingBrush> класса.</span><span class="sxs-lookup"><span data-stu-id="f1fab-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="f1fab-114">В этом разделе примере применяется шахматной в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="f1fab-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="f1fab-115">Анимация начинается снова и повторяется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="f1fab-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> <span data-ttu-id="f1fab-116">Это единственный тип ключевого кадра, который можно использовать с <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> класса.</span><span class="sxs-lookup"><span data-stu-id="f1fab-116">is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="f1fab-117">Опорные кадры, например <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> , создают резкие изменения значений, то есть, изменения цвета в этом примере происходит внезапное.</span><span class="sxs-lookup"><span data-stu-id="f1fab-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f1fab-118">Описание полного примера см. в разделе [Пример анимации по ключевым кадрам](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="f1fab-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fab-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f1fab-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="f1fab-120">Общие сведения об анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="f1fab-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="f1fab-121">Практические руководства, посвященные анимации по ключевым кадрам</span><span class="sxs-lookup"><span data-stu-id="f1fab-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
