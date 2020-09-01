---
description: Справочник по C#. Ключевое слово protected
title: Справочник по C#. Ключевое слово protected
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 4c18d1f2f45a0a154dccd42736a01874dd1af853
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122385"
---
# <a name="protected-c-reference"></a><span data-ttu-id="14e33-103">protected (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="14e33-103">protected (C# Reference)</span></span>

<span data-ttu-id="14e33-104">Ключевое слово `protected` является модификатором доступа к члену.</span><span class="sxs-lookup"><span data-stu-id="14e33-104">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="14e33-105">Эта страница содержит доступ `protected`.</span><span class="sxs-lookup"><span data-stu-id="14e33-105">This page covers `protected` access.</span></span> <span data-ttu-id="14e33-106">Ключевое слово `protected` также является частью модификаторов доступа [`protected internal`](protected-internal.md) и [`private protected`](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="14e33-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="14e33-107">Доступ к защищенному элементу может быть получен из соответствующего класса, а также экземплярами производных классов.</span><span class="sxs-lookup"><span data-stu-id="14e33-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="14e33-108">Сравнение модификатора `protected` с другими модификаторами доступа см. в разделе [Уровни доступности](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="14e33-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="14e33-109">Пример</span><span class="sxs-lookup"><span data-stu-id="14e33-109">Example</span></span>

<span data-ttu-id="14e33-110">Доступ к защищенному элементу базового класса может быть получен в производном классе, только если доступ осуществляется через тип производного класса.</span><span class="sxs-lookup"><span data-stu-id="14e33-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="14e33-111">Для примера рассмотрим следующий сегмент кода:</span><span class="sxs-lookup"><span data-stu-id="14e33-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="14e33-112">Оператор `a.x = 10` вызывает ошибку, поскольку выполняется в статическом методе Main, а не в экземпляре класса Б.</span><span class="sxs-lookup"><span data-stu-id="14e33-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="14e33-113">Элементы структуры защитить нельзя, поскольку структура не может наследоваться.</span><span class="sxs-lookup"><span data-stu-id="14e33-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="14e33-114">Пример</span><span class="sxs-lookup"><span data-stu-id="14e33-114">Example</span></span>

<span data-ttu-id="14e33-115">В этом примере класс `DerivedPoint` является производным от класса `Point`.</span><span class="sxs-lookup"><span data-stu-id="14e33-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="14e33-116">В связи с этим доступ к защищенным элементам базового класса можно получить напрямую из производного класса.</span><span class="sxs-lookup"><span data-stu-id="14e33-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="14e33-117">Если изменить уровни доступа `x` и `y` на [private](private.md), компилятор выдаст сообщения об ошибках:</span><span class="sxs-lookup"><span data-stu-id="14e33-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="14e33-118">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="14e33-118">C# language specification</span></span>  

<span data-ttu-id="14e33-119">Дополнительные сведения см. в разделе [Объявленная доступность](~/_csharplang/spec/basic-concepts.md#declared-accessibility) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="14e33-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="14e33-120">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="14e33-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="14e33-121">См. также</span><span class="sxs-lookup"><span data-stu-id="14e33-121">See also</span></span>

- [<span data-ttu-id="14e33-122">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="14e33-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="14e33-123">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="14e33-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="14e33-124">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="14e33-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="14e33-125">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="14e33-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="14e33-126">Уровни доступности</span><span class="sxs-lookup"><span data-stu-id="14e33-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="14e33-127">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="14e33-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="14e33-128">public</span><span class="sxs-lookup"><span data-stu-id="14e33-128">public</span></span>](public.md)
- [<span data-ttu-id="14e33-129">private</span><span class="sxs-lookup"><span data-stu-id="14e33-129">private</span></span>](private.md)
- [<span data-ttu-id="14e33-130">internal</span><span class="sxs-lookup"><span data-stu-id="14e33-130">internal</span></span>](internal.md)
- <span data-ttu-id="14e33-131">[Вопросы безопасности, связанные с использованием ключевых слов internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14e33-131">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
