---
title: Руководство по программированию на C#. Буферы фиксированного размера
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5bfd9f3f559e4780b910a2e5a3430b08a2183ee3
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833503"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="a6dcd-102">Буферы фиксированного размера (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="a6dcd-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="a6dcd-103">В языке C# для создания буфера с массивом фиксированного размера в структуре данных можно использовать оператор [fixed](../../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a6dcd-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="a6dcd-104">Буферы фиксированного размера полезны при написании методов, взаимодействующих с источниками данных, созданными на других языках или платформах.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="a6dcd-105">Фиксированный массив может принимать любые атрибуты или модификаторы, допустимые для обычных членов структуры.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="a6dcd-106">Единственным ограничением является то, что массив должен иметь тип `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` или `double`.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="a6dcd-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="a6dcd-107">Remarks</span></span>

<span data-ttu-id="a6dcd-108">В безопасном коде структура C#, содержащая массив, не содержит элементы массива.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="a6dcd-109">Вместо этого в ней присутствуют ссылки на элементы.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="a6dcd-110">Вы можете внедрить массив фиксированного размера в [структуру](../../language-reference/keywords/struct.md), если он используется в блоке [небезопасного](../../language-reference/keywords/unsafe.md) кода.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="a6dcd-111">Размер следующего типа `struct` составляет 8 байт.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="a6dcd-112">Массив `pathName` является ссылкой:</span><span class="sxs-lookup"><span data-stu-id="a6dcd-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="a6dcd-113">`struct` может содержать внедренный массив в небезопасном коде.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="a6dcd-114">В приведенном ниже примере массив `fixedBuffer` имеет фиксированный размер.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="a6dcd-115">Для установки указателя на первый элемент используется оператор `fixed`.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="a6dcd-116">С помощью этого указателя осуществляется доступ к элементам массива.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="a6dcd-117">Оператор `fixed` закрепляет поле экземпляра `fixedBuffer` в определенном месте в памяти.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="a6dcd-118">Размер массива из 128 элементов `char` составляет 256 байт.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="a6dcd-119">В буферах типа [char](../../language-reference/keywords/char.md) фиксированного размера на один символ всегда приходится два байта независимо от кодировки.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="a6dcd-120">Это справедливо даже в том случае, когда буферы char маршалируются в методы API или структуры с `CharSet = CharSet.Auto` или `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="a6dcd-121">Для получения дополнительной информации см. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="a6dcd-122">В предыдущем примере демонстрировался доступ к полям `fixed` без закрепления в памяти, доступный в C#, начиная с версии 7.3.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="a6dcd-123">Еще одним распространенным массивом фиксированного размера является массив [bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="a6dcd-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="a6dcd-124">Элементы в массиве `bool` всегда имеют размер в один байт.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="a6dcd-125">Массивы `bool` не подходят для создания битовых массивов или буферов.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="a6dcd-126">За исключением памяти, созданной с помощью [stackalloc](../../language-reference/operators/stackalloc.md), компилятор C# и среда CLR не выполняют проверку переполнения буфера безопасности.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="a6dcd-127">Как и при работе с любым небезопасным кодом, следует проявлять осторожность.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="a6dcd-128">Небезопасные буферы отличаются от обычных массивов указанными ниже особенностями.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="a6dcd-129">Небезопасные буферы можно использовать в небезопасном контексте.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="a6dcd-130">Небезопасные буферы — это всегда векторы или одномерные массивы.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="a6dcd-131">В объявлении массива всегда должен присутствовать счетчик, такой как `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="a6dcd-132">Использовать `char id[]` нельзя.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="a6dcd-133">Небезопасные буферы могут быть только полями экземпляров структур в небезопасном контексте.</span><span class="sxs-lookup"><span data-stu-id="a6dcd-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6dcd-134">См. также</span><span class="sxs-lookup"><span data-stu-id="a6dcd-134">See also</span></span>

- [<span data-ttu-id="a6dcd-135">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="a6dcd-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a6dcd-136">Небезопасный код и указатели</span><span class="sxs-lookup"><span data-stu-id="a6dcd-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="a6dcd-137">Оператор fixed</span><span class="sxs-lookup"><span data-stu-id="a6dcd-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="a6dcd-138">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a6dcd-138">Interoperability</span></span>](../interop/index.md)
