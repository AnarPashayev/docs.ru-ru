---
title: Отсутствует место в стеке (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318797"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="ff144-102">Отсутствует место в стеке (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff144-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="ff144-103">Стек — это рабочая область памяти, который увеличивается и уменьшается динамически с помощью требований выполняемой программы.</span><span class="sxs-lookup"><span data-stu-id="ff144-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="ff144-104">Предел был превышен.</span><span class="sxs-lookup"><span data-stu-id="ff144-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ff144-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ff144-105">To correct this error</span></span>  
  
1. <span data-ttu-id="ff144-106">Проверьте, что процедуры не вложены слишком глубоко.</span><span class="sxs-lookup"><span data-stu-id="ff144-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="ff144-107">Убедитесь, что рекурсивные процедуры завершаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="ff144-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="ff144-108">Если локальных переменных недостаточно места, чем доступно, объявите некоторые переменные на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="ff144-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="ff144-109">Можно также объявить все переменные в процедуре статический перед `Property`, `Sub`, или `Function` ключевого слова with `Static`.</span><span class="sxs-lookup"><span data-stu-id="ff144-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="ff144-110">Или можно использовать `Static` инструкцию для объявления в процедурах отдельных статических переменных.</span><span class="sxs-lookup"><span data-stu-id="ff144-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="ff144-111">Переопределите некоторые из строк фиксированной длины как строки переменной длины, как строки фиксированной длины используйте больше пространства стека, чем строки переменной длины.</span><span class="sxs-lookup"><span data-stu-id="ff144-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="ff144-112">Можно также определить строку на уровне модуля, где требуются не пространство стека.</span><span class="sxs-lookup"><span data-stu-id="ff144-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="ff144-113">Проверьте количество вложенных `DoEvents` вызовы функций, с помощью `Calls` диалоговое окно, чтобы узнать, какие процедуры активны в стеке.</span><span class="sxs-lookup"><span data-stu-id="ff144-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="ff144-114">Убедитесь, что вы не приводит к «Каскад событий» путем активации события, вызывающего процедуру обработки события уже в стеке.</span><span class="sxs-lookup"><span data-stu-id="ff144-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="ff144-115">Каскад событий аналогичен без признака завершения рекурсивный вызов процедуры, но это менее очевидных, так как вызов выполняется по Visual Basic, а не явным вызовом в коде.</span><span class="sxs-lookup"><span data-stu-id="ff144-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="ff144-116">Используйте `Calls` диалоговое окно, чтобы узнать, какие процедуры активны в стеке.</span><span class="sxs-lookup"><span data-stu-id="ff144-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff144-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ff144-117">See also</span></span>

- [<span data-ttu-id="ff144-118">Окно памяти</span><span class="sxs-lookup"><span data-stu-id="ff144-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
