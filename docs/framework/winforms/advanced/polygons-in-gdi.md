---
title: Многоугольники в GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641311"
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="e37a0-102">Многоугольники в GDI+</span><span class="sxs-lookup"><span data-stu-id="e37a0-102">Polygons in GDI+</span></span>
<span data-ttu-id="e37a0-103">Многоугольник — замкнутой фигуры с тремя или более прямые стороны.</span><span class="sxs-lookup"><span data-stu-id="e37a0-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="e37a0-104">Например треугольник — это многоугольник с трех сторон, прямоугольник — это многоугольник с четырех сторон и пятиугольник — это многоугольник с пятью сторонами.</span><span class="sxs-lookup"><span data-stu-id="e37a0-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="e37a0-105">На следующем рисунке несколько многоугольников.</span><span class="sxs-lookup"><span data-stu-id="e37a0-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="e37a0-106">![Многоугольники](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="e37a0-106">![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="e37a0-107">Рисование многоугольника</span><span class="sxs-lookup"><span data-stu-id="e37a0-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="e37a0-108">Чтобы нарисовать прямоугольник, вам потребуется <xref:System.Drawing.Graphics> объекта, <xref:System.Drawing.Pen> объекта, а также массив <xref:System.Drawing.Point> (или <xref:System.Drawing.PointF>) объектов.</span><span class="sxs-lookup"><span data-stu-id="e37a0-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="e37a0-109"><xref:System.Drawing.Graphics> Предоставляет <xref:System.Drawing.Graphics.DrawPolygon%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="e37a0-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="e37a0-110"><xref:System.Drawing.Pen> Объект сохраняет атрибуты, например, ширина и цвет линии, используемый для визуализации многоугольника, а также массив <xref:System.Drawing.Point> объектов содержит все точки, чтобы быть соединенных прямых линий.</span><span class="sxs-lookup"><span data-stu-id="e37a0-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="e37a0-111"><xref:System.Drawing.Pen> Объект и массив <xref:System.Drawing.Point> объекты передаются как аргументы для <xref:System.Drawing.Graphics.DrawPolygon%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="e37a0-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="e37a0-112">В следующем примере рисуется три стороны многоугольника.</span><span class="sxs-lookup"><span data-stu-id="e37a0-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="e37a0-113">Обратите внимание, что только три точки в `myPointArray`: (0, 0), (50, 30) и (30, 60).</span><span class="sxs-lookup"><span data-stu-id="e37a0-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="e37a0-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Метод автоматически закрывает многоугольника путем рисования линии из (30, 60) обратно к начальной точке (0, 0).</span><span class="sxs-lookup"><span data-stu-id="e37a0-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="e37a0-115">На следующем рисунке многоугольника.</span><span class="sxs-lookup"><span data-stu-id="e37a0-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="e37a0-116">![Многоугольник](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="e37a0-116">![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37a0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="e37a0-117">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="e37a0-118">Линии, кривые и фигуры</span><span class="sxs-lookup"><span data-stu-id="e37a0-118">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="e37a0-119">Практическое руководство. Создание пера</span><span class="sxs-lookup"><span data-stu-id="e37a0-119">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
