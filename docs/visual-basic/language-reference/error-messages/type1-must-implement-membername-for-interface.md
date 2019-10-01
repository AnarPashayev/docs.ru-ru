---
title: <type1>'<typename>«должен реализовывать»<membername>«для интерфейса»<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696895"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="d7fc8-102">\<type1 > "\<typename >" должен реализовывать "\<membername >" для интерфейса "\<interfacename >"</span><span class="sxs-lookup"><span data-stu-id="d7fc8-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="d7fc8-103">"\<typename >" должен реализовывать "\<membername >" для интерфейса "\<interfacename >".</span><span class="sxs-lookup"><span data-stu-id="d7fc8-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="d7fc8-104">Реализация свойства должна иметь соответствующие описатели "ReadOnly"/"WriteOnly".</span><span class="sxs-lookup"><span data-stu-id="d7fc8-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="d7fc8-105">Класс или структура объявляет о необходимости реализации интерфейса, но не реализует процедуру, свойство или событие, определенные интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="d7fc8-106">Каждый член интерфейса должен быть реализован.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="d7fc8-107">**Идентификатор ошибки:** BC30154</span><span class="sxs-lookup"><span data-stu-id="d7fc8-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7fc8-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d7fc8-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d7fc8-109">Объявите член с таким же именем и сигнатурой, как определено в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="d7fc8-110">Не забудьте включить как минимум инструкцию `End Function`, `End Sub` или `End Property`.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="d7fc8-111">Добавьте предложение `Implements` в конец оператора `Function`, `Sub`, `Property` или `Event`.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="d7fc8-112">Пример:</span><span class="sxs-lookup"><span data-stu-id="d7fc8-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="d7fc8-113">При реализации свойства убедитесь, что `ReadOnly` или `WriteOnly` используется так же, как и в определении интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="d7fc8-114">При реализации свойства объявите процедуры `Get` и `Set` соответственно.</span><span class="sxs-lookup"><span data-stu-id="d7fc8-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fc8-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d7fc8-115">See also</span></span>

- [<span data-ttu-id="d7fc8-116">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="d7fc8-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="d7fc8-117">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="d7fc8-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
