---
title: Руководство по программированию на C#. Индексаторы
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167548"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="12ea2-102">Индексаторы (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="12ea2-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="12ea2-103">Индексаторы позволяют индексировать экземпляры класса или структуры точно так же, как и массивы.</span><span class="sxs-lookup"><span data-stu-id="12ea2-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="12ea2-104">Индексированное значение можно задавать или получать без явного указания типа или экземпляра элемента.</span><span class="sxs-lookup"><span data-stu-id="12ea2-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="12ea2-105">Индексаторы действуют как [свойства](../classes-and-structs/properties.md), за исключением того, что их акцессоры принимают параметры.</span><span class="sxs-lookup"><span data-stu-id="12ea2-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="12ea2-106">В следующем примере определяется универсальный класс с простыми акцессорами [get](../../language-reference/keywords/get.md) и [set](../../language-reference/keywords/set.md) для назначения и получения значений.</span><span class="sxs-lookup"><span data-stu-id="12ea2-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="12ea2-107">Класс `Program` создает экземпляр этого класса для хранения строк.</span><span class="sxs-lookup"><span data-stu-id="12ea2-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="12ea2-108">Дополнительные примеры см. в разделе [Связанные разделы](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="12ea2-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="12ea2-109">Определения текста выражений</span><span class="sxs-lookup"><span data-stu-id="12ea2-109">Expression Body Definitions</span></span>  

<span data-ttu-id="12ea2-110">Довольно часто акцессор get или set индексатора состоит из одной инструкции, которая просто возвращает или задает значение.</span><span class="sxs-lookup"><span data-stu-id="12ea2-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="12ea2-111">Члены, воплощающие выражение, предоставляют упрощенный синтаксис для поддержки такого варианта использования.</span><span class="sxs-lookup"><span data-stu-id="12ea2-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="12ea2-112">Начиная с версии C# 6, доступные только для чтения индексаторы можно реализовать в виде члена, воплощающего выражение, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="12ea2-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="12ea2-113">Обратите внимание, что `=>` представляет тело выражения, а ключевое слово `get` не используется.</span><span class="sxs-lookup"><span data-stu-id="12ea2-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="12ea2-114">Начиная с версии C# 7.0, методы доступа get и set можно реализовывать в виде членов с телом в виде выражения.</span><span class="sxs-lookup"><span data-stu-id="12ea2-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="12ea2-115">В этом случае необходимо указывать оба ключевых слова (`get` и `set`).</span><span class="sxs-lookup"><span data-stu-id="12ea2-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="12ea2-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="12ea2-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="12ea2-117">Общие сведения об индексаторах</span><span class="sxs-lookup"><span data-stu-id="12ea2-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="12ea2-118">Индексаторы позволяют индексировать объекты так же, как и массивы.</span><span class="sxs-lookup"><span data-stu-id="12ea2-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="12ea2-119">Метод доступа `get` возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="12ea2-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="12ea2-120">Метод доступа `set` назначает значение.</span><span class="sxs-lookup"><span data-stu-id="12ea2-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="12ea2-121">Ключевое слово [this](../../language-reference/keywords/this.md) используется для определения индексаторов.</span><span class="sxs-lookup"><span data-stu-id="12ea2-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="12ea2-122">Ключевое слово [value`set` используется для определения значения, присваиваемого индексатором ](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="12ea2-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="12ea2-123">Индексаторы не нужно индексировать по целому значению; пользователь может определить конкретный механизм поиска на свое усмотрение.</span><span class="sxs-lookup"><span data-stu-id="12ea2-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="12ea2-124">Индексаторы могут быть перегружены.</span><span class="sxs-lookup"><span data-stu-id="12ea2-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="12ea2-125">Индексаторы могут иметь более одного формального параметра, например при доступе к двумерному массиву.</span><span class="sxs-lookup"><span data-stu-id="12ea2-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a> <span data-ttu-id="12ea2-126">См. также</span><span class="sxs-lookup"><span data-stu-id="12ea2-126">Related Sections</span></span>  
  
- [<span data-ttu-id="12ea2-127">Использование индексаторов</span><span class="sxs-lookup"><span data-stu-id="12ea2-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="12ea2-128">Индексаторы в интерфейсах</span><span class="sxs-lookup"><span data-stu-id="12ea2-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="12ea2-129">Сравнение свойств и индексаторов</span><span class="sxs-lookup"><span data-stu-id="12ea2-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="12ea2-130">Ограничение доступности методов доступа</span><span class="sxs-lookup"><span data-stu-id="12ea2-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="12ea2-131">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="12ea2-131">C# Language Specification</span></span>  

<span data-ttu-id="12ea2-132">Дополнительные сведения см. в разделе [Индексаторы](~/_csharplang/spec/classes.md#indexers) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="12ea2-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="12ea2-133">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="12ea2-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12ea2-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="12ea2-134">See also</span></span>

- [<span data-ttu-id="12ea2-135">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="12ea2-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="12ea2-136">Свойства</span><span class="sxs-lookup"><span data-stu-id="12ea2-136">Properties</span></span>](../classes-and-structs/properties.md)
