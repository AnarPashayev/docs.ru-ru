---
ms.openlocfilehash: addfd55fd01b13e9088e4706ff846fc624aafa68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804944"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus вызывается повторно, если соответствующий обработчик выводит окно сообщения Windows Forms

|   |   |
|---|---|
|Подробные сведения|Начиная с .NET Framework 4.5, вызов <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> из обработчика <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> приведет к повторному запуску обработчика после закрытия окна сообщения. В результате может начаться бесконечный цикл вывода окон сообщений.|
|Предложение|Существует два способа решения этой проблемы:<ol><li>Ее можно избежать, вызвав <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> вместо <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Ее можно избежать, открыв окно сообщения из обработчика событий <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> (в отличие от обработчика событий <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name>).</li></ol>|
|Область|Пограничный случай|
|Версия|4.5|
|Тип|Среда выполнения|
|Затронутые API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
