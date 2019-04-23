---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804886"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap успешно преобразует значки с кадрами PNG в растровые изображения

|   |   |
|---|---|
|Подробные сведения|Начиная с приложений, предназначенных для .NET Framework 4.6, метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> успешно преобразует значки с кадрами PNG в объекты Bitmap.<p/>В приложениях, предназначенных для .NET Framework 4.5.2 и более ранних версий, метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> создает исключение <xref:System.ArgumentOutOfRangeException>, если объект Icon содержит кадры PNG.<p/>Это изменение затрагивает приложения, которые компилируются повторно для платформы .NET Framework 4.6 и в которых реализуется специальная обработка исключения <xref:System.ArgumentOutOfRangeException>, создаваемого при наличии кадров PNG в объекте Icon . При выполнении в .NET Framework 4.6 преобразование проходит успешно, исключение <xref:System.ArgumentOutOfRangeException> больше не создается, и поэтому обработчик исключений больше не вызывается.|
|Предложение|Если такое поведение нежелательно, можно сохранить прежнее поведение, добавив в раздел <code>&lt;runtime&gt;</code> файла app.config следующий элемент:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Если файл app.config уже содержит элемент <code>AppContextSwitchOverrides</code>, новое значение следует объединить с атрибутом значения следующим образом:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Область|Дополнительный номер|
|Версия|4.6|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
