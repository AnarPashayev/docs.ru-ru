---
title: События общих переменных WithEvents не могут обрабатываться не используемыми совместно методами
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: d6067c75835ecd14f1dd796c20ae3f29f456e541
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642945"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="9fca9-102">События общих переменных WithEvents не могут обрабатываться не используемыми совместно методами</span><span class="sxs-lookup"><span data-stu-id="9fca9-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="9fca9-103">Переменная, объявленная с `Shared` модификатор является общей переменной.</span><span class="sxs-lookup"><span data-stu-id="9fca9-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="9fca9-104">Общей переменной определяет строго одно место хранения.</span><span class="sxs-lookup"><span data-stu-id="9fca9-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="9fca9-105">Переменная, объявленная с `WithEvents` модификатором обработки набора событий, вызываемых переменной типа, к которому относится переменная.</span><span class="sxs-lookup"><span data-stu-id="9fca9-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="9fca9-106">Когда значение присваивается переменной, свойства, созданные `WithEvents` объявление отсоединяется от любого существующего обработчика событий и подключает обработчик событий с помощью `Add` метод.</span><span class="sxs-lookup"><span data-stu-id="9fca9-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="9fca9-107">**Идентификатор ошибки:** BC30594</span><span class="sxs-lookup"><span data-stu-id="9fca9-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9fca9-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9fca9-108">To correct this error</span></span>  
  
- <span data-ttu-id="9fca9-109">Объявите обработчик событий `Shared`.</span><span class="sxs-lookup"><span data-stu-id="9fca9-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fca9-110">См. также</span><span class="sxs-lookup"><span data-stu-id="9fca9-110">See also</span></span>

- [<span data-ttu-id="9fca9-111">Общие</span><span class="sxs-lookup"><span data-stu-id="9fca9-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="9fca9-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="9fca9-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
