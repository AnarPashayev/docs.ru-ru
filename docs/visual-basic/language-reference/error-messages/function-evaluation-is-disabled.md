---
title: Вычисление функции отключено, поскольку истекло время, выделенное на вычисление предыдущей функции
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: bc4d05e52434cf62fa90671d29b407c83114b5d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315781"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="166d4-102">Вычисление функции отключено, поскольку истекло время, выделенное на вычисление предыдущей функции</span><span class="sxs-lookup"><span data-stu-id="166d4-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="166d4-103">Вычисление функции отключено, так как истекло время ожидания вычисление предыдущей функции. Чтобы снова включить вычисление функции, еще один шаг или перезапустите отладку.</span><span class="sxs-lookup"><span data-stu-id="166d4-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="166d4-104">В отладчике Visual Studio выражение задает вызов процедуры, но другое вычисление обнаружил превышение времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="166d4-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="166d4-105">Среди возможных причин вызов процедуры истечения времени ожидания бесконечного цикла или *бесконечный цикл*.</span><span class="sxs-lookup"><span data-stu-id="166d4-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="166d4-106">Дополнительные сведения см. в разделе [для... Следующий оператор](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="166d4-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="166d4-107">Является особым случаем бесконечного цикла *рекурсии*.</span><span class="sxs-lookup"><span data-stu-id="166d4-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="166d4-108">Дополнительные сведения см. в разделе [рекурсивные процедуры](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="166d4-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="166d4-109">**Идентификатор ошибки:** BC30957</span><span class="sxs-lookup"><span data-stu-id="166d4-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="166d4-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="166d4-110">To correct this error</span></span>  
  
1. <span data-ttu-id="166d4-111">По возможности определите, какой параметр имел вычисление предыдущей функции и что вызвало его истечения времени ожидания. В противном случае эта ошибка может возникнуть еще раз.</span><span class="sxs-lookup"><span data-stu-id="166d4-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="166d4-112">Опять же, завести отладчик или завершите и перезапустите отладку.</span><span class="sxs-lookup"><span data-stu-id="166d4-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166d4-113">См. также</span><span class="sxs-lookup"><span data-stu-id="166d4-113">See also</span></span>

- [<span data-ttu-id="166d4-114">Отладка в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="166d4-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="166d4-115">Навигация по коду с помощью отладчика</span><span class="sxs-lookup"><span data-stu-id="166d4-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
