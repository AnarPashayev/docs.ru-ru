---
title: Ключевое слово namespace. Справочник по C#
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 8cc1d1461a33ab94f8ae399d6ff40f26eaf7f74a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039448"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="9c40f-102">namespace (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="9c40f-102">namespace (C# Reference)</span></span>

<span data-ttu-id="9c40f-103">Ключевое слово `namespace` используется для объявления области действия, которая содержит набор связанных объектов.</span><span class="sxs-lookup"><span data-stu-id="9c40f-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="9c40f-104">Пространство имен можно использовать для организации элементов кода и для создания глобально уникальных типов.</span><span class="sxs-lookup"><span data-stu-id="9c40f-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="9c40f-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="9c40f-105">Remarks</span></span>

<span data-ttu-id="9c40f-106">В пространстве имен можно объявить ноль или больше следующих типов:</span><span class="sxs-lookup"><span data-stu-id="9c40f-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="9c40f-107">другое пространство имен</span><span class="sxs-lookup"><span data-stu-id="9c40f-107">another namespace</span></span>

- [<span data-ttu-id="9c40f-108">class</span><span class="sxs-lookup"><span data-stu-id="9c40f-108">class</span></span>](class.md)

- [<span data-ttu-id="9c40f-109">interface</span><span class="sxs-lookup"><span data-stu-id="9c40f-109">interface</span></span>](interface.md)

- [<span data-ttu-id="9c40f-110">struct</span><span class="sxs-lookup"><span data-stu-id="9c40f-110">struct</span></span>](struct.md)

- [<span data-ttu-id="9c40f-111">enum</span><span class="sxs-lookup"><span data-stu-id="9c40f-111">enum</span></span>](enum.md)

- [<span data-ttu-id="9c40f-112">delegate</span><span class="sxs-lookup"><span data-stu-id="9c40f-112">delegate</span></span>](delegate.md)

<span data-ttu-id="9c40f-113">Независимо от того, было ли пространство имен объявлено явным образом в исходном файле на языке C#, компилятор добавляет пространство имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9c40f-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="9c40f-114">Это безымянное пространство имен, иногда называемое глобальным пространством имен, существует в каждом файле.</span><span class="sxs-lookup"><span data-stu-id="9c40f-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="9c40f-115">Любой идентификатор в глобальном пространстве имен доступен для использования в именованном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="9c40f-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="9c40f-116">Пространства имен неявно имеют общий доступ, и это невозможно изменить.</span><span class="sxs-lookup"><span data-stu-id="9c40f-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="9c40f-117">Описание модификаторов доступа, которые можно назначить элементам в пространстве имен, см. в разделе [Модификаторы доступа](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9c40f-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="9c40f-118">Пространство имен можно определить в двух или нескольких объявлениях.</span><span class="sxs-lookup"><span data-stu-id="9c40f-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="9c40f-119">Например, в следующем примере два класса определяются в качестве части пространства имен `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="9c40f-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="9c40f-120">Пример</span><span class="sxs-lookup"><span data-stu-id="9c40f-120">Example</span></span>

<span data-ttu-id="9c40f-121">В следующем примере показано, как можно вызвать статический метод вложенного пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9c40f-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9c40f-122">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="9c40f-122">C# language specification</span></span>

<span data-ttu-id="9c40f-123">Дополнительные сведения см. в статье [Пространства имен](~/_csharplang/spec/namespaces.md) в разделе [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9c40f-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c40f-124">См. также</span><span class="sxs-lookup"><span data-stu-id="9c40f-124">See also</span></span>

- [<span data-ttu-id="9c40f-125">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="9c40f-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9c40f-126">Ключевые слова C#</span><span class="sxs-lookup"><span data-stu-id="9c40f-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="9c40f-127">using</span><span class="sxs-lookup"><span data-stu-id="9c40f-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="9c40f-128">using static</span><span class="sxs-lookup"><span data-stu-id="9c40f-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="9c40f-129">Квалификатор псевдонима пространства имен `::`</span><span class="sxs-lookup"><span data-stu-id="9c40f-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="9c40f-130">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="9c40f-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
