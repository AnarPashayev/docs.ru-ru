---
title: Как написать настраиваемые преобразователи для сериализации JSON — .NET
description: Узнайте, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен System.Text.Json.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33334ccd8bad4ac5a9f5dccde79ff3ae09ca8f89
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008868"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>Как написать настраиваемые преобразователи для сериализации JSON (маршалинг) в .NET

В этой статье показано, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен <xref:System.Text.Json>. Общие сведения о `System.Text.Json` см. в статье [Как сериализировать и десериализировать (маршалирование и демаршалирование) JSON в .NET](system-text-json-how-to.md).

*Преобразователь* — это класс, который преобразует объект или значение в формат JSON и обратно. Пространство имен `System.Text.Json` содержит встроенные преобразователи для большинства примитивных типов, которые сопоставляются с примитивами JavaScript. Вы можете создавать настраиваемые преобразователи для следующих целей:

* Чтобы переопределить поведение встроенного преобразователя, используемое по умолчанию. Например, может потребоваться, чтобы значения `DateTime` были представлены в формате "мм/дд/гггг". По умолчанию поддерживается стандарт ISO 8601-1:2019, включая профиль RFC 3339. Дополнительные сведения см. в разделе [Поддержка DateTime и DateTimeOffset в System.Text.Json](../datetime/system-text-json-support.md).
* Для поддержки настраиваемого типа значения. Например, структуры `PhoneNumber`.

Вы также можете создать настраиваемые преобразователи для настройки или расширения `System.Text.Json` с функциональностью, не входящей в текущий выпуск. Далее в этой статье описываются следующие сценарии:

::: zone pivot="dotnet-5-0"

* [Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).
* [Поддержка полиморфной десериализации](#support-polymorphic-deserialization).
* [Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).
* [Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).
* [Поддержка полиморфной десериализации](#support-polymorphic-deserialization).
* [Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).
::: zone-end

При написании кода настраиваемого преобразователя помните о значительном снижении производительности при использовании новых экземпляров <xref:System.Text.Json.JsonSerializerOptions>. Дополнительные сведения см. в разделе [Повторное использование экземпляров JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).

## <a name="custom-converter-patterns"></a>Шаблоны настраиваемых преобразователей

Существует два шаблона для создания настраиваемого преобразователя: базовый шаблон и шаблон фабрики. Шаблон фабрики предназначен для преобразователей, обрабатывающих типы `Enum` или открытые универсальные шаблоны. Базовый шаблон предназначен для неуниверсальных и закрытых универсальных типов.  Например, для преобразователей следующих типов требуется шаблон фабрики:

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

Ниже приведены некоторые примеры типов, которые могут быть обработаны базовым шаблоном:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

Базовый шаблон создает класс, который может работать с одним типом. Шаблон фабрики создает класс, который в среде выполнения определяет, какой конкретный тип требуется, и динамически создает соответствующий преобразователь.

## <a name="sample-basic-converter"></a>Пример базового преобразователя

Следующий пример представляет собой преобразователь, который переопределяет сериализацию по умолчанию для существующего типа данных. Для свойств `DateTimeOffset` преобразователь использует формат дд.мм.гггг.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a>Пример преобразователя шаблона фабрики

В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`. Код соответствует шаблону фабрики, так как первый параметр универсального типа является `Enum`, а второй — открытым. Метод `CanConvert` возвращает `true` только для `Dictionary` с двумя универсальными параметрами, первый из которых является типом `Enum`. Внутренний преобразователь получает существующий преобразователь для работы с любым типом, предоставленным во время выполнения для `TValue`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

Предыдущий код аналогичен тому, который приведен в разделе [Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key) далее в этой статье.

## <a name="steps-to-follow-the-basic-pattern"></a>Инструкции по базовому шаблону

Ниже описывается, как создать преобразователь с помощью базового шаблона:

* Создайте класс, производный от <xref:System.Text.Json.Serialization.JsonConverter%601>, где `T` — это тип для сериализации и десериализации.
* Переопределите метод `Read`, чтобы десериализировать входящие данные JSON и преобразовать их в тип `T`. Для чтения JSON используйте передаваемое в метод значение <xref:System.Text.Json.Utf8JsonReader>.
* Переопределите метод `Write` для сериализации входящего объекта типа `T`. Для записи JSON используйте передаваемое в метод значение <xref:System.Text.Json.Utf8JsonWriter>.
* Переопределяйте метод `CanConvert` только при необходимости. Реализация по умолчанию возвращает `true`, если тип для преобразования имеет тип `T`. Поэтому для преобразователей, поддерживающих только тип `T`, не требуется переопределять этот метод. Пример преобразователя, в котором требуется переопределить этот метод, см. в разделе [Поддержка полиморфной десериализации](#support-polymorphic-deserialization) далее в этой статье.

Вы можете ссылаться на [исходный код встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) в качестве эталонных реализаций для написания настраиваемых преобразователей.

## <a name="steps-to-follow-the-factory-pattern"></a>Инструкции по шаблону фабрики

Ниже описывается, как создать преобразователь с помощью шаблона фабрики:

* Создайте класс, наследующий от класса <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Переопределите метод `CanConvert`, чтобы он возвращал значение true, если преобразователь может обрабатывать этот тип. Например, если преобразователь предназначен для `List<T>`, он может обрабатывать только `List<int>`, `List<string>` и `List<DateTime>`.
* Переопределите метод `CreateConverter`, чтобы он возвращал экземпляр класса преобразователя, обрабатывающего тип для преобразования, который будет предоставлен во время выполнения.
* Создайте класс преобразователя с помощью метода `CreateConverter`.

Шаблон фабрики необходим для открытых универсальных шаблонов, так как код для преобразования объекта в строку и обратно не совпадает для всех типов. Преобразователь для открытого универсального типа (например, `List<T>`) должен создать преобразователь для закрытого универсального типа (например, `List<DateTime>`) в фоновом режиме. Необходимо написать код для обработки каждого закрытого универсального типа, который может обрабатывать преобразователь.

Тип `Enum` похож на открытый универсальный тип: преобразователь для `Enum` должен создать преобразователь для определенного типа `Enum` (например, `WeekdaysEnum`) в фоновом режиме.

## <a name="error-handling"></a>Обработка ошибок

Сериализатор обеспечивает специальную обработку типов исключений <xref:System.Text.Json.JsonException> и <xref:System.NotSupportedException>.

### <a name="jsonexception"></a>JsonException

Если выдается исключение `JsonException` без сообщения, сериализатор создает сообщение, содержащее путь к части JSON, вызвавшей ошибку. Например, инструкция `throw new JsonException()` выдает сообщение об ошибке, как в следующем примере:

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Если вы выдаете сообщение (например, `throw new JsonException("Error occurred")`), сериализатор по-прежнему устанавливает свойства <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber> и <xref:System.Text.Json.JsonException.BytePositionInLine>.

### <a name="notsupportedexception"></a>NotSupportedException

При возникновении `NotSupportedException` вы всегда получаете сведения о пути в сообщении. Если сообщение указано, сведения о пути добавляются к нему. Например, инструкция `throw new NotSupportedException("Error occurred.")` выдает сообщение об ошибке, как в следующем примере:

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a>Типы исключений, которые следует использовать в различных случаях

Если полезные данные JSON содержат токены, которые не являются допустимыми для десериализуемого типа, необходимо выдать исключение `JsonException`.

Если требуется запретить определенные типы, используйте исключение `NotSupportedException`. Это исключение автоматически выдается сериализатором для типов, которые не поддерживаются. Например, тип `System.Type` не поддерживается по соображениям безопасности, поэтому попытка десериализации приведет к исключению `NotSupportedException`.

При необходимости можно вызвать и другие исключения, но в них не будут автоматически включаться сведения о пути JSON.

## <a name="register-a-custom-converter"></a>Регистрация настраиваемого преобразователя

*Зарегистрируйте* настраиваемый преобразователь, чтобы использовать методы `Serialize` и `Deserialize`. Воспользуйтесь одним из перечисленных ниже подходов.

* Добавьте экземпляр класса преобразователя в коллекцию <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Примените атрибут [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) к свойствам, для которых требуется настраиваемый преобразователь.
* Примените атрибут [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) к классу или структуре, представляющей настраиваемый тип значения.

## <a name="registration-sample---converters-collection"></a>Пример регистрации — коллекция преобразователей

Ниже приведен пример, который делает <xref:System.ComponentModel.DateTimeOffsetConverter> классом по умолчанию для свойств типа <xref:System.DateTimeOffset>.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

Предположим, что вы сериализуете экземпляр следующего типа.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

Ниже приведен пример выходных данных JSON, в котором показано использование настраиваемого преобразователя.

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Следующий код использует тот же подход для десериализации с помощью настраиваемого преобразователя `DateTimeOffset`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a>Пример регистрации — [JsonConverter] для свойства

В следующем примере кода выбирается настраиваемый преобразователь для свойства `Date`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

В коде для сериализации `WeatherForecastWithConverterAttribute` не нужно использовать `JsonSerializeOptions.Converters`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

В коде для десериализации также не нужно использовать `Converters`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a>Пример регистрации — [JsonConverter] для типа

Ниже приведен код, создающий структуру и применяющий к ней атрибут `[JsonConverter]`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

Ниже приведен настраиваемый преобразователь для предыдущей структуры.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

Атрибут `[JsonConvert]` в структуре регистрирует настраиваемый преобразователь в качестве значения по умолчанию для свойств типа `Temperature`. Этот преобразователь автоматически используется в свойстве `TemperatureCelsius` следующего типа при его сериализации или десериализации.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a>Очередность регистрации преобразователей

Во время сериализации или десериализации выбирается преобразователь для каждого элемента JSON в следующем порядке — от наивысшего приоритета к наименьшему.

* Атрибут `[JsonConverter]` применяется к свойству.
* Преобразователь, добавляемый в коллекцию `Converters`.
* Атрибут `[JsonConverter]` применяется к настраиваемому типу значения или POCO.

Если в коллекции `Converters` зарегистрировано несколько настраиваемых преобразователей для типов, то используется первый преобразователь, возвращающий значение true для `CanConvert`.

Встроенный преобразователь выбирается только в том случае, если соответствующий настраиваемый преобразователь не зарегистрирован.

## <a name="converter-samples-for-common-scenarios"></a>Примеры преобразователей для выполнения стандартных сценариев

В следующих разделах приведены примеры преобразователей, в которых рассматриваются распространенные сценарии, необрабатываемые встроенными функциями.

::: zone pivot="dotnet-5-0"

* [Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).
* [Поддержка полиморфной десериализации](#support-polymorphic-deserialization).
* [Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).
* [Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).
* [Поддержка полиморфной десериализации](#support-polymorphic-deserialization).
* [Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a>Десериализация выводимых типов в свойства объекта

При десериализации в свойство типа `object` создается объект `JsonElement`. Причина заключается в том, что десериализатор не знает, какой тип среды выполнения создать, и не пытается угадать. Например, если свойство JSON имеет значение true, десериализатор не определит, что значение является `Boolean`, а если у элемента есть значение 01/01/2019, десериализатор не определит, что это `DateTime`.

Определение типа может быть неточным. Если десериализатор анализирует число JSON, не имеющее десятичного разделителя в качестве `long`, это может привести к проблемам в виде выхода за пределы диапазона, если значение первоначально было сериализовано как `ulong` или `BigInteger`. Анализ числа с десятичным разделителем в качестве `double` может привести к потере точности, если это число было первоначально сериализовано как `decimal`.

В следующем коде показан настраиваемый преобразователь для свойств `object` сценариев с определением типа. Код преобразует:

* `true` и `false` в `Boolean`.
* Числа без десятичного числа в `long`.
* Числа с десятичным числом в `double`.
* Даты в `DateTime`.
* Строки в `string`.
* Все остальное в `JsonElement`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

В следующем коде регистрируется преобразователь.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

Ниже приведен пример типа со свойствами `object`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

Следующий пример JSON для десериализации содержит значения, которые будут десериализованы как `DateTime`, `long` и `string`.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Без настраиваемого преобразователя десериализация помещает `JsonElement` в каждое свойство.

В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в пространстве имен `System.Text.Json.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих десериализацию свойств `object`.

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a>Поддержка словаря с ключом, не являющимся строкой

Встроенная поддержка коллекций словарей предназначена для `Dictionary<string, TValue>`. То есть ключ должен быть строкой. Для поддержки словаря с целым числом или другим типом в качестве ключа нужен настраиваемый преобразователь.

В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

В следующем коде регистрируется преобразователь.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

Преобразователь может сериализовать и десериализировать свойство `TemperatureRanges` следующего класса, который использует `Enum`.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

Выходные данные JSON из сериализации выглядят так, как показано в следующем примере.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в пространстве имен `System.Text.Json.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих словари с ключом, не являющимся строкой.
::: zone-end

### <a name="support-polymorphic-deserialization"></a>Поддержка полиморфной десериализации

Встроенные функции предоставляют ограниченный диапазон [полиморфной сериализации](system-text-json-polymorphism.md), но совсем не поддерживают десериализацию. Для десериализации требуется настраиваемый преобразователь.

Например, предположим, что имеется абстрактный базовый класс `Person` с производными классами `Employee` и `Customer`. Полиморфная десериализации означает, что во время разработки можно указать `Person` в качестве цели десериализации, а объекты `Customer` и `Employee` в JSON правильно десериализованы во время выполнения. Во время десериализации необходимо найти признаки, которые определяют требуемый тип в JSON. В каждом сценарии доступны различные типы признаков. Например, может быть доступно свойство дискриминатора или придется полагаться на присутствие или отсутствие конкретного свойства. В текущем выпуске `System.Text.Json` не предоставлены атрибуты для указания способов обработки сценариев полиморфной десериализации, поэтому необходимо использовать настраиваемые преобразователи.

В следующем коде показан базовый класс, два производных класса и настраиваемый преобразователь для них. Преобразователь использует свойство дискриминатора для выполнения в полиморфной десериализации. Дискриминатор типа не находится в определениях классов, но создается во время сериализации и считывается во время десериализации.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

В следующем коде регистрируется преобразователь.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

Преобразователь может десериализировать JSON, созданный с помощью того же преобразователя для сериализации, например.

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

Код преобразователя в предыдущем примере считывает и записывает каждое свойство вручную. Альтернативой является вызов `Deserialize` или `Serialize` для выполнения некоторых операций. Пример см. в [этой публикации на сайте StackOverflow](https://stackoverflow.com/a/59744873/12509023).

### <a name="support-round-trip-for-stackt"></a>Поддержка кругового пути для Stack\<T>

Если десериализовать строку JSON в объект <xref:System.Collections.Generic.Stack%601>, а затем сериализовать этот объект, содержимое стека будет организовано в обратном порядке. Это поведение применимо к следующим типам и интерфейсу, а также пользовательским типам, производным от них:

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

Чтобы включить поддержку сериализации и десериализации, сохраняющей исходный порядок в стеке, требуется пользовательский преобразователь.

В следующем коде показан пользовательский преобразователь, включающий поддержку кругового пути для объектов `Stack<T>`:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

В следующем коде регистрируется преобразователь.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a>Обработка значений NULL

По умолчанию сериализатор обрабатывает значения NULL следующим образом:

* Для ссылочных типов и типов <xref:System.Nullable%601>:

  * Не передает `null` в пользовательские преобразователи для сериализации.
  * Не передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации.
  * Возвращает экземпляр `null` при десериализации.
  * Записывает `null` непосредственно с помощью модуля записи при сериализации.

* Для типов значений, не допускающих значения NULL:

  * Передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации. (Если пользовательский преобразователь недоступен, внутренний преобразователь для типа выдает исключение `JsonException`.)

Это поведение обработки значений NULL в основном предназначено для оптимизации производительности путем пропуска дополнительного вызова преобразователя. Кроме того, оно позволяет избежать принудительного выполнения преобразователей для типов, допускающих значение null, для проверки `null` в начале каждого переопределения метода `Read` и `Write`.

::: zone pivot="dotnet-5-0"
Чтобы разрешить пользовательскому преобразователю обработку `null` для ссылочного типа или типа значения, переопределите <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType>, чтобы возвратить `true`, как показано в следующем примере:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a>Другие примеры настраиваемых преобразователей

В статье о [миграции из Newtonsoft.Json в System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) приведены дополнительные примеры настраиваемых преобразователей.

В [папке модульных тестов](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в исходном коде `System.Text.Json.Serialization` есть и другие примеры настраиваемых преобразователей, например:

* [Преобразователь Int32, который преобразовывает значение NULL в 0 при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs).
* [Преобразователь Int32, который допускает как строковые, так и числовые значения при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs).
* [Преобразователь Enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs).
* Преобразователь [List\<T>, который принимает внешние данные](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Преобразователь Long[], который работает с разделенным запятыми списком чисел](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

Если необходимо создать преобразователь, изменяющий поведение существующего встроенного преобразователя, можно получить [исходный код существующего преобразователя](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) в качестве отправной точки для настройки.

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Исходный код для встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [Общие сведения о System.Text.Json](system-text-json-overview.md)
* [Практическое руководство. Сериализация и десериализация JSON](system-text-json-how-to.md)
* [Создание экземпляров JsonSerializerOptions](system-text-json-configure-options.md)
* [Сопоставление без учета регистра](system-text-json-character-casing.md)
* [Настройка имен и значений свойств](system-text-json-customize-properties.md)
* [Игнорирование свойств](system-text-json-ignore-properties.md)
* [Применение недействительного кода JSON](system-text-json-invalid-json.md)
* [Обработка переполнения JSON](system-text-json-handle-overflow.md)
* [Сохранение ссылок](system-text-json-preserve-references.md)
* [Неизменяемые типы и непубличные методы доступа](system-text-json-immutability.md)
* [Полиморфная сериализация](system-text-json-polymorphism.md)
* [Миграция из Newtonsoft.Json в System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Настройка кодировки символов](system-text-json-character-encoding.md)
* [Написание пользовательских сериализаторов и десериализаторов](write-custom-serializer-deserializer.md)
* [Поддержка DateTime и DateTimeOffset](../datetime/system-text-json-support.md)
* [Справочник по API System.Text.Json](xref:System.Text.Json)
* [Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)
