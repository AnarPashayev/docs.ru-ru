---
title: Справочник по C#. Предложение let
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: a6eee9a23fa28b78343e6479106eaa24ecf4caa6
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795369"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="1506c-102">Предложение let (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="1506c-102">let clause (C# Reference)</span></span>

<span data-ttu-id="1506c-103">В выражении запроса иногда требуется сохранить результат вложенного выражения, который будет использоваться в последующих предложениях.</span><span class="sxs-lookup"><span data-stu-id="1506c-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="1506c-104">Это можно сделать с помощью ключевого слова `let`, которое создает новую переменную диапазона и инициализирует ее, используя результат предоставленного выражения.</span><span class="sxs-lookup"><span data-stu-id="1506c-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="1506c-105">После инициализации с использованием этого значения такую переменную диапазона нельзя использовать для хранения других значений.</span><span class="sxs-lookup"><span data-stu-id="1506c-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="1506c-106">Тем не менее если переменная диапазона хранит запрашиваемый тип, к ней можно выполнять запросы.</span><span class="sxs-lookup"><span data-stu-id="1506c-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="1506c-107">Пример</span><span class="sxs-lookup"><span data-stu-id="1506c-107">Example</span></span>

<span data-ttu-id="1506c-108">В следующем примере показываются два способа использования `let`:</span><span class="sxs-lookup"><span data-stu-id="1506c-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="1506c-109">Создание перечисляемого типа, к которому можно выполнять запросы.</span><span class="sxs-lookup"><span data-stu-id="1506c-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="1506c-110">Реализация запроса с однократным вызовом `ToLower` для переменной диапазона `word`.</span><span class="sxs-lookup"><span data-stu-id="1506c-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="1506c-111">Если ключевое слово `let` не используется, потребуется выполнять вызов `ToLower` в каждом предикате предложения `where`.</span><span class="sxs-lookup"><span data-stu-id="1506c-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="1506c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="1506c-112">See also</span></span>

- [<span data-ttu-id="1506c-113">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="1506c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1506c-114">Ключевые слова запроса (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1506c-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="1506c-115">LINQ в C#</span><span class="sxs-lookup"><span data-stu-id="1506c-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="1506c-116">LINQ</span><span class="sxs-lookup"><span data-stu-id="1506c-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="1506c-117">Обработка исключений в выражениях запросов</span><span class="sxs-lookup"><span data-stu-id="1506c-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
