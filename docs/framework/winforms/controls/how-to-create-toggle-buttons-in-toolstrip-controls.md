---
title: Практическое руководство. Создание переключателей в элементах управления ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972356"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Практическое руководство. Создание переключателей в элементах управления ToolStrip

Когда пользователь щелкает выключатель, он отображается утопленным и остается утопленным, пока пользователь не нажмет кнопку еще раз.

## <a name="to-create-a-toggling-toolstripbutton"></a>Создание переключателя ToolStripButton

- Используйте код, такой как следующий пример кода. В этом коде предполагается, что форма <xref:System.Windows.Forms.ToolStrip> содержит элемент управления и его <xref:System.Windows.Forms.ToolStrip.Items%2A> коллекция содержит <xref:System.Windows.Forms.ToolStripButton> вызванный `toolStripButton1`. Также предполагается, что имеется обработчик событий с именем `toolStripButton1_CheckedChanged`.

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.ToolStripButton>
- [Общие сведения об элементе управления ToolStrip](toolstrip-control-overview-windows-forms.md)
