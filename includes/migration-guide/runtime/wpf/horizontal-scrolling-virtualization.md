---
ms.openlocfilehash: 14585b6de3ce02884f8be789930fc8610f73ba7d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621402"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Горизонтальная прокрутка и виртуализация

#### <a name="details"></a>Подробнее

Это изменение относится к элементу управления <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName>, который выполняет собственную виртуализацию в направлении, перпендикулярном основному направлению прокрутки (главным примером является элемент <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, для которого EnableColumnVirtualization=&quot;True&quot;).  Результат некоторых операций горизонтальной прокрутки был изменен для получения результатов, которые являются более интуитивно понятными и более подобными результатам сопоставимых вертикальных операций.<p/>К таким операциям относятся &quot;Прокрутка на месте&quot; и &quot;К правому краю&quot;, с использованием имен из меню, открываемого щелчком правой кнопкой мыши по горизонтальной полосе прокрутки.  Обе они вычисляют предполагаемое смещение и вызывают <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>После прокрутки к новой позиции может измениться значение &quot;на месте&quot; или &quot;правый край&quot; может измениться, поскольку новое девиртуализированное содержимое изменяет значение свойства <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName>.<p/>В версиях до .NET Framework 4.6.2 операция прокрутки просто использует предполагаемое смещение, несмотря на то, что оно может оказаться больше не &quot;на месте&quot; или на &quot;правом краю&quot;.  Его результаты проявляются в виде &quot;подпрыгивания&quot; бегунка прокрутки. Лучше всего это проиллюстрировать на примере. Допустим, для <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> заданы значения ExtentWidth=1000 и Width=200.  При прокрутке &quot;к правому краю&quot; используется вариант смещения 1000 – 200 = 800.  В процессе прокрутки к этому смещению девиртуализируются новые столбцы. Предположим, что они очень широкие, и теперь свойство <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> получает значение 2000.  Прокрутка заканчивается при HorizontalOffset=800, и бегунок &quot;отпрыгивает&quot; обратно почти в середину полосы прокрутки, а точнее, на позицию 40 % (800/2000).<p/>Это изменение позволяет повторно вычислить новое предполагаемое смещение в такой ситуации и повторить попытку. (Так уже работает вертикальная прокрутка.) <p/>Это поведение стало более прогнозируемым и интуитивно понятным для конечного пользователя, но изменение может повлиять на те приложения, которые ожидают конкретных значений свойства <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> после горизонтальной прокрутки, вызванной действиями пользователя или прямым вызовом <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.

#### <a name="suggestion"></a>Предложение

Нужно изменить приложения, использующие прогнозируемое значение для <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName>, чтобы они извлекали фактическое значение (а также значение <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName>) после любой горизонтальной прокрутки, при которой <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> может измениться из-за девиртуализации.

| name    | Значение       |
|:--------|:------------|
| Область   |Дополнительный номер|
|Version|4.6.2|
|Type|Среда выполнения

#### <a name="affected-apis"></a>Затронутые API

-<xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
