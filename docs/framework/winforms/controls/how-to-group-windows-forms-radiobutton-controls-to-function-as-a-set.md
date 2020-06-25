---
title: Группирование элементов управления RadioButton для работы в качестве набора
description: Узнайте, как группировать Windows Forms элементы управления RadioButton для работы независимо от других наборов.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325918"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Практическое руководство. Создание переключателя для выбора одной из нескольких установок на базе элементов управления RadioButton в Windows Forms
Windows Forms <xref:System.Windows.Forms.RadioButton> элементы управления позволяют предоставить пользователям выбор между двумя или более параметрами, из которых только один может быть назначен процедуре или объекту. Например, группа <xref:System.Windows.Forms.RadioButton> элементов управления может отображать один или несколько перевозчиков пакетов для заказа, но будут использоваться только те из них. Поэтому <xref:System.Windows.Forms.RadioButton> можно выбрать только один за раз, даже если он является частью функциональной группы.  
  
 Переключатели группируются путем их рисования внутри контейнера, такого как <xref:System.Windows.Forms.Panel> элемент управления, <xref:System.Windows.Forms.GroupBox> элемент управления или форма. Все переключатели, добавленные непосредственно в форму, становятся одной группой. Чтобы добавить отдельные группы, необходимо поместить их внутри панелей или групп. Дополнительные сведения о панелях или полях групп см. в разделе Общие сведения об [элементе управления Panel](panel-control-overview-windows-forms.md) или [элементе управления GroupBox](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Группировка элементов управления RadioButton как набора, который будет функционировать независимо от других наборов  
  
1. Перетащите элемент <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> управления или с вкладки **Windows Forms** на **панели элементов** на форму.  
  
2. Рисование <xref:System.Windows.Forms.RadioButton> элементов управления в <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> элементе управления или.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.RadioButton>
- [Общие сведения об элементе управления RadioButton](radiobutton-control-overview-windows-forms.md)
- [Общие сведения об элементе управления Panel](panel-control-overview-windows-forms.md)
- [Общие сведения об элементе управления GroupBox](groupbox-control-overview-windows-forms.md)
- [Общие сведения об элементе управления CheckBox](checkbox-control-overview-windows-forms.md)
- [Элемент управления RadioButton](radiobutton-control-windows-forms.md)
