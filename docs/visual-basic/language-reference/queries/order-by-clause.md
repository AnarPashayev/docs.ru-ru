---
title: Предложение Order By (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004951"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="2591a-102">Предложение Order By (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2591a-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="2591a-103">Задает порядок сортировки для результата запроса.</span><span class="sxs-lookup"><span data-stu-id="2591a-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2591a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2591a-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="2591a-105">Части</span><span class="sxs-lookup"><span data-stu-id="2591a-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="2591a-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2591a-106">Required.</span></span> <span data-ttu-id="2591a-107">Одно или несколько полей из текущего результата запроса, которые указывают порядок упорядочения возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="2591a-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="2591a-108">Имена полей должны быть разделены запятыми (,).</span><span class="sxs-lookup"><span data-stu-id="2591a-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="2591a-109">Каждое поле можно задать как отсортированное по возрастанию или убыванию с помощью ключевых слов `Ascending` или `Descending`.</span><span class="sxs-lookup"><span data-stu-id="2591a-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="2591a-110">Если не указано ключевое слово `Ascending` или `Descending`, порядок сортировки по умолчанию — по возрастанию.</span><span class="sxs-lookup"><span data-stu-id="2591a-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="2591a-111">Поля порядка сортировки получают приоритет слева направо.</span><span class="sxs-lookup"><span data-stu-id="2591a-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2591a-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="2591a-112">Remarks</span></span>  
 <span data-ttu-id="2591a-113">Для сортировки результатов запроса можно использовать предложение `Order By`.</span><span class="sxs-lookup"><span data-stu-id="2591a-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="2591a-114">Предложение `Order By` может отсортировать результат только на основе переменной диапазона для текущей области.</span><span class="sxs-lookup"><span data-stu-id="2591a-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="2591a-115">Например, предложение `Select` вводит новую область в выражении запроса с новыми переменными итерации для этой области.</span><span class="sxs-lookup"><span data-stu-id="2591a-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="2591a-116">Переменные диапазона, определенные до предложения `Select` в запросе, недоступны после предложения `Select`.</span><span class="sxs-lookup"><span data-stu-id="2591a-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="2591a-117">Поэтому, если требуется упорядочить результаты по полю, которое недоступно в предложении `Select`, необходимо поместить предложение `Order By` перед предложением `Select`.</span><span class="sxs-lookup"><span data-stu-id="2591a-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="2591a-118">Одним из примеров того, когда это потребуется, является то, что нужно отсортировать запрос по полям, которые не возвращаются как часть результата.</span><span class="sxs-lookup"><span data-stu-id="2591a-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="2591a-119">Порядок сортировки для поля по возрастанию и убыванию определяется реализацией интерфейса <xref:System.IComparable> для типа данных поля.</span><span class="sxs-lookup"><span data-stu-id="2591a-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="2591a-120">Если тип данных не реализует интерфейс <xref:System.IComparable>, порядок сортировки игнорируется.</span><span class="sxs-lookup"><span data-stu-id="2591a-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2591a-121">Пример</span><span class="sxs-lookup"><span data-stu-id="2591a-121">Example</span></span>  
 <span data-ttu-id="2591a-122">Следующее выражение запроса использует предложение `From` для объявления переменной диапазона `book` для коллекции `books`.</span><span class="sxs-lookup"><span data-stu-id="2591a-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="2591a-123">Предложение `Order By` сортирует результат запроса по цене в возрастающем порядке (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2591a-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="2591a-124">Книги с одинаковой ценой сортируются по названию в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="2591a-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="2591a-125">Предложение `Select` выбирает свойства `Title` и `Price` в качестве значений, возвращаемых запросом.</span><span class="sxs-lookup"><span data-stu-id="2591a-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="2591a-126">Пример</span><span class="sxs-lookup"><span data-stu-id="2591a-126">Example</span></span>  
 <span data-ttu-id="2591a-127">Следующее выражение запроса использует предложение `Order By` для сортировки результатов запроса по цене в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="2591a-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="2591a-128">Книги с одинаковой ценой сортируются по названию в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="2591a-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="2591a-129">Пример</span><span class="sxs-lookup"><span data-stu-id="2591a-129">Example</span></span>  
 <span data-ttu-id="2591a-130">Следующее выражение запроса использует предложение `Select` для выбора названия книги, цены, даты публикации и автора.</span><span class="sxs-lookup"><span data-stu-id="2591a-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="2591a-131">Затем он заполняет поля `Title`, `Price`, `PublishDate` и `Author` переменной диапазона для новой области.</span><span class="sxs-lookup"><span data-stu-id="2591a-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="2591a-132">Предложение `Order By` упорядочивает новую переменную диапазона по имени автора, названию книги и стоимости.</span><span class="sxs-lookup"><span data-stu-id="2591a-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="2591a-133">Каждый столбец сортируется в порядке по умолчанию (по возрастанию).</span><span class="sxs-lookup"><span data-stu-id="2591a-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="2591a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="2591a-134">See also</span></span>

- <span data-ttu-id="2591a-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2591a-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="2591a-136">Запросы</span><span class="sxs-lookup"><span data-stu-id="2591a-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="2591a-137">Предложение Select</span><span class="sxs-lookup"><span data-stu-id="2591a-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="2591a-138">Предложение From</span><span class="sxs-lookup"><span data-stu-id="2591a-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
