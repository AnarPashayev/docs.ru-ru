---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 5e534eac2300327d4c54c5ce93d8b2c6c538e794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801670"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="57d33-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57d33-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="57d33-103">Указывает, что аргумент передается таким образом, что вызванная процедура или свойство не может изменить значение переменной в аргументе в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="57d33-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57d33-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="57d33-104">Remarks</span></span>  
 <span data-ttu-id="57d33-105">Модификатор `ByVal` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="57d33-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="57d33-106">Оператор Declare</span><span class="sxs-lookup"><span data-stu-id="57d33-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="57d33-107">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="57d33-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="57d33-108">Оператор Statement</span><span class="sxs-lookup"><span data-stu-id="57d33-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="57d33-109">Оператор Property</span><span class="sxs-lookup"><span data-stu-id="57d33-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="57d33-110">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="57d33-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="57d33-111">Пример</span><span class="sxs-lookup"><span data-stu-id="57d33-111">Example</span></span>  
 <span data-ttu-id="57d33-112">В следующем примере показано использование `ByVal` механизм с ссылочным аргументом типа передачи параметров.</span><span class="sxs-lookup"><span data-stu-id="57d33-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="57d33-113">В примере аргумент является `c1`, экземпляр класса `Class1`.</span><span class="sxs-lookup"><span data-stu-id="57d33-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="57d33-114">`ByVal` запрещает изменять основное значение ссылочного аргумента кода в процедурах `c1`, но не защищает доступные поля и свойства `c1`.</span><span class="sxs-lookup"><span data-stu-id="57d33-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="57d33-115">См. также</span><span class="sxs-lookup"><span data-stu-id="57d33-115">See also</span></span>

- [<span data-ttu-id="57d33-116">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="57d33-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="57d33-117">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="57d33-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
