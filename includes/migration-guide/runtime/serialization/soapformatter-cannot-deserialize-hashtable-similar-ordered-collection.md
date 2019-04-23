---
ms.openlocfilehash: 6ed7438a7f6e7710fcce03c8260a1360143f8d93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235494"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>Классу SoapFormatter не удается выполнить десериализацию хэш-таблицы и подобных упорядоченных объектов коллекции

|   |   |
|---|---|
|Подробные сведения|Класс <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> не гарантирует, что объекты, сериализованные в одной версии .NET Framework, будут успешно десериализованы в другой версии платформы. В частности, в некоторые упорядоченные коллекции (например, <xref:System.Collections.Hashtable?displayProperty=name>) добавлены элементы в версиях с 4.0 по 4.5, поэтому объекты этих типов не могут быть десериализованы в .NET Framework 4.0, если бы они были сериализованы в .NET Framework 4.5. Обратите внимание, что если сериализованные данные сериализуются и десериализуются в одной версии .NET Framework, проблемы не возникают.|
|Предложение|Чтобы обеспечить поддержку изменений в .NET Framework, сериализацию <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> следует заменить на сериализацию <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> или <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>.|
|Область|Дополнительный номер|
|Версия|4.5|
|Тип|Среда выполнения|
|Затронутые API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
