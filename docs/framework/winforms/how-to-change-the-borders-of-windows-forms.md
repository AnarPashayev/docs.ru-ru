---
title: Практическое руководство. Изменение границ в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 036bef79e83350801ce45e6b77691339c6548d15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665255"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Практическое руководство. Изменение границ в Windows Forms
При определении внешнего вида и поведения формы Windows Forms можно выбрать из нескольких стилей границы. Изменив <xref:System.Windows.Forms.Form.FormBorderStyle%2A> свойство, можно управлять поведением изменения размеров формы. Кроме того, параметр <xref:System.Windows.Forms.Form.FormBorderStyle%2A> влияет на способ отображения строки заголовка и кнопок, которые на нем могут отображаться. Дополнительные сведения см. в разделе <xref:System.Windows.Forms.FormBorderStyle>.  
  
 В Visual Studio предусмотрена расширенная поддержка данной задачи.  
  
 См. также [Практическое руководство. Изменение границ в Windows Forms с помощью конструктора](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Установка стиля границ формы Windows Forms программными средствами  
  
- Задайте для свойства <xref:System.Windows.Forms.Form.FormBorderStyle%2A> нужный стиль. В следующем примере кода задает стиль границы формы `DlgBx1` для <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Также см. раздел [Как Создание диалоговых окон во время разработки](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Кроме того Если выбран стиль границы для формы, которая предоставляет необязательный **свернуть** и **развернуть** кнопок, можно указать, хотите ли вы один или оба эти кнопки для его функционирования. Эти кнопки полезны в тех случаях, когда требуется точно управлять взаимодействием с пользователем. **Свернуть** и **развернуть** кнопки включены по умолчанию, и их функции изменяются с помощью **свойства** окна.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Приступая к работе с Windows Forms](getting-started-with-windows-forms.md)
