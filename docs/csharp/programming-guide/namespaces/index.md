---
title: Руководство по программированию на C#. Пространства имен
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: cf5a7f239cf7d3cd3a6e39f31d16adb830646afc
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039497"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="cfffe-102">Пространства имен (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="cfffe-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="cfffe-103">Пространства имен часто используются в программировании на C# двумя способами.</span><span class="sxs-lookup"><span data-stu-id="cfffe-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="cfffe-104">Первый способ — платформа .NET Framework использует пространства имен для упорядочения множества ее классов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cfffe-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="cfffe-105">`System` является пространством имен, а `Console` — это класс в нем.</span><span class="sxs-lookup"><span data-stu-id="cfffe-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="cfffe-106">Можно использовать ключевое слово `using`, и тогда полное имя не потребуется. См. следующий пример:</span><span class="sxs-lookup"><span data-stu-id="cfffe-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="cfffe-107">См. дополнительные сведения о [директиве using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="cfffe-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="cfffe-108">Второй способ — объявление собственных пространств имен поможет вам контролировать область имен классов и методов в более крупных проектах.</span><span class="sxs-lookup"><span data-stu-id="cfffe-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="cfffe-109">Используйте ключевое слово [namespace](../../language-reference/keywords/namespace.md), чтобы объявить пространство имен, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="cfffe-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="cfffe-110">Имя пространства имен должно быть допустимым [именем идентификатора](../inside-a-program/identifier-names.md) C#.</span><span class="sxs-lookup"><span data-stu-id="cfffe-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="cfffe-111">Обзор пространств имен</span><span class="sxs-lookup"><span data-stu-id="cfffe-111">Namespaces Overview</span></span>  

<span data-ttu-id="cfffe-112">Пространства имен имеют следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="cfffe-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="cfffe-113">Они помогают упорядочивать проекты с большим объемом кода.</span><span class="sxs-lookup"><span data-stu-id="cfffe-113">They organize large code projects.</span></span>  
- <span data-ttu-id="cfffe-114">Они разделяются оператором `.`.</span><span class="sxs-lookup"><span data-stu-id="cfffe-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="cfffe-115">Директива `using` позволяет не указывать название пространства имен для каждого класса.</span><span class="sxs-lookup"><span data-stu-id="cfffe-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="cfffe-116">Пространство имен `global` является корневым: `global::System` всегда будет ссылаться на пространство имен <xref:System> в .NET.</span><span class="sxs-lookup"><span data-stu-id="cfffe-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="cfffe-117">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="cfffe-117">C# language specification</span></span>

<span data-ttu-id="cfffe-118">Дополнительные сведения см. в статье [Пространства имен](~/_csharplang/spec/namespaces.md) в разделе [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cfffe-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cfffe-119">См. также</span><span class="sxs-lookup"><span data-stu-id="cfffe-119">See also</span></span>

- [<span data-ttu-id="cfffe-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="cfffe-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cfffe-121">Использование пространств имен</span><span class="sxs-lookup"><span data-stu-id="cfffe-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="cfffe-122">Практическое руководство. Использование пространства имен My</span><span class="sxs-lookup"><span data-stu-id="cfffe-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="cfffe-123">Имена идентификаторов</span><span class="sxs-lookup"><span data-stu-id="cfffe-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="cfffe-124">Директива using</span><span class="sxs-lookup"><span data-stu-id="cfffe-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="cfffe-125">:: Оператор</span><span class="sxs-lookup"><span data-stu-id="cfffe-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
