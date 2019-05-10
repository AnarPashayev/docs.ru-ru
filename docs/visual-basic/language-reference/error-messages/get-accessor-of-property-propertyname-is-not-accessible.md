---
title: Метод доступа Get свойства <propertyname> недоступен
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 92cc6d732b59617a6043bd71a9549649ff1ad356
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662048"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="6be49-102">Метод доступа свойства «get» "\<имя_свойства >" не доступен</span><span class="sxs-lookup"><span data-stu-id="6be49-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="6be49-103">Оператор пытается извлечь значение свойства, если он не имеет доступа к свойству `Get` процедуры.</span><span class="sxs-lookup"><span data-stu-id="6be49-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="6be49-104">Если [оператор Get](../../../visual-basic/language-reference/statements/get-statement.md) помечается более строгий доступ уровня, чем его [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), попытка прочитать значение свойства может завершиться ошибкой в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="6be49-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="6be49-105">`Get` Оператор помечен [частного](../../../visual-basic/language-reference/modifiers/private.md) и вызывающий код находится за пределами класса или структуры, в котором оно определено свойство.</span><span class="sxs-lookup"><span data-stu-id="6be49-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="6be49-106">`Get` Оператор помечен [Protected](../../../visual-basic/language-reference/modifiers/protected.md) и вызывающий код находится не в классе или структуре, в котором оно определено свойство, ни в производном классе.</span><span class="sxs-lookup"><span data-stu-id="6be49-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="6be49-107">`Get` Оператор помечен [Friend](../../../visual-basic/language-reference/modifiers/friend.md) и вызывающий код не находится в той же сборке, в котором оно определено свойство.</span><span class="sxs-lookup"><span data-stu-id="6be49-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="6be49-108">**Идентификатор ошибки:** BC31103</span><span class="sxs-lookup"><span data-stu-id="6be49-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6be49-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6be49-109">To correct this error</span></span>  
  
- <span data-ttu-id="6be49-110">Если у вас есть контроль исходного кода, определяющего свойство, рассмотрим следующее объявление `Get` процедуру с тот же уровень доступа, как и само свойство.</span><span class="sxs-lookup"><span data-stu-id="6be49-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="6be49-111">Если у вас нет контроля исходного кода, определяющего свойство или необходимо ограничить `Get` больше, чем у самого свойства, попробуйте переместить инструкцию, которая считывает значение свойства для области кода, имеющий более удобный доступ к процедуре уровень доступа свойство.</span><span class="sxs-lookup"><span data-stu-id="6be49-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be49-112">См. также</span><span class="sxs-lookup"><span data-stu-id="6be49-112">See also</span></span>

- [<span data-ttu-id="6be49-113">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="6be49-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="6be49-114">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="6be49-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
