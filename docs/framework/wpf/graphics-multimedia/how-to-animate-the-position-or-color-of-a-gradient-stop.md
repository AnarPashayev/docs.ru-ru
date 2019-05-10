---
title: Практическое руководство. Анимация положения или цвета ограничения градиента
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: 4762233cace895c9d492fb426f3f6be14498ad53
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593372"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Практическое руководство. Анимация положения или цвета ограничения градиента
В этом примере демонстрируется анимация <xref:System.Windows.Media.GradientStop.Color%2A> и <xref:System.Windows.Media.GradientStop.Offset%2A> из <xref:System.Windows.Media.GradientStop> объектов.  
  
## <a name="example"></a>Пример  
 Следующий пример анимирует три градиента внутри <xref:System.Windows.Media.LinearGradientBrush>. В примере используется три анимации, каждый из которых выполняет анимацию различных градиента:  
  
- Первая анимация, <xref:System.Windows.Media.Animation.DoubleAnimation>, анимирует первого градиента <xref:System.Windows.Media.GradientStop.Offset%2A> от 0,0 до 1,0, а затем снова 0,0. Таким образом первый цвет градиента перемещается из левой части правую сторону прямоугольника и затем обратно в левой части.  
  
- Второй анимации, <xref:System.Windows.Media.Animation.ColorAnimation>, анимирует второй градиента <xref:System.Windows.Media.GradientStop.Color%2A> из <xref:System.Windows.Media.Colors.Purple%2A> для <xref:System.Windows.Media.Colors.Yellow%2A> и затем обратно до <xref:System.Windows.Media.Colors.Purple%2A>. В результате Средний цвет градиента изменяется от фиолетового на желтый и обратно.  
  
- Третий анимации, другой <xref:System.Windows.Media.Animation.ColorAnimation>, анимирует прозрачность третий градиента <xref:System.Windows.Media.GradientStop.Color%2A> -1, а затем снова. Таким образом третий цвет в градиенте исчезает, а затем снова становится непрозрачным.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Несмотря на то, что в этом примере используется <xref:System.Windows.Media.LinearGradientBrush>, процесс одинаков для анимации <xref:System.Windows.Media.GradientStop> объектов внутри <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Дополнительные примеры см. в разделе [пример использования кистей](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Media.GradientStop>
- [Общие сведения об эффектах анимации](animation-overview.md)
- [Общие сведения о раскадровке](storyboards-overview.md)
