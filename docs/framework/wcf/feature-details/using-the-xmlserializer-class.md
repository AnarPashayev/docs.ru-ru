---
title: Использование класса XmlSerializer
description: Сведения о XmlSerializer, который WCF использует для сериализации данных в приложении в XML-код, передаваемый между клиентами и службами.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: f7473de3f34ba543b4fabfe93167ea267f16dda5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246390"
---
# <a name="using-the-xmlserializer-class"></a>Использование класса XmlSerializer

Windows Communication Foundation (WCF) может использовать две различные технологии сериализации, чтобы превратить данные в приложение в XML, передаваемый между клиентами и службами, процесс, называемый сериализацией.

## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer по умолчанию

По умолчанию WCF использует <xref:System.Runtime.Serialization.DataContractSerializer> класс для сериализации типов данных. Данный сериализатор поддерживает следующие типы:

- Примитивные типы (например, целые числа, строки и массивы байтов), а также некоторые специальные типы, такие как <xref:System.Xml.XmlElement> и <xref:System.DateTime>, обрабатываемые как примитивы.

- Типы контрактов данных (типы, отмеченные атрибутом <xref:System.Runtime.Serialization.DataContractAttribute>).

- Типы, отмеченные атрибутом <xref:System.SerializableAttribute>, включающие типы, реализующие интерфейс <xref:System.Runtime.Serialization.ISerializable>.

- Типы, реализующие интерфейс <xref:System.Xml.Serialization.IXmlSerializable>.

- Множество типов общих коллекций, включающих множество типов универсальных коллекций.

Многие типы .NET Framework относятся к двум последним категориям и поэтому являются сериализуемыми. Массивы сериализуемых типов также являются сериализуемыми. Полный список см. в разделе [указание передача данных в контрактах служб](specifying-data-transfer-in-service-contracts.md).

<xref:System.Runtime.Serialization.DataContractSerializer>, Используемый совместно с типами контрактов данных, является рекомендуемым способом написания новых служб WCF. Дополнительные сведения см. [в разделе Использование контрактов данных](using-data-contracts.md).

## <a name="when-to-use-the-xmlserializer-class"></a>Когда использовать класс XmlSerializer

WCF также поддерживает <xref:System.Xml.Serialization.XmlSerializer> класс. <xref:System.Xml.Serialization.XmlSerializer>Класс не является уникальным для WCF. Это тот же механизм сериализации, который используется ASP.NET веб-службами. Класс <xref:System.Xml.Serialization.XmlSerializer> поддерживает более узкий набор типов по сравнению с классом <xref:System.Runtime.Serialization.DataContractSerializer>, но позволяет более четко контролировать получаемый XML-код и более полно поддерживает стандарт языка определения схемы XML (XSD). Кроме того, данный класс не требует никаких декларативных атрибутов на сериализуемых типах. Дополнительные сведения см. в разделе XML-сериализация статьи .NET Framework документация. Класс <xref:System.Xml.Serialization.XmlSerializer> не поддерживает типы контрактов данных.

При использовании Svcutil.exe или функции **Добавление ссылки на службу** в Visual Studio для создания клиентского кода для службы стороннего производителя или для доступа к схеме стороннего разработчика соответствующий сериализатор выбирается автоматически. Если схема не совместима с <xref:System.Runtime.Serialization.DataContractSerializer>, выбирается <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="manually-switching-to-the-xmlserializer"></a>Ручное переключение на XmlSerializer

Иногда может понадобиться ручное переключение на <xref:System.Xml.Serialization.XmlSerializer>. Это происходит, например, в следующих случаях:

- При переносе приложения из веб-служб ASP.NET в WCF может потребоваться повторно использовать существующие <xref:System.Xml.Serialization.XmlSerializer> совместимые типы вместо создания новых типов контрактов данных.

- Если важен четкий контроль над XML-кодом, появляющимся в сообщении, но документ WSDL отсутствует - например, при создании службы с типами, которые должны соответствовать некоторой стандартизированной опубликованной схеме, которая не совместима с DataContractSerializer.

- При создании служб, которые используют стандарт предыдущих версий с кодировкой SOAP.

В этом и в других случаях может понадобиться ручное переключение на класс <xref:System.Xml.Serialization.XmlSerializer> путем применения атрибута `XmlSerializerFormatAttribute` к службе, как показано в следующем коде.

[!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
[!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]

## <a name="security-considerations"></a>Соображения безопасности

> [!NOTE]
> При переключении модулей сериализации необходимо соблюдать меры предосторожности. Один и тот же тип может быть сериализован в XML-код по-разному, в зависимости от используемого сериализатора. Если случайно был использован не тот сериализатор, может быть раскрыта информация из типа, который раскрывать не предполагалось.

Например, класс <xref:System.Runtime.Serialization.DataContractSerializer> при сериализации типов контрактов данных сериализует только элементы, отмеченные атрибутом <xref:System.Runtime.Serialization.DataMemberAttribute>. Класс <xref:System.Xml.Serialization.XmlSerializer> сериализует любой открытый элемент. Смотрите тип в следующем коде.

[!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
[!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]

Если тип был случайно использован в контракте службы, где выбран класс <xref:System.Xml.Serialization.XmlSerializer>, сериализуется элемент `creditCardNumber`, который, судя по всему, для этого не предназначен.

Даже если класс <xref:System.Runtime.Serialization.DataContractSerializer> является значением по умолчанию, можно явным образом выбрать его для своей службы (хотя делать это не всегда обязательно), применив атрибут <xref:System.ServiceModel.DataContractFormatAttribute> к типу контракта данных.

Сериализатор, используемый для службы, является неотъемлемой частью контракта и не может быть изменен путем выбора другой привязки или путем изменения других параметров конфигурации.

Другие важные вопросы безопасности распространяются на класс <xref:System.Xml.Serialization.XmlSerializer>. Во-первых, настоятельно рекомендуется, чтобы любое приложение WCF, использующее <xref:System.Xml.Serialization.XmlSerializer> класс, было подписано ключом, который защищается от раскрытия. Данная рекомендация применяется и при переключении на <xref:System.Xml.Serialization.XmlSerializer> вручную, и при выполнении автоматического переключения (с помощью Svcutil.exe, добавления ссылки на службы или подобных средств). Это обусловлено тем, что <xref:System.Xml.Serialization.XmlSerializer> механизм сериализации поддерживает загрузку *предварительно созданных сборок сериализации* при условии, что они подписаны с помощью того же ключа, что и приложение. Неподписанное приложение совершенно не защищено от возможности совпадения злонамеренной сборки с ожидаемым именем заранее созданной сборки сериализации, размещенной в папке приложения или в глобальном кэше сборок. Чтобы попытаться сделать это, злоумышленнику, конечно, сначала нужно получить доступ с правами записи к одному из этих двух расположений.

Другая угроза, которая существует при использовании <xref:System.Xml.Serialization.XmlSerializer>, относится к доступу с правами записи к временной папке системы. <xref:System.Xml.Serialization.XmlSerializer>Модуль сериализации создает и использует в этой папке Временные *сборки сериализации* . Следует иметь в виду, что любой процесс с доступом на запись к временной папке может перезаписать эти сборки сериализации с помощью вредоносного кода.

## <a name="rules-for-xmlserializer-support"></a>Правила для поддержки XmlSerializer

Нельзя непосредственно применить <xref:System.Xml.Serialization.XmlSerializer>-совместимые атрибуты к параметрам операции контракта или возвратить значения. Однако они могут быть применены к типизированным сообщениям (части тела контракта сообщения), как показано в следующем коде.

[!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
[!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]

При применении к типизированным элементам сообщений данные атрибуты переопределяют свойства, конфликтующие с атрибутами типизированного сообщения. Например, в следующем коде `ElementName` переопределяет `Name`.

[!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
[!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]

Атрибут <xref:System.ServiceModel.MessageHeaderArrayAttribute> не поддерживается при использовании <xref:System.Xml.Serialization.XmlSerializer>.

> [!NOTE]
> В этом случае <xref:System.Xml.Serialization.XmlSerializer> метод создает следующее исключение, которое освобождается до WCF: "элемент, объявленный на верхнем уровне схемы, не может иметь `maxOccurs` > 1. Укажите элемент-оболочку для more, указав `XmlArray` или `XmlArrayItem` вместо `XmlElementAttribute` или стиль параметров Wrapped».
>
> При получении такого исключения, разберитесь, с такой ли ситуацией пришлось столкнуться.

WCF не поддерживает <xref:System.Xml.Serialization.SoapIncludeAttribute> <xref:System.Xml.Serialization.XmlIncludeAttribute> атрибуты и в контрактах сообщений и контрактах операций; используйте <xref:System.Runtime.Serialization.KnownTypeAttribute> вместо этого атрибут.

## <a name="types-that-implement-the-ixmlserializable-interface"></a>Типы, реализующие интерфейс IXmlSerializable

Типы, реализующие интерфейс `IXmlSerializable`, полностью поддерживаются сериализатором `DataContractSerializer`. К данным типам всегда нужно применять атрибут <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>, необходимый для управления их схемой.

> [!WARNING]
> Если выполняется сериализация полиморфных типов, необходимо применить атрибут <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> к типу, чтобы убедиться, что сериализуется правильный тип.

Существует три разновидности типов, реализующих интерфейс `IXmlSerializable`: типы, представляющие производное содержимое; типы, представляющие одиночный элемент; устаревшие типы <xref:System.Data.DataSet>.

- Типы содержимого используют метод поставщика схемы, заданный атрибутом `XmlSchemaProviderAttribute`. Метод не возвращает значение `null`, и свойство <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> атрибута остается в значении по умолчанию `false`. Это наиболее распространенное использование типов `IXmlSerializable`.

- Типы элемента используется в том случае, когда тип `IXmlSerializable` должен управлять собственным именем корневого элемента. Чтобы пометить тип как тип элемента, установите свойство <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> атрибута <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> в значение `true` или верните значение `null` из метода поставщика схемы. Наличие метода поставщика схемы является необязательным для типов элементов - вместо имени метода в `null` можно указать значение `XmlSchemaProviderAttribute`. Однако если `IsAny` имеет значение `true` и указан метод поставщика схемы, то метод должен возвращать значение `null`.

- Устаревшие типы <xref:System.Data.DataSet> являются типами `IXmlSerializable`, не отмеченными атрибутом `XmlSchemaProviderAttribute`. Вместо этого они используют для создания схемы метод <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A>. Данный шаблон используется для типа `DataSet`, и его типизированный набор данных наследует класс в более ранних версиях .NET Framework; в настоящее время он устарел и поддерживается только из соображений совместимости с более ранними версиями. Не используйте данный шаблон и всегда применяйте атрибут `XmlSchemaProviderAttribute` к своим типам `IXmlSerializable`.

### <a name="ixmlserializable-content-types"></a>Типы содержимого IXmlSerializable

При сериализации элемента данных типа, который реализует интерфейс `IXmlSerializable` и относится к определенному ранее типу содержимого, сериализатор записывает элемент-оболочку для элемента данных и передает управление методу <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>. Реализация <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> может записывать любой XML-код, включая добавление атрибутов в элемент-оболочку. После выполнения `WriteXml` сериализатор закрывает элемент.

При десериализации элемента данных типа, который реализует интерфейс `IXmlSerializable` и относится к определенному ранее типу содержимого, десериализатор помещает модуль чтения XML в элемент-оболочку для элемента данных и передает управление методу <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>. Метод должен прочесть весь элемент, включая открывающий и закрывающий теги. Убедитесь, что код `ReadXml` обрабатывает случай, когда элемент пуст. Кроме того, реализация `ReadXml` не должна использовать элемент программы-оболочки, именованный особым образом. Имя, выбранное сериализатором, может изменяться.

Разрешается полиморфно присваивать типы содержимого `IXmlSerializable`, например, элементам данных типа <xref:System.Object>. Кроме того, для экземпляров типа разрешено значение null. И наконец, можно использовать типы `IXmlSerializable` с включенным режимом сохранения графов объектов и с <xref:System.Runtime.Serialization.NetDataContractSerializer>. Для всех этих функций требуется, чтобы сериализатор WCF присоединяет определенные атрибуты в элемент-оболочку ("nil" и "Type" в пространстве имен экземпляра XML-схемы, а "ID", "ref", "Type" и "Assembly" в пространстве имен, характерном для WCF).

#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Атрибуты, игнорируемые при реализации ReadXml

Перед передачей управления коду `ReadXml` десериализатор проверяет XML-элемент, обнаруживает данные специальные атрибуты XML и работает с ними. Например, если "nil" имеет значение `true`, десериализуется значение null, и `ReadXml` не вызывается. Если обнаружен полиморфизм, содержимое десериализуется так, как если бы это был другой тип. Вызывается реализация `ReadXml` полиморфно назначенного типа. В любом случае, реализация `ReadXml` игнорирует данные специальные атрибуты, поскольку они обрабатываются десериализатором.

### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Замечания по схемам для типов содержимого IXmlSerializable

При экспорте схемы и типа содержимого `IXmlSerializable` вызывается метод поставщика схемы. <xref:System.Xml.Schema.XmlSchemaSet> передается в метод поставщика схемы. Метод может добавить любую допустимую схему в набор схем. Набор схем содержит схему, которая уже была известна на момент экспорта схемы. Если метод поставщика схем должен добавить элемент в набор схем, он должен определить, имеется ли в наборе схема <xref:System.Xml.Schema.XmlSchema> с соответствующим пространством имен. Если это так, метод поставщика схемы должен добавить новый элемент в существующую схему `XmlSchema`. В противном случае, метод создает новый экземпляр `XmlSchema`. Это важно, если используются массивы типов `IXmlSerializable`. Например, если есть тип `IXmlSerializable`, который экспортируется как тип "A" в пространстве имен "Б", возможно, что к моменту вызова метода поставщика схем, набор схем уже содержит схему для "Б" для удержания типа "ArrayOfA".

Кроме добавления типов в <xref:System.Xml.Schema.XmlSchemaSet>, метод поставщика схемы для типов содержимого должен возвратить ненулевое значение. Метод может возвратить <xref:System.Xml.XmlQualifiedName>, указывающий имя типа схемы, которая будет использоваться для заданного типа `IXmlSerializable`. Полное имя также служит именем контракта данных и пространством имен для типа. Не разрешается возвращать тип, не существующий в наборе схем, немедленно при возврате метода поставщика. Однако предполагается, что к моменту экспорта всех типов (метод <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> вызывается для всех соответствующих типов <xref:System.Runtime.Serialization.XsdDataContractExporter> и выполняется доступ к свойству <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A>) тип существует в наборе схем. Доступ к свойству `Schemas` до того, как были выполнены все соответствующие вызовы `Export`, может привести к созданию исключения <xref:System.Xml.Schema.XmlSchemaException>. Дополнительные сведения о процессе экспорта см. в разделе [Экспорт схем из классов](exporting-schemas-from-classes.md).

Метод поставщика схемы также может возвратить тип <xref:System.Xml.Schema.XmlSchemaType> для использования. Тип может быть или не быть анонимным. Если тип анонимный, схема для типа `IXmlSerializable` экспортируется как анонимный тип при каждом использовании типа `IXmlSerializable` в качестве элемента данных. Тип `IXmlSerializable` все еще имеет контракт данных и пространство имен. (Это определяется, как описано в разделе [имена контрактов данных](data-contract-names.md) , за исключением того, что <xref:System.Runtime.Serialization.DataContractAttribute> атрибут не может быть использован для настройки имени.) Если он не является анонимным, то он должен быть одним из типов в `XmlSchemaSet` . Данный случай эквивалентен возврату `XmlQualifiedName` типа.

Кроме того, для типа экспортируется глобальное объявление элемента. Если к типу не применен атрибут <xref:System.Xml.Serialization.XmlRootAttribute>, то элемент имеет те же имя и пространство имен, что и контракт данных, а его свойство nillable имеет значение `true`. Единственным исключением является пространство имен схемы (). `http://www.w3.org/2001/XMLSchema` Если контракт данных типа находится в этом пространстве имен, соответствующий глобальный элемент находится в пустом пространстве имен, поскольку запрещено добавлять новые элементы в пространство имен схемы. Если тип имеет применяемый к нему атрибут `XmlRootAttribute`, глобальное объявление элемента экспортируется с помощью свойств <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> и <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A>. Значениями по умолчанию при применении атрибута `XmlRootAttribute` являются имя контракта данных, пустое пространство имен, а свойство «nillable» имеет значение `true`.

Те же правила объявления глобального элемента применяются и к устаревшим типам наборов данных. Важно отметить, что `XmlRootAttribute` не может переопределить объявления глобальных элементов, добавленных с помощью пользовательского кода или добавленных в набор схем `XmlSchemaSet` с помощью метода поставщика схем или посредством метода `GetSchema` для устаревших типов наборов данных.

### <a name="ixmlserializable-element-types"></a>Типы элемента IXmlSerializable

Типы элементов `IXmlSerializable` либо имеют свойство `IsAny`, которому присвоено значение `true`, либо их метод поставщика схем возвращает значение `null`.

Сериализация и десериализация типа элемента очень похожа на сериализацию и десериализацию типа содержимого. Однако есть некоторые важные отличия.

- Как правило, реализация `WriteXml` записывает только один элемент (который, конечно, может содержать несколько дочерних элементов). Она не должна записывать атрибуты вне данного одиночного элемента, несколько родственных элементов или смешанное содержимое. Элемент может быть пустым.

- Реализация `ReadXml` не должна прочитывать элемент программы-оболочки. Как правило, реализация прочитывает один элемент, создаваемый методом `WriteXml`.

- При регулярной сериализации типа элемента (например, как элемента данных в контракте данных) сериализатор, как и в случае с типами содержимого, выводит элемент программы-оболочки до вызова метода `WriteXml`. Однако при сериализации типа элемента на верхнем уровне сериализатор обычно не выводит элемент-оболочку в окружение элемента, который записывается методом `WriteXml`, кроме случая, когда корневое имя и пространство имен явно заданы при конструировании сериализатора в конструкторах `DataContractSerializer` или `NetDataContractSerializer`. Дополнительные сведения см. в разделе [сериализация и десериализация](serialization-and-deserialization.md).

- При сериализации типа элемента на верхнем уровне без указания корневого имени и пространства имен во время создания <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> и <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> обычно не выполняют никаких операций, а <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> вызывает `WriteXml`. В данном режиме сериализуемый объект не может иметь значение `null` и не может быть назначен полиморфно. Кроме того, не может быть включено сохранение графов объектов и не может использоваться `NetDataContractSerializer`.

- При десериализации типа элемента на верхнем уровне без указания корневого имени и пространства имен во время построения <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> возвращает значение `true`, если не может найти начало хотя бы одного из элементов. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> с параметром `verifyObjectName`, установленным в значение `true`, работает таким же образом, как и `IsStartObject` перед фактическим считыванием объекта. Затем `ReadObject` передает управление методу `ReadXml`.

Схема, экспортированная для типов элементов, аналогична схеме для типа `XmlElement`, как описано в предыдущем разделе, за исключением того, что метод поставщика схемы может добавлять дополнительную схему в <xref:System.Xml.Schema.XmlSchemaSet> как типы содержимого. Использование атрибута `XmlRootAttribute` с типами элемента не разрешено, и для данных типов никогда не выдаются глобальные объявления элемента.

### <a name="differences-from-the-xmlserializer"></a>Отличия от XmlSerializer

Сериализатор `IXmlSerializable` также понимает интерфейс `XmlSchemaProviderAttribute` и атрибуты `XmlRootAttribute` и <xref:System.Xml.Serialization.XmlSerializer>. Однако есть некоторые отличия в том, как данные атрибуты обрабатываются в модели контракта данных. Сводка важнейших отличий представлена ниже.

- Метод поставщика схемы должен быть открытым для использования в `XmlSerializer`, но не должен быть открытым для использования в модели контракта данных.

- Метод поставщика схемы вызывается, если свойству `IsAny` имеет значение `true` в модели контракта данных, но не с `XmlSerializer`.

- Если атрибут `XmlRootAttribute` не присутствует в содержимом или устаревших типах набора данных, сериализатор `XmlSerializer` экспортирует глобальное объявление элемента в пустое пространство имени. В модели контракта данных используемым пространством имен обычно является пространство имен контракта данных, как было описано ранее.

Помните об этих отличиях при создании типов, которые используются с обеими технологиями сериализации.

### <a name="importing-ixmlserializable-schema"></a>Импорт схемы IXmlSerializable

При импорте схемы, созданной из типов `IXmlSerializable`, существует несколько возможностей.

- Созданная схема может быть допустимой схемой контракта данных, как описано в [справочнике по схеме контракта данных](data-contract-schema-reference.md). В таком случае, схема может быть импортирована обычным образом, и создаются обычные типы контракта данных.

- Созданная схема может не быть действительной схемой контракта данных. Например, метод поставщика схемы может создать схему, которая включает XML-атрибуты, не поддерживаемые в модели контракта данных. В данном случае можно импортировать схему как типы `IXmlSerializable`. Этот режим импорта не включен по умолчанию, но его можно легко включить, например, с помощью `/importXmlTypes` переключения командной строки в [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Это подробно описано в статье [Импорт схемы для создания классов](importing-schema-to-generate-classes.md). Обратите внимание, что работать нужно непосредственно с XML собственных экземпляров типа. Кроме того, следует принимать во внимание другую технологию сериализации, поддерживающую широкий диапазон схем - см. раздел, посвященный использованию `XmlSerializer`.

- Возможно, вам понадобится повторно использовать существующие типы `IXmlSerializable` в прокси, вместо того чтобы создавать новые. В таком случае для указания типа для повторного использования может использоваться функция ссылочных типов, описанная в разделе «Импорт схемы для создания типов». Это соответствует использованию параметра `/reference` программы svcutil.exe, указывающего на сборку, которая содержит типы для повторного использования.

### <a name="xmlserializer-legacy-behavior"></a>Поведение предыдущих версий XmlSerializer

В .NET Framework 4.0 и более ранних версиях XmlSerializer формировал временные сборки сериализации путем записи кода C# в файл. Затем файл компилировался в сборку.  Это имело некоторые нежелательные последствия, например замедление времени запуска для сериализатора. В .NET Framework 4.5 сборки формируются без использования компилятора. Некоторым разработчикам может потребоваться просмотр сформированного кода C#. Вернуться к поведению предыдущих версий можно с помощью следующих настроек:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.xml.serialization>
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />
  </system.xml.serialization>
  <system.diagnostics>
    <switches>
      <add name="XmlSerialization.Compilation" value="1" />
    </switches>
  </system.diagnostics>
</configuration>
```

При возникновении проблем совместимости, таких как `XmlSerializer` сбой сериализации производного класса с неоткрытым новым переопределением, можно переключиться обратно на `XMLSerializer` прежнее поведение, используя следующую конфигурацию:

```xml
<configuration>
  <appSettings>
    <add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />
  </appSettings>
</configuration>
```

В качестве альтернативы описанной выше конфигурации можно использовать следующую конфигурацию на компьютере с .NET Framework 4,5 или более поздней версии:

```xml
<configuration>
  <system.xml.serialization>
    <xmlSerializer useLegacySerializerGeneration="true"/>
  </system.xml.serialization>
</configuration>
```

> [!NOTE]
> `<xmlSerializer useLegacySerializerGeneration="true"/>`Коммутатор работает только на компьютере с .NET Framework 4,5 или более поздней версии. Описанный выше `appSettings` подход работает со всеми .NET Framework версиями.

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Задание передачи данных в контрактах служб](specifying-data-transfer-in-service-contracts.md)
- [Использование контрактов данных](using-data-contracts.md)
- [Практическое руководство. Сокращение времени запуска клиентских приложений WCF с использованием XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
