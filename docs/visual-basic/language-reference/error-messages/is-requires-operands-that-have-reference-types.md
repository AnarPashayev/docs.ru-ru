---
title: При использовании оператора сравнения Is требуются операнды со ссылочным типом, однако данный операнд имеет тип значения <typename>
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: b828de196a12128a9f34ee1f9ff1e57fee22c687
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843855"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="a745a-102">«Is» требуются операнды ссылочных типов, а этот операнд имеет тип значения "\<typename >"</span><span class="sxs-lookup"><span data-stu-id="a745a-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="a745a-103">`Is` Оператор сравнения определяет, ссылаются ли две объектные переменные на один экземпляр.</span><span class="sxs-lookup"><span data-stu-id="a745a-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="a745a-104">Это сравнение не определен для типов значений.</span><span class="sxs-lookup"><span data-stu-id="a745a-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="a745a-105">**Идентификатор ошибки:** BC30020</span><span class="sxs-lookup"><span data-stu-id="a745a-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a745a-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a745a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a745a-107">Используйте соответствующий арифметический оператор сравнения или `Like` оператор для сравнения двух типов значений.</span><span class="sxs-lookup"><span data-stu-id="a745a-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a745a-108">См. также</span><span class="sxs-lookup"><span data-stu-id="a745a-108">See also</span></span>

- [<span data-ttu-id="a745a-109">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="a745a-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="a745a-110">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="a745a-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="a745a-111">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="a745a-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
