---
ms.openlocfilehash: ed0dde302e30ae0cf3c7a8d0985f2314d91cab66
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760906"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream использует собственные интерфейсы API для распаковки

|   |   |
|---|---|
|Подробные сведения|Начиная с .NET Framework 4.7.2 реализация распаковки в классе <code>T:System.IO.Compression.DeflateStream</code> была изменена и теперь использует собственные API Windows по умолчанию. Как правило, это приводит к значительному повышению производительности. Во всех приложениях .NET, предназначенных для .NET Framework 4.7.2 или более поздней версии, используется собственная реализация. Это изменение может привести к некоторым отличиям в поведении, в том числе:<ul><li>Могут отличаться сообщения об исключениях. Однако тип исключения не изменится.</li><li>Могут иначе обрабатываться некоторые особые ситуации, например, если для завершения операции недостаточно памяти.</li><li>Существуют известные различия в анализе заголовка gzip (примечание: это затрагивает только набор <code>GZipStream</code> для распаковки):</li><li>При анализе недопустимых заголовков исключения могут возникать в разное время.</li><li>Собственная реализация требует установку значений для некоторых зарезервированных флагов в заголовке gzip (т. е. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) в соответствии со спецификацией, что может приводить к исключению там, где ранее недопустимые значения игнорировались.</li></ul>|
|Предложение|Если распаковка с собственными API-интерфейсами отрицательно повлияла на поведение приложения, этот компонент можно отключить, добавив переключатель <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> в раздел <code>runtime</code> файла app.config и установив для него значение <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Область|Дополнительный номер|
|Версия|4.7.2|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|

