---
title: Практическое руководство. Отображение времени с помощью элемента управления DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 84f10540e7735ac1043e63eecda84161c10deeef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591719"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Практическое руководство. Отображение времени с помощью элемента управления DateTimePicker
Чтобы пользователи приложения могли выбирать дату и время, которые будут отображаться в указанном формате, используйте элемент управления <xref:System.Windows.Forms.DateTimePicker>. Ниже показано, как использовать элемент управления <xref:System.Windows.Forms.DateTimePicker> для отображения времени.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>Отображение времени с помощью элемента управления DateTimePicker  
  
1. Задайте свойству <xref:System.Windows.Forms.DateTimePicker.Format%2A> значение <xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. Присвойте свойству <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> элемента <xref:System.Windows.Forms.DateTimePicker> значение `true`.  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Пример  
 В примере кода ниже показано, как создать элемент <xref:System.Windows.Forms.DateTimePicker>, позволяющий пользователю выбирать только время.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
- ссылки на сборки System, System.Data, System.Drawing и System.Windows.Forms.  
  
## <a name="see-also"></a>См. также

- [Элемент управления DateTimePicker](datetimepicker-control-windows-forms.md)
