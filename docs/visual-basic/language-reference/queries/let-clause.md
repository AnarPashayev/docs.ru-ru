---
title: Предложение Let (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004729"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="94ebb-102">Предложение Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94ebb-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="94ebb-103">Выполняет вычисление значения и присваивает его новой переменной в запросе.</span><span class="sxs-lookup"><span data-stu-id="94ebb-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ebb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94ebb-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="94ebb-105">Части</span><span class="sxs-lookup"><span data-stu-id="94ebb-105">Parts</span></span>  
  
|<span data-ttu-id="94ebb-106">Термин</span><span class="sxs-lookup"><span data-stu-id="94ebb-106">Term</span></span>|<span data-ttu-id="94ebb-107">Определение</span><span class="sxs-lookup"><span data-stu-id="94ebb-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="94ebb-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="94ebb-108">Required.</span></span> <span data-ttu-id="94ebb-109">Псевдоним, который может использоваться для ссылки на результаты предоставляемого выражения.</span><span class="sxs-lookup"><span data-stu-id="94ebb-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="94ebb-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="94ebb-110">Required.</span></span> <span data-ttu-id="94ebb-111">Выражение, которое будет вычислено и назначено указанной переменной.</span><span class="sxs-lookup"><span data-stu-id="94ebb-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94ebb-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="94ebb-112">Remarks</span></span>  
 <span data-ttu-id="94ebb-113">Предложение `Let` позволяет вычислять значения для каждого результата запроса и ссылаться на них с помощью псевдонима.</span><span class="sxs-lookup"><span data-stu-id="94ebb-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="94ebb-114">Псевдоним можно использовать в других предложениях, например в предложении `Where`.</span><span class="sxs-lookup"><span data-stu-id="94ebb-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="94ebb-115">Предложение `Let` позволяет создать инструкцию запроса, которая будет проще читать, поскольку можно указать псевдоним для предложения выражения, включенного в запрос, и заменить псевдоним при каждом использовании предложения Expression.</span><span class="sxs-lookup"><span data-stu-id="94ebb-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="94ebb-116">В предложение @no__t 2 можно включить любое количество назначений `variable` и `expression`.</span><span class="sxs-lookup"><span data-stu-id="94ebb-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="94ebb-117">Разделяйте каждое назначение запятой (,).</span><span class="sxs-lookup"><span data-stu-id="94ebb-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94ebb-118">Пример</span><span class="sxs-lookup"><span data-stu-id="94ebb-118">Example</span></span>  
 <span data-ttu-id="94ebb-119">В следующем примере кода используется предложение `Let` для расчета скидки на 10% для продуктов.</span><span class="sxs-lookup"><span data-stu-id="94ebb-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="94ebb-120">См. также</span><span class="sxs-lookup"><span data-stu-id="94ebb-120">See also</span></span>

- <span data-ttu-id="94ebb-121">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94ebb-121">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="94ebb-122">Запросы</span><span class="sxs-lookup"><span data-stu-id="94ebb-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="94ebb-123">Предложение Select</span><span class="sxs-lookup"><span data-stu-id="94ebb-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="94ebb-124">Предложение From</span><span class="sxs-lookup"><span data-stu-id="94ebb-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="94ebb-125">Предложения Where</span><span class="sxs-lookup"><span data-stu-id="94ebb-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
