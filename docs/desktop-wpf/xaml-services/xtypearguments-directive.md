---
title: Директива x:TypeArguments
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432632"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="2a81b-102">Директива x:TypeArguments</span><span class="sxs-lookup"><span data-stu-id="2a81b-102">x:TypeArguments Directive</span></span>

<span data-ttu-id="2a81b-103">Передает ограничивающие аргументы типа общего для конструктора общего типа.</span><span class="sxs-lookup"><span data-stu-id="2a81b-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="2a81b-104">Использование атрибута XAML</span><span class="sxs-lookup"><span data-stu-id="2a81b-104">XAML Attribute Usage</span></span>

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a><span data-ttu-id="2a81b-105">Значения XAML</span><span class="sxs-lookup"><span data-stu-id="2a81b-105">XAML Values</span></span>

|||
|-|-|
|`object`|<span data-ttu-id="2a81b-106">Объявление элемента объекта типа XAML, которое поддерживается общим типом CLR.</span><span class="sxs-lookup"><span data-stu-id="2a81b-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="2a81b-107">Если `object` относится к типу XAML, который не из `object` пространства имен XAML по умолчанию, требуется префикс для обозначения пространства имен XAML, где `object` существует.</span><span class="sxs-lookup"><span data-stu-id="2a81b-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|
|`typeString`|<span data-ttu-id="2a81b-108">Строка, которая объявляет одно или несколько имен типа XAML строками, которая поставляет аргументы типа для общего типа CLR.</span><span class="sxs-lookup"><span data-stu-id="2a81b-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="2a81b-109">Смотрите замечания для дополнительных примечаний синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="2a81b-109">See Remarks for additional syntax notes.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a81b-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="2a81b-110">Remarks</span></span>

<span data-ttu-id="2a81b-111">В большинстве случаев типы XAML, которые `typeString` используются в качестве элемента информации в строке, являются префикатами.</span><span class="sxs-lookup"><span data-stu-id="2a81b-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="2a81b-112">Типичные типы общих ограничений <xref:System.Int32> <xref:System.String>CLR (например, и) поступают из библиотек базового класса CLR.</span><span class="sxs-lookup"><span data-stu-id="2a81b-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="2a81b-113">Эти библиотеки не отображаются в типичных пространствах имен XAML по умолчанию, и поэтому требуют отображения приставки для использования XAML.</span><span class="sxs-lookup"><span data-stu-id="2a81b-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>

<span data-ttu-id="2a81b-114">Вы можете указать несколько имен типа XAML с помощью делимитеда запятой.</span><span class="sxs-lookup"><span data-stu-id="2a81b-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>

<span data-ttu-id="2a81b-115">Если общие ограничения сами используют общие типы, аргументы типа вложенных ограничений могут содержаться скобками ().</span><span class="sxs-lookup"><span data-stu-id="2a81b-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>

<span data-ttu-id="2a81b-116">Обратите внимание, `x:TypeArguments` что это определение специфична для .NET XAML Услуги и с использованием поддержки CLR.</span><span class="sxs-lookup"><span data-stu-id="2a81b-116">Note that this definition of `x:TypeArguments` is specific to .NET XAML Services and using CLR backing.</span></span> <span data-ttu-id="2a81b-117">Определение уровня языка можно найти в [ \[разделе\] MS-XAML 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="2a81b-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="usage-examples"></a><span data-ttu-id="2a81b-118">Примеры использования</span><span class="sxs-lookup"><span data-stu-id="2a81b-118">Usage Examples</span></span>

<span data-ttu-id="2a81b-119">В этих примерах предположим, что заявлены следующие определения пространства имен XAML:</span><span class="sxs-lookup"><span data-stu-id="2a81b-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a><span data-ttu-id="2a81b-120">Список\<струнных></span><span class="sxs-lookup"><span data-stu-id="2a81b-120">List\<String></span></span>

<span data-ttu-id="2a81b-121">`<scg:List x:TypeArguments="sys:String" ...>`мгновенно новый <xref:System.Collections.Generic.List%601> с типом <xref:System.String> аргумента.</span><span class="sxs-lookup"><span data-stu-id="2a81b-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>

### <a name="dictionarystringstring"></a><span data-ttu-id="2a81b-122">Словарная\<строка, струнная></span><span class="sxs-lookup"><span data-stu-id="2a81b-122">Dictionary\<String,String></span></span>

<span data-ttu-id="2a81b-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`мгновенно новый <xref:System.Collections.Generic.Dictionary%602> с двумя <xref:System.String> аргументами типа.</span><span class="sxs-lookup"><span data-stu-id="2a81b-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>

### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="2a81b-124">Очередь<строки KeyValuePair,\<струнная>></span><span class="sxs-lookup"><span data-stu-id="2a81b-124">Queue<KeyValuePair\<String,String>></span></span>

<span data-ttu-id="2a81b-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`мгновенно <xref:System.Collections.Generic.Queue%601> новый, который имеет ограничение <xref:System.Collections.Generic.KeyValuePair%602> с внутренним испорчить <xref:System.String> <xref:System.String>аргументы типа ограничения и .</span><span class="sxs-lookup"><span data-stu-id="2a81b-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="2a81b-126">XAML 2006 и WPF Общие XAML Использования</span><span class="sxs-lookup"><span data-stu-id="2a81b-126">XAML 2006 and WPF Generic XAML Usages</span></span>

<span data-ttu-id="2a81b-127">Для использования XAML 2006 и XAML, который используется для приложений WPF, существуют следующие ограничения для `x:TypeArguments` общих типов и общих типов xAML в целом:</span><span class="sxs-lookup"><span data-stu-id="2a81b-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>

- <span data-ttu-id="2a81b-128">Только корневой элемент файла XAML может поддерживать общее использование XAML, которое ссылается на общий тип.</span><span class="sxs-lookup"><span data-stu-id="2a81b-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>

- <span data-ttu-id="2a81b-129">Корневой элемент должен отображаться на общем типе, по крайней мере, с аргументом одного типа.</span><span class="sxs-lookup"><span data-stu-id="2a81b-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="2a81b-130">Например, <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="2a81b-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="2a81b-131">Функции страницы являются основным сценарием для поддержки общего использования XAML в WPF.</span><span class="sxs-lookup"><span data-stu-id="2a81b-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>

- <span data-ttu-id="2a81b-132">Элемент объекта корневого элемента XAML для общего `x:Class`элемента должен также объявить частичный класс с использованием.</span><span class="sxs-lookup"><span data-stu-id="2a81b-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="2a81b-133">Это верно даже при определении действия по сборке WPF.</span><span class="sxs-lookup"><span data-stu-id="2a81b-133">This is true even if defining a WPF build action.</span></span>

- <span data-ttu-id="2a81b-134">`x:TypeArguments`не может ссылаться на вложенные общие ограничения.</span><span class="sxs-lookup"><span data-stu-id="2a81b-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="2a81b-135">XAML 2009 или XAML 2006 без Зависимости WPF 3.0 или WPF 3.5</span><span class="sxs-lookup"><span data-stu-id="2a81b-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>

<span data-ttu-id="2a81b-136">В .NET XAML Services для XAML 2006 или XAML 2009, связанные с WPF ограничения на использование общего XAML смягчаются.</span><span class="sxs-lookup"><span data-stu-id="2a81b-136">In .NET XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="2a81b-137">Вы можете мгновенно настроить элемент общего объекта в любом положении в разметке XAML, которую может поддерживать система резервного типа и модель объекта.</span><span class="sxs-lookup"><span data-stu-id="2a81b-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>

<span data-ttu-id="2a81b-138">Если вы используете XAML 2009 вместо отображения типов базовых CLR для получения типов XAML для примитивов общего `typeString`языка, вы можете использовать [встроенные типы для общих примитивов языка XAML](types-for-primitives.md) в качестве элементов информации в .</span><span class="sxs-lookup"><span data-stu-id="2a81b-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](types-for-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="2a81b-139">Например, можно объявить следующее (фотофиксация не показана, но x является x-языком XAML namespace для XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="2a81b-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

<span data-ttu-id="2a81b-140">В WPF и при таргетинге .NET Framework 4 или .NET Core 3.0 (или `x:TypeArguments` позже) вы можете использовать функции XAML 2009 вместе с, но только для свободного XAML (XAML, который не разметка-компилируется).</span><span class="sxs-lookup"><span data-stu-id="2a81b-140">In WPF and when targeting .NET Framework 4 or .NET Core 3.0 (or later), you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="2a81b-141">Скомпилированный с разметкой XAML и форма BAML кода XAML в настоящее время не поддерживают ключевые слова и компоненты XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="2a81b-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="2a81b-142">Если вам нужно разметки компилировать XAML, вы должны работать в соответствии с ограничениями, отмеченные в разделе [XAML 2006 и WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages)</span><span class="sxs-lookup"><span data-stu-id="2a81b-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the [XAML 2006 and WPF Generic XAML Usages](#xaml-2006-and-wpf-generic-xaml-usages) section.</span></span> <span data-ttu-id="2a81b-143">BAML поддерживается только в рамках .NET.</span><span class="sxs-lookup"><span data-stu-id="2a81b-143">BAML is only supported in .NET Framework.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a81b-144">См. также</span><span class="sxs-lookup"><span data-stu-id="2a81b-144">See also</span></span>

- [<span data-ttu-id="2a81b-145">Директива x:Class</span><span class="sxs-lookup"><span data-stu-id="2a81b-145">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="2a81b-146">Расширение разметки x:Type</span><span class="sxs-lookup"><span data-stu-id="2a81b-146">x:Type Markup Extension</span></span>](xtype-markup-extension.md)
- [<span data-ttu-id="2a81b-147">Встроенные типы для общих примитивов языка XAML</span><span class="sxs-lookup"><span data-stu-id="2a81b-147">Built-in Types for Common XAML Language Primitives</span></span>](types-for-primitives.md)
- [<span data-ttu-id="2a81b-148">Универсальные шаблоны в XAML</span><span class="sxs-lookup"><span data-stu-id="2a81b-148">Generics in XAML</span></span>](generics.md)
