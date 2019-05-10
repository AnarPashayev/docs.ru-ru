---
title: Структура <structurename> должна содержать по крайней мере один экземпляр переменной члена или экземпляр объявления события, не помеченный как Custom
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4ce24073896326bb5a68e563e2d34aafa09ef1c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593206"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="7e019-102">Структура "\<имя_структуры >" должен содержать по крайней мере один экземпляр переменной члена или объявление по крайней мере один экземпляр события, не помечен как «Custom»</span><span class="sxs-lookup"><span data-stu-id="7e019-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="7e019-103">Определение структуры не включает все совместно переменные или обычные события.</span><span class="sxs-lookup"><span data-stu-id="7e019-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="7e019-104">Каждая структура должна иметь переменную либо событие, которое применяется к каждому определенному экземпляру (не общие), а не ко всем экземплярам совокупности ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="7e019-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="7e019-105">Неиспользуемые совместно константы, свойства и процедуры не удовлетворяют этим требованиям.</span><span class="sxs-lookup"><span data-stu-id="7e019-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="7e019-106">Кроме того, если нет неиспользуемых совместно переменных и только одно событие, не являющиеся общими, что событие не может быть `Custom` событий.</span><span class="sxs-lookup"><span data-stu-id="7e019-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="7e019-107">**Идентификатор ошибки:** BC30941</span><span class="sxs-lookup"><span data-stu-id="7e019-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e019-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="7e019-108">To correct this error</span></span>  
  
- <span data-ttu-id="7e019-109">Определите по крайней мере одну переменную или событие, которое не является `Shared`.</span><span class="sxs-lookup"><span data-stu-id="7e019-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="7e019-110">Если вы определяете только одно событие, он должен быть являющуюся, а также не совместно.</span><span class="sxs-lookup"><span data-stu-id="7e019-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e019-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7e019-111">See also</span></span>

- [<span data-ttu-id="7e019-112">Структуры</span><span class="sxs-lookup"><span data-stu-id="7e019-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7e019-113">Практическое руководство. Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="7e019-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="7e019-114">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="7e019-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
