---
ms.openlocfilehash: 14b8930044381d1d86ec7984d36a5c3588eebd81
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774032"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Алгоритмом хэширования для компилятора разметки WPF по умолчанию теперь является SHA256

|   |   |
|---|---|
|Подробные сведения|Компилятор разметки (MarkupCompiler) WPF предоставляет службы компиляции для файлов разметки XAML.  В .NET Framework 4.7.1 и более ранних версиях для вычисления значений контрольной суммы по умолчанию использовался хэш-алгоритм SHA1. С учетом выявленных проблем с безопасностью SHA1, начиная с версии .NET Framework 4.7.2, теперь по умолчанию используется алгоритм SHA256.  Это изменение затрагивает все поколения контрольной суммы для файлов разметки во время компиляции.|
|Предложение|Разработчикам приложений, предназначенных для .NET Framework 4.7.2 или более поздних версий, которым требуется вернуться к режиму хэширования SHA1, необходимо установить следующий флаг AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Разработчикам, которым требуется использовать хэширование SHA256 для версий целевой платформы ниже .NET Framework 4.7.2, необходимо задать следующий флаг AppContext.  Обратите внимание, что установленная версия .NET Framework должна быть 4.7.2 или выше.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Область|Прозрачный|
|Версия|4.7.2|
|Тип|Изменение целевой платформы|
