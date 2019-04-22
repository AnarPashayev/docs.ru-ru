---
title: Предложение Skip While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839903"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="b632b-102">Предложение Skip While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b632b-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="b632b-103">Пропускает элементы в коллекции, если заданное условие имеет значение `true`, и возвращает остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="b632b-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b632b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b632b-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b632b-105">Части</span><span class="sxs-lookup"><span data-stu-id="b632b-105">Parts</span></span>  
  
|<span data-ttu-id="b632b-106">Термин</span><span class="sxs-lookup"><span data-stu-id="b632b-106">Term</span></span>|<span data-ttu-id="b632b-107">Определение</span><span class="sxs-lookup"><span data-stu-id="b632b-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="b632b-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b632b-108">Required.</span></span> <span data-ttu-id="b632b-109">Выражение, которое представляет условие для проверки элементов.</span><span class="sxs-lookup"><span data-stu-id="b632b-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="b632b-110">Выражение должно возвращать `Boolean` значение или функциональный эквивалент, например `Integer` для оценки в качестве `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b632b-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b632b-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="b632b-111">Remarks</span></span>  
 <span data-ttu-id="b632b-112">`Skip While` Предложение пропускает элементы в начале результатов запроса до предоставленного `expression` возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="b632b-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="b632b-113">После `expression` возвращает `false`, запрос возвращает все оставшиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="b632b-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="b632b-114">`expression` Игнорируется для оставшихся результатов.</span><span class="sxs-lookup"><span data-stu-id="b632b-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="b632b-115">`Skip While` Предложение отличается от `Where` предложение, в который `Where` предложение может использоваться для исключения всех элементов из запроса, который не удовлетворяют определенному условию.</span><span class="sxs-lookup"><span data-stu-id="b632b-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="b632b-116">`Skip While` Предложение исключает элементы только до момента первого, условие не выполняется.</span><span class="sxs-lookup"><span data-stu-id="b632b-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="b632b-117">`Skip While` Предложение наиболее полезно при работе с упорядоченным результатом запроса.</span><span class="sxs-lookup"><span data-stu-id="b632b-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="b632b-118">Можно пропустить определенное количество результатов в начале результата запроса с помощью `Skip` предложение.</span><span class="sxs-lookup"><span data-stu-id="b632b-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b632b-119">Пример</span><span class="sxs-lookup"><span data-stu-id="b632b-119">Example</span></span>  
 <span data-ttu-id="b632b-120">В следующем примере кода используется `Skip While` предложение для обхода результатов, пока не будет найдено первого заказчика из США.</span><span class="sxs-lookup"><span data-stu-id="b632b-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b632b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b632b-121">See also</span></span>

- <span data-ttu-id="b632b-122">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b632b-122">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="b632b-123">Запросы</span><span class="sxs-lookup"><span data-stu-id="b632b-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b632b-124">Предложение Select</span><span class="sxs-lookup"><span data-stu-id="b632b-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b632b-125">Предложение From</span><span class="sxs-lookup"><span data-stu-id="b632b-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b632b-126">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="b632b-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="b632b-127">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="b632b-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="b632b-128">Предложения Where</span><span class="sxs-lookup"><span data-stu-id="b632b-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
