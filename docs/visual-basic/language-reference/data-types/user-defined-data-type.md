---
title: Определяемый пользователем тип (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814202"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="11e38-102">Тип данных, определенный пользователем</span><span class="sxs-lookup"><span data-stu-id="11e38-102">User-Defined Data Type</span></span>
<span data-ttu-id="11e38-103">Содержит данные в формате, определяемом.</span><span class="sxs-lookup"><span data-stu-id="11e38-103">Holds data in a format you define.</span></span> <span data-ttu-id="11e38-104">`Structure` Инструкция определяет формат.</span><span class="sxs-lookup"><span data-stu-id="11e38-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="11e38-105">Предыдущие версии Visual Basic поддерживают определяемый пользователем тип (UDT).</span><span class="sxs-lookup"><span data-stu-id="11e38-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="11e38-106">Текущая версия расширяет в определяемом пользователем ТИПЕ *структуры*.</span><span class="sxs-lookup"><span data-stu-id="11e38-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="11e38-107">Структура — это объединение одного или нескольких *члены* различных типов данных.</span><span class="sxs-lookup"><span data-stu-id="11e38-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="11e38-108">Visual Basic обрабатывает структуру как единое целое, несмотря на то, что можно получить также доступ к членам по отдельности.</span><span class="sxs-lookup"><span data-stu-id="11e38-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11e38-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="11e38-109">Remarks</span></span>  
 <span data-ttu-id="11e38-110">Определение и использование типом структуры данных, при необходимости для объединения различных типов данных в единое целое, или если ни один из простых типов данных целей.</span><span class="sxs-lookup"><span data-stu-id="11e38-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="11e38-111">Значение по умолчанию типа структуры данных состоит из сочетания значений по умолчанию для всех его членов.</span><span class="sxs-lookup"><span data-stu-id="11e38-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="11e38-112">Формат объявления</span><span class="sxs-lookup"><span data-stu-id="11e38-112">Declaration Format</span></span>  
 <span data-ttu-id="11e38-113">Объявление структуры начинается с [оператор Structure](../../../visual-basic/language-reference/statements/structure-statement.md) и заканчивается `End Structure` инструкции.</span><span class="sxs-lookup"><span data-stu-id="11e38-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="11e38-114">`Structure` Оператор содержит имя структуры, которая также является идентификатором типа данных, определение структуры.</span><span class="sxs-lookup"><span data-stu-id="11e38-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="11e38-115">Другие части кода можно использовать этот идентификатор для объявления переменных, параметров и функции возвращают значения того типа данных этой структуры.</span><span class="sxs-lookup"><span data-stu-id="11e38-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="11e38-116">Объявления между `Structure` и `End Structure` операторы определяют члены структуры.</span><span class="sxs-lookup"><span data-stu-id="11e38-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="11e38-117">Уровни доступа к членам</span><span class="sxs-lookup"><span data-stu-id="11e38-117">Member Access Levels</span></span>  
 <span data-ttu-id="11e38-118">Необходимо объявить каждый член с помощью [оператор Dim](../../../visual-basic/language-reference/statements/dim-statement.md) или оператор, который определяет уровень доступа, такие как [открытый](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), или [Private](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="11e38-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="11e38-119">Если вы используете `Dim` инструкции, по умолчанию уровня доступа к общедоступным.</span><span class="sxs-lookup"><span data-stu-id="11e38-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="11e38-120">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="11e38-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="11e38-121">**Потребление памяти.**</span><span class="sxs-lookup"><span data-stu-id="11e38-121">**Memory Consumption.**</span></span> <span data-ttu-id="11e38-122">Как и в случае всех составных типов данных, нельзя вычислить безопасно общее потребление памяти структуры путем сложения распределения Номинальное дисковое его членов.</span><span class="sxs-lookup"><span data-stu-id="11e38-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="11e38-123">Кроме того нельзя рассчитывать на безопасно порядок элементов в памяти: так же, как порядок их объявления.</span><span class="sxs-lookup"><span data-stu-id="11e38-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="11e38-124">Если вам нужно управлять макетом структуры хранилища, вы можете применить <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут `Structure` инструкции.</span><span class="sxs-lookup"><span data-stu-id="11e38-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="11e38-125">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="11e38-125">**Interop Considerations.**</span></span> <span data-ttu-id="11e38-126">При взаимодействии с компонентами, которые не написаны для платформы .NET Framework, например автоматизация или COM-объектов, имейте в виду, что определяемые пользователем типы в других средах не совместимы с Visual Basic типами структуры.</span><span class="sxs-lookup"><span data-stu-id="11e38-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="11e38-127">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="11e38-127">**Widening.**</span></span> <span data-ttu-id="11e38-128">Нет автоматического преобразования в или из любого типа структуры данных.</span><span class="sxs-lookup"><span data-stu-id="11e38-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="11e38-129">Операторы преобразования можно определить для структуры с помощью [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), вы можете объявить каждый оператор преобразования быть `Widening` или `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="11e38-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="11e38-130">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="11e38-130">**Type Characters.**</span></span> <span data-ttu-id="11e38-131">Типы данных структуры не имеют знак типа литерала или знак типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="11e38-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="11e38-132">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="11e38-132">**Framework Type.**</span></span> <span data-ttu-id="11e38-133">Отсутствует соответствующий тип в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11e38-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="11e38-134">Все структуры наследуют от класса .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, но нет отдельных структура соответствует <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11e38-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e38-135">Пример</span><span class="sxs-lookup"><span data-stu-id="11e38-135">Example</span></span>  
 <span data-ttu-id="11e38-136">В следующем примере демонстрируется структура объявления структуры.</span><span class="sxs-lookup"><span data-stu-id="11e38-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="11e38-137">См. также</span><span class="sxs-lookup"><span data-stu-id="11e38-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="11e38-138">Типы данных</span><span class="sxs-lookup"><span data-stu-id="11e38-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="11e38-139">Функции преобразования типов</span><span class="sxs-lookup"><span data-stu-id="11e38-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="11e38-140">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="11e38-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="11e38-141">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="11e38-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="11e38-142">Расширение</span><span class="sxs-lookup"><span data-stu-id="11e38-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="11e38-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="11e38-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="11e38-144">Структуры</span><span class="sxs-lookup"><span data-stu-id="11e38-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="11e38-145">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="11e38-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
