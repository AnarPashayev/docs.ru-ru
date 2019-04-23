---
title: Практическое руководство. Добавление выходного значения анимации к начальному значению анимации
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102613"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Практическое руководство. Добавление выходного значения анимации к начальному значению анимации
В этом примере показано, как добавление выходного значения анимации к начальному значению анимации.  
  
## <a name="example"></a>Пример  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Свойство указывает, следует ли выходное значение анимации добавлены начальным значением (базовое значение) анимированного свойства. Можно использовать <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> свойство с большинством базовых анимаций и большинство анимации ключевого кадра. Дополнительные сведения см. в разделе [Общие сведения об анимации](animation-overview.md) и [сведения об анимации по ключевым кадрам](key-frame-animations-overview.md).  
  
 В следующем примере показано применение <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> свойство с <xref:System.Windows.Media.Animation.DoubleAnimation> и с помощью <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> свойство с <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>См. также

- [Накапливание значений анимации в повторяющихся циклах](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Общие сведения об эффектах анимации](animation-overview.md)
- [Общие сведения об анимации по ключевым кадрам](key-frame-animations-overview.md)
- [Анимации и практические руководства](animation-and-timing-how-to-topics.md)
