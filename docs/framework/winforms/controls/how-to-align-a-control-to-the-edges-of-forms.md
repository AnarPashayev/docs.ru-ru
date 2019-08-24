---
title: Практическое руководство. Выравнивание элементов управления по границам формы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015949"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Практическое руководство. Выравнивание элементов управления по границам формы

Элемент управления можно выровнять по границе формы с помощью свойства <xref:System.Windows.Forms.Control.Dock%2A>. Это свойство определяет, в каком месте формы будет размещаться элемент управления. Свойство <xref:System.Windows.Forms.Control.Dock%2A> может принимать указанные ниже значения.

|Параметр|Влияние на элемент управления|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Фиксирует элемент управления у нижнего края формы.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Заполняет все свободное пространство формы.|
|<xref:System.Windows.Forms.DockStyle.Left>|Фиксирует элемент управления у левого края формы.|
|<xref:System.Windows.Forms.DockStyle.None>|Не фиксирует элемент нигде; он отображается в месте, указанном в свойстве <xref:System.Windows.Forms.Control.Location%2A>.|
|<xref:System.Windows.Forms.DockStyle.Right>|Фиксирует элемент управления у правого края формы.|
|<xref:System.Windows.Forms.DockStyle.Top>|Фиксирует элемент управления у верхнего края формы.|

Эта возможность поддерживается во время разработки в Visual Studio.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Установка свойства Dock для элемента управления во время выполнения

Присвойте свойству <xref:System.Windows.Forms.Control.Dock%2A> соответствующее значение в коде.

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Разработка пользовательских элементов управления Windows Forms в .NET Framework](developing-custom-windows-forms-controls.md)
- [Практическое руководство. Привязка и закрепление дочерних элементов управления в элементе управления FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Практическое руководство. Привязка и закрепление дочерних элементов управления в элементе управления TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Свойство AutoSize](autosize-property-overview.md)
