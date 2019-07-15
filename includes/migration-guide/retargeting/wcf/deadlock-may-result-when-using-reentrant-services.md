---
ms.openlocfilehash: 0aaa0ad0e0e3cbd23de287b3b79a8c209143544e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859330"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>При использовании реентерабельных служб может возникнуть взаимоблокировка

|   |   |
|---|---|
|Подробные сведения|В реентерабельной службе может возникнуть взаимоблокировка, которая ограничивает экземпляры службы одним потоком выполнения за раз. Службы, в которых может возникнуть это проблема, имеют следующий <xref:System.ServiceModel.ServiceBehaviorAttribute> в коде:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Предложение|Чтобы устранить эту проблему, выполните следующие действия:<ul><li>Установите для режима параллелизма службы <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> или &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Например:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Установите последнее обновление для .NET Framework 4.6.2 или обновитесь до последней версии платформы .NET Framework. Это приведет к отключению потока <xref:System.Threading.ExecutionContext> в <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. Это поведение можно настраивать. Это эквивалентно добавлению следующего параметра приложения в файл конфигурации:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Значение <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> нельзя устанавливать на <code>false</code> для реентерабельных служб.|
|Область|Дополнительный номер|
|Версия|4.6.2|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

