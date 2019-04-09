---
title: Практическое руководство. Управление заливкой составных фигур
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 9b3ab1f7b81c296aa1ee766136b6c95b82cab105
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084054"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Практическое руководство. Управление заливкой составных фигур
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Свойство <xref:System.Windows.Media.GeometryGroup> или <xref:System.Windows.Media.PathGeometry>, указывает «правило», которое Составная фигура использует для определения, является ли заданная точка частью геометрии. Существует два возможных значения для <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> и <xref:System.Windows.Media.FillRule.Nonzero>. Следующие разделы описывают использование этих двух правил.  
  
 **EvenOdd:** Это правило определяет, находится ли точка в области заполнения, рисования луча от этой точки до бесконечности в любом направлении и подсчета числа сегментов пути в пределах заданной фигуры пересекает луч. Если это число нечетное, точка находится внутри; если четное — точка находится снаружи.  
  
 Например, ниже XAML создает составной фигуры, состоящий из ряда концентрических колец (мишень) с <xref:System.Windows.Media.GeometryGroup.FillRule%2A> присвоено <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 На следующем рисунке показана фигура, созданная в предыдущем примере.  
  
 ![Снимок экрана: Свойство FillRule для EvenOdd](./media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Обратите внимание, что на приведенном выше рисунке центр и третье кольцо не заполнены. Это потому, что луч, нарисованный из любой точки в одном из этих двух колец проходит через четное число сегментов. См. рисунок ниже:  
  
 ![Схема: Значение свойства FillRule для EvenOdd](./media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **Ненулевое значение:** Это правило определяет, находится ли точка в области заполнения пути, рисования луча от этой точки до бесконечности в любом направлении и проверкой мест, в которых сегмент фигуры пересекает луч. Начиная с нуля, добавляется единица каждый раз, когда сегмент пересекает луч слева направо, и вычитается единица каждый раз, когда сегмент пересекает луч справа налево. Если после подсчета пересечений результат равен нулю, то точка находится снаружи пути. В противном случае — она находится внутри.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 В примере выше, значение <xref:System.Windows.Media.FillRule.Nonzero> для <xref:System.Windows.Media.GeometryGroup.FillRule%2A> дает в результате следующий рисунок:  
  
 ![Снимок экрана: Значение NonZero свойства FillRule](./media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Как можно видеть, все кольца заполнены. Это связано с тем, что все сегменты идут в одном направлении и поэтому луч, рисуемый из любой точки, будет пересекать один или несколько сегментов и сумма пересечений не будет равна нулю. Например, на следующем рисунке красные стрелки обозначают направление рисования сегментов, а белая стрелка показывает произвольный луч, идущий от точки во внутреннем кольце. Начиная с нуля, для каждого сегмента, который пересекает луч, значение 1 добавляется, так как сегмент пересекает луч слева направо.  
  
 ![Схема: Значение свойства FillRule равно NonZero](./media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Чтобы лучше продемонстрировать поведение <xref:System.Windows.Media.FillRule.Nonzero> правило требуется более сложная фигура с сегментами, идущими в разных направлениях является обязательным. Приведенный ниже код XAML создает фигуру, аналогичную аналогичен предыдущему примеру, за исключением того, что она создается с <xref:System.Windows.Media.PathGeometry> а не <xref:System.Windows.Media.EllipseGeometry> которого создаются четыре концентрических дуги а не полностью замкнутые концентрические окружности.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 На следующем рисунке показана фигура, созданная в предыдущем примере.  
  
 ![Снимок экрана: Значение свойства FillRule для NonZero](./media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Обратите внимание, что третья дуга от центра не заполнена. На приведенном ниже рисунке показана причина этого. На рисунке красные стрелки обозначают направление, в котором рисуются сегменты. Две белые стрелки показывают два произвольных луча, которые выходят из точки в «незаполненной» области. Как видно из рисунка, сумма значений для луча, пересекающего сегменты в пути, равна нулю. Как указано выше, сумма ноль означает, что точка не является частью геометрии (не является частью заливки), а сумма, которая *не равна* нулю, в том числе отрицательное значение, является частью геометрии.  
  
 ![Схема: Значение свойства FillRule для NonZero](./media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Примечание.** В рамках <xref:System.Windows.Media.FillRule>, все фигуры считаются замкнутыми. Если в сегменте есть разрыв, нарисуйте воображаемую линию, чтобы его закрыть. В приведенном выше примере имеются небольшие разрывы в кольцах. Учитывая это, можно предположить, что луч, проходящий через разрыв, даст другой результат, чем луч, проходящий в другом направлении. Ниже приведен увеличенный рисунок одного из этих разрывов и «воображаемый сегмент» (сегмент, нарисованный для применения <xref:System.Windows.Media.FillRule>), закрывает его.  
  
 ![Схема: Для FillRule сегменты всегда закрыты](./media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Пример  
  
## <a name="see-also"></a>См. также

- [Создание составной фигуры](how-to-create-a-composite-shape.md)
- [Общие сведения о классе Geometry](geometry-overview.md)
