---
title: Практическое руководство. Создание фигуры с помощью объекта PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: b0ab703596612524881ab892a1095b0f49cd1551
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159319"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="1a24c-102">Практическое руководство. Создание фигуры с помощью объекта PathGeometry</span><span class="sxs-lookup"><span data-stu-id="1a24c-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="1a24c-103">В этом примере демонстрируется создание фигуры с помощью <xref:System.Windows.Media.PathGeometry> класса.</span><span class="sxs-lookup"><span data-stu-id="1a24c-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="1a24c-104"><xref:System.Windows.Media.PathGeometry> объекты состоят из одного или нескольких <xref:System.Windows.Media.PathFigure> объектов, каждый из которых <xref:System.Windows.Media.PathFigure> представляет различные «рисунок» или фигуры.</span><span class="sxs-lookup"><span data-stu-id="1a24c-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="1a24c-105">Каждый <xref:System.Windows.Media.PathFigure> состоит из одного или нескольких <xref:System.Windows.Media.PathSegment> объектов, каждый из которых представляет переходную часть фигуры.</span><span class="sxs-lookup"><span data-stu-id="1a24c-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="1a24c-106">Типы сегментов включают <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, и <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="1a24c-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a24c-107">Пример</span><span class="sxs-lookup"><span data-stu-id="1a24c-107">Example</span></span>  
 <span data-ttu-id="1a24c-108">В следующем примере используется <xref:System.Windows.Media.PathGeometry> для образования треугольника.</span><span class="sxs-lookup"><span data-stu-id="1a24c-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="1a24c-109"><xref:System.Windows.Media.PathGeometry> Отображается с использованием <xref:System.Windows.Shapes.Path> элемент.</span><span class="sxs-lookup"><span data-stu-id="1a24c-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="1a24c-110">На следующем рисунке показана фигура, созданная в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="1a24c-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="1a24c-111">![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="1a24c-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="1a24c-112">Треугольник, созданных с помощью PathGeometry</span><span class="sxs-lookup"><span data-stu-id="1a24c-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="1a24c-113">В предыдущем примере показан способ создания относительно простой фигуры, треугольника.</span><span class="sxs-lookup"><span data-stu-id="1a24c-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="1a24c-114">Объект <xref:System.Windows.Media.PathGeometry> можно также использовать для создания более сложных фигур, включая дуги и кривые.</span><span class="sxs-lookup"><span data-stu-id="1a24c-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="1a24c-115">Примеры, см. в разделе [Создание эллиптической дуги](how-to-create-an-elliptical-arc.md), [Создание кривой Безье третьего порядка](how-to-create-a-cubic-bezier-curve.md), и [Создание кривой Безье второго порядка](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="1a24c-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="1a24c-116">Этот пример является частью большего примера; полный пример см. в разделе [Пример геометрических объектов](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="1a24c-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a24c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1a24c-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="1a24c-118">Общие сведения о классе Geometry</span><span class="sxs-lookup"><span data-stu-id="1a24c-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="1a24c-119">Примеры геометрических объектов</span><span class="sxs-lookup"><span data-stu-id="1a24c-119">Geometries Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159989)
