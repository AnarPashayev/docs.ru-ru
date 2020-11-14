---
title: Как написать настраиваемые преобразователи для сериализации JSON — .NET
description: Узнайте, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен :::no-loc(System.Text.Json):::.
ms.date: 01/10/2020
no-loc:
- ':::no-loc(System.Text.Json):::'
- ':::no-loc(Newtonsoft.Json):::'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: ba6b61232ccf7ed493fe5809e5c0b8ba21091d3d
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329811"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="24a19-103">Как написать настраиваемые преобразователи для сериализации JSON (маршалинг) в .NET</span><span class="sxs-lookup"><span data-stu-id="24a19-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="24a19-104">В этой статье показано, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен <xref::::no-loc(System.Text.Json):::>.</span><span class="sxs-lookup"><span data-stu-id="24a19-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref::::no-loc(System.Text.Json):::> namespace.</span></span> <span data-ttu-id="24a19-105">Общие сведения о `:::no-loc(System.Text.Json):::` см. в статье [Как сериализировать и десериализировать (маршалирование и демаршалирование) JSON в .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="24a19-105">For an introduction to `:::no-loc(System.Text.Json):::`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="24a19-106">*Преобразователь*  — это класс, который преобразует объект или значение в формат JSON и обратно.</span><span class="sxs-lookup"><span data-stu-id="24a19-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="24a19-107">Пространство имен `:::no-loc(System.Text.Json):::` содержит встроенные преобразователи для большинства примитивных типов, которые сопоставляются с примитивами JavaScript.</span><span class="sxs-lookup"><span data-stu-id="24a19-107">The `:::no-loc(System.Text.Json):::` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="24a19-108">Вы можете создавать настраиваемые преобразователи для следующих целей:</span><span class="sxs-lookup"><span data-stu-id="24a19-108">You can write custom converters:</span></span>

* <span data-ttu-id="24a19-109">Чтобы переопределить поведение встроенного преобразователя, используемое по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="24a19-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="24a19-110">Например, может потребоваться, чтобы значения `DateTime` были представлены в формате дд.мм.гггг вместо формата ISO 8601-1:2019 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="24a19-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="24a19-111">Для поддержки настраиваемого типа значения.</span><span class="sxs-lookup"><span data-stu-id="24a19-111">To support a custom value type.</span></span> <span data-ttu-id="24a19-112">Например, структуры `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="24a19-112">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="24a19-113">Вы также можете создать настраиваемые преобразователи для настройки или расширения `:::no-loc(System.Text.Json):::` с функциональностью, не входящей в текущий выпуск.</span><span class="sxs-lookup"><span data-stu-id="24a19-113">You can also write custom converters to customize or extend `:::no-loc(System.Text.Json):::` with functionality not included in the current release.</span></span> <span data-ttu-id="24a19-114">Далее в этой статье описываются следующие сценарии:</span><span class="sxs-lookup"><span data-stu-id="24a19-114">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="24a19-115">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="24a19-115">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="24a19-116">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="24a19-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="24a19-117">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="24a19-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="24a19-118">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="24a19-118">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="24a19-119">[Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="24a19-119">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="24a19-120">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="24a19-120">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="24a19-121">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="24a19-121">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

## <a name="custom-converter-patterns"></a><span data-ttu-id="24a19-122">Шаблоны настраиваемых преобразователей</span><span class="sxs-lookup"><span data-stu-id="24a19-122">Custom converter patterns</span></span>

<span data-ttu-id="24a19-123">Существует два шаблона для создания настраиваемого преобразователя: базовый шаблон и шаблон фабрики.</span><span class="sxs-lookup"><span data-stu-id="24a19-123">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="24a19-124">Шаблон фабрики предназначен для преобразователей, обрабатывающих типы `Enum` или открытые универсальные шаблоны.</span><span class="sxs-lookup"><span data-stu-id="24a19-124">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="24a19-125">Базовый шаблон предназначен для неуниверсальных и закрытых универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="24a19-125">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="24a19-126">Например, для преобразователей следующих типов требуется шаблон фабрики:</span><span class="sxs-lookup"><span data-stu-id="24a19-126">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="24a19-127">Ниже приведены некоторые примеры типов, которые могут быть обработаны базовым шаблоном:</span><span class="sxs-lookup"><span data-stu-id="24a19-127">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="24a19-128">Базовый шаблон создает класс, который может работать с одним типом.</span><span class="sxs-lookup"><span data-stu-id="24a19-128">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="24a19-129">Шаблон фабрики создает класс, который в среде выполнения определяет, какой конкретный тип требуется, и динамически создает соответствующий преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-129">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="24a19-130">Пример базового преобразователя</span><span class="sxs-lookup"><span data-stu-id="24a19-130">Sample basic converter</span></span>

<span data-ttu-id="24a19-131">Следующий пример представляет собой преобразователь, который переопределяет сериализацию по умолчанию для существующего типа данных.</span><span class="sxs-lookup"><span data-stu-id="24a19-131">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="24a19-132">Для свойств `DateTimeOffset` преобразователь использует формат дд.мм.гггг.</span><span class="sxs-lookup"><span data-stu-id="24a19-132">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="24a19-133">Пример преобразователя шаблона фабрики</span><span class="sxs-lookup"><span data-stu-id="24a19-133">Sample factory pattern converter</span></span>

<span data-ttu-id="24a19-134">В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="24a19-134">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="24a19-135">Код соответствует шаблону фабрики, так как первый параметр универсального типа является `Enum`, а второй — открытым.</span><span class="sxs-lookup"><span data-stu-id="24a19-135">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="24a19-136">Метод `CanConvert` возвращает `true` только для `Dictionary` с двумя универсальными параметрами, первый из которых является типом `Enum`.</span><span class="sxs-lookup"><span data-stu-id="24a19-136">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="24a19-137">Внутренний преобразователь получает существующий преобразователь для работы с любым типом, предоставленным во время выполнения для `TValue`.</span><span class="sxs-lookup"><span data-stu-id="24a19-137">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="24a19-138">Предыдущий код аналогичен тому, который приведен в разделе [Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="24a19-138">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="24a19-139">Инструкции по базовому шаблону</span><span class="sxs-lookup"><span data-stu-id="24a19-139">Steps to follow the basic pattern</span></span>

<span data-ttu-id="24a19-140">Ниже описывается, как создать преобразователь с помощью базового шаблона:</span><span class="sxs-lookup"><span data-stu-id="24a19-140">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="24a19-141">Создайте класс, производный от <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601>, где `T` — это тип для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-141">Create a class that derives from <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="24a19-142">Переопределите метод `Read`, чтобы десериализировать входящие данные JSON и преобразовать их в тип `T`.</span><span class="sxs-lookup"><span data-stu-id="24a19-142">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="24a19-143">Для чтения JSON используйте передаваемое в метод значение <xref::::no-loc(System.Text.Json):::.Utf8JsonReader>.</span><span class="sxs-lookup"><span data-stu-id="24a19-143">Use the <xref::::no-loc(System.Text.Json):::.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="24a19-144">Переопределите метод `Write` для сериализации входящего объекта типа `T`.</span><span class="sxs-lookup"><span data-stu-id="24a19-144">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="24a19-145">Для записи JSON используйте передаваемое в метод значение <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="24a19-145">Use the <xref::::no-loc(System.Text.Json):::.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="24a19-146">Переопределяйте метод `CanConvert` только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="24a19-146">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="24a19-147">Реализация по умолчанию возвращает `true`, если тип для преобразования имеет тип `T`.</span><span class="sxs-lookup"><span data-stu-id="24a19-147">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="24a19-148">Поэтому для преобразователей, поддерживающих только тип `T`, не требуется переопределять этот метод.</span><span class="sxs-lookup"><span data-stu-id="24a19-148">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="24a19-149">Пример преобразователя, в котором требуется переопределить этот метод, см. в разделе [Поддержка полиморфной десериализации](#support-polymorphic-deserialization) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="24a19-149">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="24a19-150">Вы можете ссылаться на [исходный код встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters/) в качестве эталонных реализаций для написания настраиваемых преобразователей.</span><span class="sxs-lookup"><span data-stu-id="24a19-150">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="24a19-151">Инструкции по шаблону фабрики</span><span class="sxs-lookup"><span data-stu-id="24a19-151">Steps to follow the factory pattern</span></span>

<span data-ttu-id="24a19-152">Ниже описывается, как создать преобразователь с помощью шаблона фабрики:</span><span class="sxs-lookup"><span data-stu-id="24a19-152">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="24a19-153">Создайте класс, наследующий от класса <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="24a19-153">Create a class that derives from <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="24a19-154">Переопределите метод `CanConvert`, чтобы он возвращал значение true, если преобразователь может обрабатывать этот тип.</span><span class="sxs-lookup"><span data-stu-id="24a19-154">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="24a19-155">Например, если преобразователь предназначен для `List<T>`, он может обрабатывать только `List<int>`, `List<string>` и `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="24a19-155">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="24a19-156">Переопределите метод `CreateConverter`, чтобы он возвращал экземпляр класса преобразователя, обрабатывающего тип для преобразования, который будет предоставлен во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="24a19-156">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="24a19-157">Создайте класс преобразователя с помощью метода `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="24a19-157">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="24a19-158">Шаблон фабрики необходим для открытых универсальных шаблонов, так как код для преобразования объекта в строку и обратно не совпадает для всех типов.</span><span class="sxs-lookup"><span data-stu-id="24a19-158">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="24a19-159">Преобразователь для открытого универсального типа (например, `List<T>`) должен создать преобразователь для закрытого универсального типа (например, `List<DateTime>`) в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="24a19-159">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="24a19-160">Необходимо написать код для обработки каждого закрытого универсального типа, который может обрабатывать преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-160">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="24a19-161">Тип `Enum` похож на открытый универсальный тип: преобразователь для `Enum` должен создать преобразователь для определенного типа `Enum` (например, `WeekdaysEnum`) в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="24a19-161">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="24a19-162">Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="24a19-162">Error handling</span></span>

<span data-ttu-id="24a19-163">Если необходимо вызвать исключение в коде обработки ошибок, рассмотрите возможность создания <xref::::no-loc(System.Text.Json):::.JsonException> без сообщения.</span><span class="sxs-lookup"><span data-stu-id="24a19-163">If you need to throw an exception in error-handling code, consider throwing a <xref::::no-loc(System.Text.Json):::.JsonException> without a message.</span></span> <span data-ttu-id="24a19-164">Этот тип исключения автоматически создает сообщение, содержащее путь к части JSON, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="24a19-164">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="24a19-165">Например, инструкция `throw new JsonException();` выдает сообщение об ошибке, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="24a19-165">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. :::no-loc(System.Text.Json):::.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="24a19-166">Если вы предоставляете сообщение (например, `throw new JsonException("Error occurred")`), исключение по-прежнему предоставляет путь в свойстве <xref::::no-loc(System.Text.Json):::.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="24a19-166">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref::::no-loc(System.Text.Json):::.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="24a19-167">Регистрация настраиваемого преобразователя</span><span class="sxs-lookup"><span data-stu-id="24a19-167">Register a custom converter</span></span>

<span data-ttu-id="24a19-168">*Зарегистрируйте* настраиваемый преобразователь, чтобы использовать методы `Serialize` и `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="24a19-168">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="24a19-169">Воспользуйтесь одним из перечисленных ниже подходов.</span><span class="sxs-lookup"><span data-stu-id="24a19-169">Choose one of the following approaches:</span></span>

* <span data-ttu-id="24a19-170">Добавьте экземпляр класса преобразователя в коллекцию <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24a19-170">Add an instance of the converter class to the <xref::::no-loc(System.Text.Json):::.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="24a19-171">Примените атрибут [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) к свойствам, для которых требуется настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-171">Apply the [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="24a19-172">Примените атрибут [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) к классу или структуре, представляющей настраиваемый тип значения.</span><span class="sxs-lookup"><span data-stu-id="24a19-172">Apply the [[JsonConverter]](xref::::no-loc(System.Text.Json):::.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="24a19-173">Пример регистрации — коллекция преобразователей</span><span class="sxs-lookup"><span data-stu-id="24a19-173">Registration sample - Converters collection</span></span>

<span data-ttu-id="24a19-174">Ниже приведен пример, который делает <xref:System.ComponentModel.DateTimeOffsetConverter> классом по умолчанию для свойств типа <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="24a19-174">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="24a19-175">Предположим, что вы сериализуете экземпляр следующего типа.</span><span class="sxs-lookup"><span data-stu-id="24a19-175">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="24a19-176">Ниже приведен пример выходных данных JSON, в котором показано использование настраиваемого преобразователя.</span><span class="sxs-lookup"><span data-stu-id="24a19-176">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="24a19-177">Следующий код использует тот же подход для десериализации с помощью настраиваемого преобразователя `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="24a19-177">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="24a19-178">Пример регистрации — [JsonConverter] для свойства</span><span class="sxs-lookup"><span data-stu-id="24a19-178">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="24a19-179">В следующем примере кода выбирается настраиваемый преобразователь для свойства `Date`.</span><span class="sxs-lookup"><span data-stu-id="24a19-179">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="24a19-180">В коде для сериализации `WeatherForecastWithConverterAttribute` не нужно использовать `JsonSerializeOptions.Converters`.</span><span class="sxs-lookup"><span data-stu-id="24a19-180">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="24a19-181">В коде для десериализации также не нужно использовать `Converters`.</span><span class="sxs-lookup"><span data-stu-id="24a19-181">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="24a19-182">Пример регистрации — [JsonConverter] для типа</span><span class="sxs-lookup"><span data-stu-id="24a19-182">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="24a19-183">Ниже приведен код, создающий структуру и применяющий к ней атрибут `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="24a19-183">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="24a19-184">Ниже приведен настраиваемый преобразователь для предыдущей структуры.</span><span class="sxs-lookup"><span data-stu-id="24a19-184">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="24a19-185">Атрибут `[JsonConvert]` в структуре регистрирует настраиваемый преобразователь в качестве значения по умолчанию для свойств типа `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="24a19-185">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="24a19-186">Этот преобразователь автоматически используется в свойстве `TemperatureCelsius` следующего типа при его сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-186">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="24a19-187">Очередность регистрации преобразователей</span><span class="sxs-lookup"><span data-stu-id="24a19-187">Converter registration precedence</span></span>

<span data-ttu-id="24a19-188">Во время сериализации или десериализации выбирается преобразователь для каждого элемента JSON в следующем порядке — от наивысшего приоритета к наименьшему.</span><span class="sxs-lookup"><span data-stu-id="24a19-188">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="24a19-189">Атрибут `[JsonConverter]` применяется к свойству.</span><span class="sxs-lookup"><span data-stu-id="24a19-189">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="24a19-190">Преобразователь, добавляемый в коллекцию `Converters`.</span><span class="sxs-lookup"><span data-stu-id="24a19-190">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="24a19-191">Атрибут `[JsonConverter]` применяется к настраиваемому типу значения или POCO.</span><span class="sxs-lookup"><span data-stu-id="24a19-191">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="24a19-192">Если в коллекции `Converters` зарегистрировано несколько настраиваемых преобразователей для типов, то используется первый преобразователь, возвращающий значение true для `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="24a19-192">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="24a19-193">Встроенный преобразователь выбирается только в том случае, если соответствующий настраиваемый преобразователь не зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="24a19-193">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="24a19-194">Примеры преобразователей для выполнения стандартных сценариев</span><span class="sxs-lookup"><span data-stu-id="24a19-194">Converter samples for common scenarios</span></span>

<span data-ttu-id="24a19-195">В следующих разделах приведены примеры преобразователей, в которых рассматриваются распространенные сценарии, необрабатываемые встроенными функциями.</span><span class="sxs-lookup"><span data-stu-id="24a19-195">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="24a19-196">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="24a19-196">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="24a19-197">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="24a19-197">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="24a19-198">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="24a19-198">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="24a19-199">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="24a19-199">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="24a19-200">[Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="24a19-200">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="24a19-201">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="24a19-201">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="24a19-202">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="24a19-202">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="24a19-203">Десериализация выводимых типов в свойства объекта</span><span class="sxs-lookup"><span data-stu-id="24a19-203">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="24a19-204">При десериализации в свойство типа `object` создается объект `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="24a19-204">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="24a19-205">Причина заключается в том, что десериализатор не знает, какой тип среды выполнения создать, и не пытается угадать.</span><span class="sxs-lookup"><span data-stu-id="24a19-205">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="24a19-206">Например, если свойство JSON имеет значение true, десериализатор не определит, что значение является `Boolean`, а если у элемента есть значение 01/01/2019, десериализатор не определит, что это `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="24a19-206">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="24a19-207">Определение типа может быть неточным.</span><span class="sxs-lookup"><span data-stu-id="24a19-207">Type inference can be inaccurate.</span></span> <span data-ttu-id="24a19-208">Если десериализатор анализирует число JSON, не имеющее десятичного разделителя в качестве `long`, это может привести к проблемам в виде выхода за пределы диапазона, если значение первоначально было сериализовано как `ulong` или `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="24a19-208">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="24a19-209">Анализ числа с десятичным разделителем в качестве `double` может привести к потере точности, если это число было первоначально сериализовано как `decimal`.</span><span class="sxs-lookup"><span data-stu-id="24a19-209">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="24a19-210">В следующем коде показан настраиваемый преобразователь для свойств `object` сценариев с определением типа.</span><span class="sxs-lookup"><span data-stu-id="24a19-210">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="24a19-211">Код преобразует:</span><span class="sxs-lookup"><span data-stu-id="24a19-211">The code converts:</span></span>

* <span data-ttu-id="24a19-212">`true` и `false` в `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="24a19-212">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="24a19-213">Числа без десятичного числа в `long`.</span><span class="sxs-lookup"><span data-stu-id="24a19-213">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="24a19-214">Числа с десятичным числом в `double`.</span><span class="sxs-lookup"><span data-stu-id="24a19-214">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="24a19-215">Даты в `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="24a19-215">Dates to `DateTime`</span></span>
* <span data-ttu-id="24a19-216">Строки в `string`.</span><span class="sxs-lookup"><span data-stu-id="24a19-216">Strings to `string`</span></span>
* <span data-ttu-id="24a19-217">Все остальное в `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="24a19-217">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="24a19-218">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-218">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="24a19-219">Ниже приведен пример типа со свойствами `object`.</span><span class="sxs-lookup"><span data-stu-id="24a19-219">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="24a19-220">Следующий пример JSON для десериализации содержит значения, которые будут десериализованы как `DateTime`, `long` и `string`.</span><span class="sxs-lookup"><span data-stu-id="24a19-220">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="24a19-221">Без настраиваемого преобразователя десериализация помещает `JsonElement` в каждое свойство.</span><span class="sxs-lookup"><span data-stu-id="24a19-221">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="24a19-222">В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) в пространстве имен `:::no-loc(System.Text.Json):::.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих десериализацию свойств `object`.</span><span class="sxs-lookup"><span data-stu-id="24a19-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="24a19-223">Поддержка словаря с ключом, не являющимся строкой</span><span class="sxs-lookup"><span data-stu-id="24a19-223">Support Dictionary with non-string key</span></span>

<span data-ttu-id="24a19-224">Встроенная поддержка коллекций словарей предназначена для `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="24a19-224">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="24a19-225">То есть ключ должен быть строкой.</span><span class="sxs-lookup"><span data-stu-id="24a19-225">That is, the key must be a string.</span></span> <span data-ttu-id="24a19-226">Для поддержки словаря с целым числом или другим типом в качестве ключа нужен настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-226">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="24a19-227">В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="24a19-227">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="24a19-228">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-228">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="24a19-229">Преобразователь может сериализовать и десериализировать свойство `TemperatureRanges` следующего класса, который использует `Enum`.</span><span class="sxs-lookup"><span data-stu-id="24a19-229">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="24a19-230">Выходные данные JSON из сериализации выглядят так, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="24a19-230">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="24a19-231">В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) в пространстве имен `:::no-loc(System.Text.Json):::.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих словари с ключом, не являющимся строкой.</span><span class="sxs-lookup"><span data-stu-id="24a19-231">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="24a19-232">Поддержка полиморфной десериализации</span><span class="sxs-lookup"><span data-stu-id="24a19-232">Support polymorphic deserialization</span></span>

<span data-ttu-id="24a19-233">Встроенные функции предоставляют ограниченный диапазон [полиморфной сериализации](system-text-json-how-to.md#serialize-properties-of-derived-classes), но совсем не поддерживают десериализацию.</span><span class="sxs-lookup"><span data-stu-id="24a19-233">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="24a19-234">Для десериализации требуется настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-234">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="24a19-235">Например, предположим, что имеется абстрактный базовый класс `Person` с производными классами `Employee` и `Customer`.</span><span class="sxs-lookup"><span data-stu-id="24a19-235">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="24a19-236">Полиморфная десериализации означает, что во время разработки можно указать `Person` в качестве цели десериализации, а объекты `Customer` и `Employee` в JSON правильно десериализованы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="24a19-236">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="24a19-237">Во время десериализации необходимо найти признаки, которые определяют требуемый тип в JSON.</span><span class="sxs-lookup"><span data-stu-id="24a19-237">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="24a19-238">В каждом сценарии доступны различные типы признаков.</span><span class="sxs-lookup"><span data-stu-id="24a19-238">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="24a19-239">Например, может быть доступно свойство дискриминатора или придется полагаться на присутствие или отсутствие конкретного свойства.</span><span class="sxs-lookup"><span data-stu-id="24a19-239">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="24a19-240">В текущем выпуске `:::no-loc(System.Text.Json):::` не предоставлены атрибуты для указания способов обработки сценариев полиморфной десериализации, поэтому необходимо использовать настраиваемые преобразователи.</span><span class="sxs-lookup"><span data-stu-id="24a19-240">The current release of `:::no-loc(System.Text.Json):::` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="24a19-241">В следующем коде показан базовый класс, два производных класса и настраиваемый преобразователь для них.</span><span class="sxs-lookup"><span data-stu-id="24a19-241">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="24a19-242">Преобразователь использует свойство дискриминатора для выполнения в полиморфной десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-242">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="24a19-243">Дискриминатор типа не находится в определениях классов, но создается во время сериализации и считывается во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-243">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="24a19-244">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-244">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="24a19-245">Преобразователь может десериализировать JSON, созданный с помощью того же преобразователя для сериализации, например.</span><span class="sxs-lookup"><span data-stu-id="24a19-245">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="24a19-246">Код преобразователя в предыдущем примере считывает и записывает каждое свойство вручную.</span><span class="sxs-lookup"><span data-stu-id="24a19-246">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="24a19-247">Альтернативой является вызов `Deserialize` или `Serialize` для выполнения некоторых операций.</span><span class="sxs-lookup"><span data-stu-id="24a19-247">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="24a19-248">Пример см. в [этой публикации на сайте StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="24a19-248">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="24a19-249">Поддержка кругового пути для Stack\<T></span><span class="sxs-lookup"><span data-stu-id="24a19-249">Support round trip for Stack\<T></span></span>

<span data-ttu-id="24a19-250">Если десериализовать строку JSON в объект <xref:System.Collections.Generic.Stack%601>, а затем сериализовать этот объект, содержимое стека будет организовано в обратном порядке.</span><span class="sxs-lookup"><span data-stu-id="24a19-250">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="24a19-251">Это поведение применимо к следующим типам и интерфейсу, а также пользовательским типам, производным от них:</span><span class="sxs-lookup"><span data-stu-id="24a19-251">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="24a19-252">Чтобы включить поддержку сериализации и десериализации, сохраняющей исходный порядок в стеке, требуется пользовательский преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-252">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="24a19-253">В следующем коде показан пользовательский преобразователь, включающий поддержку кругового пути для объектов `Stack<T>`:</span><span class="sxs-lookup"><span data-stu-id="24a19-253">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="24a19-254">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="24a19-254">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="handle-null-values"></a><span data-ttu-id="24a19-255">Обработка значений NULL</span><span class="sxs-lookup"><span data-stu-id="24a19-255">Handle null values</span></span>

<span data-ttu-id="24a19-256">По умолчанию сериализатор обрабатывает значения NULL следующим образом:</span><span class="sxs-lookup"><span data-stu-id="24a19-256">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="24a19-257">Для ссылочных типов и типов `Nullable<T>`:</span><span class="sxs-lookup"><span data-stu-id="24a19-257">For reference types and `Nullable<T>` types:</span></span>

  * <span data-ttu-id="24a19-258">Не передает `null` в пользовательские преобразователи для сериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-258">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="24a19-259">Не передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-259">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="24a19-260">Возвращает экземпляр `null` при десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-260">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="24a19-261">Записывает `null` непосредственно с помощью модуля записи при сериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-261">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="24a19-262">Для типов значений, не допускающих значения NULL:</span><span class="sxs-lookup"><span data-stu-id="24a19-262">For non-nullable value types:</span></span>

  * <span data-ttu-id="24a19-263">Передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации.</span><span class="sxs-lookup"><span data-stu-id="24a19-263">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="24a19-264">(Если пользовательский преобразователь недоступен, внутренний преобразователь для типа выдает исключение `JsonException`.)</span><span class="sxs-lookup"><span data-stu-id="24a19-264">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="24a19-265">Это поведение обработки значений NULL в основном предназначено для оптимизации производительности путем пропуска дополнительного вызова преобразователя.</span><span class="sxs-lookup"><span data-stu-id="24a19-265">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="24a19-266">Кроме того, оно позволяет избежать принудительного выполнения преобразователей для типов, допускающих значение null, для проверки `null` в начале каждого переопределения метода `Read` и `Write`.</span><span class="sxs-lookup"><span data-stu-id="24a19-266">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="24a19-267">Чтобы разрешить пользовательскому преобразователю обработку `null` для ссылочного типа или типа значения, переопределите <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType>, чтобы возвратить `true`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="24a19-267">To enable a custom converter to handle `null` for a reference or value type, override <xref::::no-loc(System.Text.Json):::.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="24a19-268">Другие примеры настраиваемых преобразователей</span><span class="sxs-lookup"><span data-stu-id="24a19-268">Other custom converter samples</span></span>

<span data-ttu-id="24a19-269">В статье о [миграции из :::no-loc(Newtonsoft.Json)::: в :::no-loc(System.Text.Json):::](system-text-json-migrate-from-newtonsoft-how-to.md) приведены дополнительные примеры настраиваемых преобразователей.</span><span class="sxs-lookup"><span data-stu-id="24a19-269">The [Migrate from :::no-loc(Newtonsoft.Json)::: to :::no-loc(System.Text.Json):::](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="24a19-270">В [папке модульных тестов](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) в исходном коде `:::no-loc(System.Text.Json):::.Serialization` есть и другие примеры настраиваемых преобразователей, например:</span><span class="sxs-lookup"><span data-stu-id="24a19-270">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/) in the `:::no-loc(System.Text.Json):::.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="24a19-271">[Преобразователь Int32, который преобразовывает значение NULL в 0 при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.NullValueType.cs).</span><span class="sxs-lookup"><span data-stu-id="24a19-271">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="24a19-272">[Преобразователь Int32, который допускает как строковые, так и числовые значения при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Int32.cs).</span><span class="sxs-lookup"><span data-stu-id="24a19-272">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="24a19-273">[Преобразователь Enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Enum.cs).</span><span class="sxs-lookup"><span data-stu-id="24a19-273">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="24a19-274">Преобразователь [List\<T>, который принимает внешние данные](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="24a19-274">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="24a19-275">[Преобразователь Long[], который работает с разделенным запятыми списком чисел](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="24a19-275">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="24a19-276">Если необходимо создать преобразователь, изменяющий поведение существующего встроенного преобразователя, можно получить [исходный код существующего преобразователя](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters) в качестве отправной точки для настройки.</span><span class="sxs-lookup"><span data-stu-id="24a19-276">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="24a19-277">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="24a19-277">Additional resources</span></span>

* <span data-ttu-id="24a19-278">[Исходный код для встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="24a19-278">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="24a19-279">Поддержка DateTime и DateTimeOffset в :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="24a19-279">DateTime and DateTimeOffset support in :::no-loc(System.Text.Json):::</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="24a19-280">Общие сведения о :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="24a19-280">:::no-loc(System.Text.Json)::: overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="24a19-281">Как использовать :::no-loc(System.Text.Json):::</span><span class="sxs-lookup"><span data-stu-id="24a19-281">How to use :::no-loc(System.Text.Json):::</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="24a19-282">Как выполнить миграцию из :::no-loc(Newtonsoft.Json):::</span><span class="sxs-lookup"><span data-stu-id="24a19-282">How to migrate from :::no-loc(Newtonsoft.Json):::</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* <span data-ttu-id="24a19-283">[Справочник по API :::no-loc(System.Text.Json):::](xref::::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="24a19-283">[:::no-loc(System.Text.Json)::: API reference](xref::::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="24a19-284">[Справочник по API :::no-loc(System.Text.Json):::.Serialization](xref::::no-loc(System.Text.Json):::.Serialization)</span><span class="sxs-lookup"><span data-stu-id="24a19-284">[:::no-loc(System.Text.Json):::.Serialization API reference](xref::::no-loc(System.Text.Json):::.Serialization)</span></span>
<!-- * [:::no-loc(System.Text.Json)::: roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/roadmap/README.md)-->
