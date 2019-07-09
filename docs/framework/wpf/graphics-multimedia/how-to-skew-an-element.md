---
title: Практическое руководство. Наклон элемента
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664087"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="f2231-102">Практическое руководство. Наклон элемента</span><span class="sxs-lookup"><span data-stu-id="f2231-102">How to: Skew an Element</span></span>
<span data-ttu-id="f2231-103">В этом примере показано, как использовать <xref:System.Windows.Media.SkewTransform> для отклонения элемента.</span><span class="sxs-lookup"><span data-stu-id="f2231-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="f2231-104">Отклонение (или срез) — это преобразование, которое неравномерно растягивает пространство координат.</span><span class="sxs-lookup"><span data-stu-id="f2231-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="f2231-105">Одним из примеров использования <xref:System.Windows.Media.SkewTransform> является имитация трехмерной глубины в объектах 2-D.</span><span class="sxs-lookup"><span data-stu-id="f2231-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="f2231-106">Используйте <xref:System.Windows.Media.SkewTransform.CenterX%2A> и <xref:System.Windows.Media.SkewTransform.CenterY%2A> точка свойства для указания центра <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="f2231-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="f2231-107">Используйте <xref:System.Windows.Media.SkewTransform.AngleX%2A> и <xref:System.Windows.Media.SkewTransform.AngleY%2A> свойства для задания угла наклона осей x и y и отклонения текущей системы координат по этим осям.</span><span class="sxs-lookup"><span data-stu-id="f2231-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="f2231-108">Чтобы спрогнозировать результат наклона, обратите внимание на <xref:System.Windows.Media.SkewTransform.AngleX%2A> Наклоняет значений по оси x относительно исходной системы координат.</span><span class="sxs-lookup"><span data-stu-id="f2231-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="f2231-109">Таким образом, для <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, ось y поворачивается на 30 градусов через начало координат и Наклоняет значений в x-на 30 градусов от начала координат.</span><span class="sxs-lookup"><span data-stu-id="f2231-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="f2231-110">Аналогичным образом <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 наклон значений y фигуры на 30 градусов от начала координат.</span><span class="sxs-lookup"><span data-stu-id="f2231-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="f2231-111">Обратите внимание, что это не то же самое, что перенос (перемещение) системы координат на 30 градусов по осям X и Y.</span><span class="sxs-lookup"><span data-stu-id="f2231-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="f2231-112">В следующем примере применяется горизонтальное отклонение на 45 градусов <xref:System.Windows.Shapes.Rectangle> относительно центральной точки (0,0).</span><span class="sxs-lookup"><span data-stu-id="f2231-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2231-113">Пример</span><span class="sxs-lookup"><span data-stu-id="f2231-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="f2231-114">В следующем примере применяется горизонтальное отклонение на 45 градусов <xref:System.Windows.Shapes.Rectangle> относительно центральной точки (25, 25).</span><span class="sxs-lookup"><span data-stu-id="f2231-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="f2231-115">В следующем примере применяется вертикальное отклонение на 45 градусов <xref:System.Windows.Shapes.Rectangle> относительно центральной точки (25, 25).</span><span class="sxs-lookup"><span data-stu-id="f2231-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="f2231-116">На следующем рисунке показаны отклонения, использованные в этом примере.</span><span class="sxs-lookup"><span data-stu-id="f2231-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="f2231-117">![Примеры SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="f2231-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="f2231-118">Показаны три примера SkewTransform</span><span class="sxs-lookup"><span data-stu-id="f2231-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="f2231-119">Полный пример см. в разделе [Примеры двумерных преобразований](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="f2231-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2231-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f2231-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="f2231-121">Общие сведения о классах Transform</span><span class="sxs-lookup"><span data-stu-id="f2231-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="f2231-122">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="f2231-122">How-to Topics</span></span>](transformations-how-to-topics.md)
