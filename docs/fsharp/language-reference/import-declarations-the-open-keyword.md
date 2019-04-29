---
title: 'Объявления импорта: Ключевое слово open'
description: Дополнительные сведения о F# импорта, объявления и как указать модуль или пространство имен, элементы которого можно ссылаться без использования полного имени.
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937505"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="6ffd4-103">Объявления импорта: `open` Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="6ffd4-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="6ffd4-104">Ссылки на справочник по API в этой статье ведут на сайт MSDN.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="6ffd4-105">Работа над справочником по API docs.microsoft.com не завершена.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="6ffd4-106">*Объявление импорта* указывает модуль или пространство имен, элементы которого можно ссылаться без использования полного имени.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ffd4-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ffd4-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="6ffd4-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="6ffd4-108">Remarks</span></span>

<span data-ttu-id="6ffd4-109">Ссылки на код, используя полное имя пространства имен или модуля путь каждый раз можно создать код, который сложно написать, чтение и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="6ffd4-110">Вместо этого можно использовать `open` ключевое слово для часто используемых модулей и пространств имен, чтобы при ссылке на член этого модуля или пространства имен, а не полное доменное имя можно использовать краткую форму имени.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="6ffd4-111">Это ключевое слово аналогичен `using` ключевого слова C# `using namespace` в Visual C++ и `Imports` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="6ffd4-112">Модуль или пространство имен должно быть в одном проекте или в указанном проекте или сборке.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="6ffd4-113">Если это не так, можно добавить ссылку на проект или использовать `-reference` команда`-`параметр командной строки (или ее сокращением `-r`).</span><span class="sxs-lookup"><span data-stu-id="6ffd4-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="6ffd4-114">Дополнительные сведения см. в разделе [Параметры компилятора](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="6ffd4-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="6ffd4-115">Объявление импорта доступны имена в коде ниже объявления, до конца строки включающего пространства имен, модуля или файл.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="6ffd4-116">При использовании нескольких объявления импорта, они должны отображаться на разных строках.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="6ffd4-117">В следующем коде показано использование `open` ключевое слово для упрощения кода.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="6ffd4-118">F# Компилятор не выдает ошибку или предупреждение в таких случаях, когда происходит тем же именем в более чем одной откройте модуль или пространство имен.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="6ffd4-119">В таких случаях F# отдает предпочтение более недавно открывавшихся модуль или пространство имен.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="6ffd4-120">Например, в следующем коде `empty` означает `Seq.empty`, даже если `empty` имеется как `List` и `Seq` модулей.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="6ffd4-121">Поэтому будьте внимательны при открытии модулей или пространств имен такие как `List` или `Seq` , содержащие члены, которые имеют одинаковые имена, вместо этого рекомендуется использовать полные имена.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="6ffd4-122">Следует избегать любой ситуации, в котором код зависит от порядка объявления импорта.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="6ffd4-123">Пространства имен, открываемые по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6ffd4-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="6ffd4-124">Некоторые пространства имен настолько часто используются в F# кода, что они открываются автоматически, без необходимости объявления явный Импорт.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="6ffd4-125">В следующей таблице показаны пространства имен, открываемые по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="6ffd4-126">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="6ffd4-126">Namespace</span></span>|<span data-ttu-id="6ffd4-127">Описание</span><span class="sxs-lookup"><span data-stu-id="6ffd4-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="6ffd4-128">Содержит основные F# введите определения для встроенных типов, таких как `int` и `float`.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="6ffd4-129">Содержит основные арифметические операции, такие как `+` и `*`.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="6ffd4-130">Содержит неизменяемые классы коллекций, такие как `List` и `Array`.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="6ffd4-131">Содержит типы для управления конструкций, таких как отложенная оценка и асинхронные рабочие потоки.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="6ffd4-132">Содержит функции для форматирования ввода/ВЫВОДА, такие как `printf` функции.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="6ffd4-133">AutoOpen-атрибут</span><span class="sxs-lookup"><span data-stu-id="6ffd4-133">AutoOpen Attribute</span></span>

<span data-ttu-id="6ffd4-134">Можно применить `AutoOpen` атрибут к сборке, чтобы автоматически открыть пространства имен или модуля, при ссылке на сборку.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="6ffd4-135">Можно также применить `AutoOpen` для модуля, чтобы автоматически открывать его при открытии родительского модуля или пространства имен атрибута.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="6ffd4-136">Дополнительные сведения см. в разделе [класс Core.AutoOpenAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="6ffd4-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="6ffd4-137">RequireQualifiedAccess-атрибут</span><span class="sxs-lookup"><span data-stu-id="6ffd4-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="6ffd4-138">Некоторые модули, записей или типы объединений могут указать `RequireQualifiedAccess` атрибута.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="6ffd4-139">При ссылке на элементы из этих модулей, записи или объединения, необходимо использовать полное имя независимо от того, следует ли включать объявление импорта.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="6ffd4-140">Если вы используете этот атрибут стратегически на типы, определяющие часто используемые имена, поможет избежать конфликтов имен и тем самым сделать код более устойчивым к изменениям в библиотеках.</span><span class="sxs-lookup"><span data-stu-id="6ffd4-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="6ffd4-141">Дополнительные сведения см. в разделе [класс Core.RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="6ffd4-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ffd4-142">См. также</span><span class="sxs-lookup"><span data-stu-id="6ffd4-142">See also</span></span>

- [<span data-ttu-id="6ffd4-143">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="6ffd4-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6ffd4-144">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="6ffd4-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="6ffd4-145">Модули</span><span class="sxs-lookup"><span data-stu-id="6ffd4-145">Modules</span></span>](modules.md)
