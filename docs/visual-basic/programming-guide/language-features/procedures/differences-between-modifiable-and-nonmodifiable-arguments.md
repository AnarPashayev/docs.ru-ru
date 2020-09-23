---
title: Различия между изменяемыми и неизменяемыми аргументами
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 662ad3039bb3fd5c44847d5b2a97a033a18ad063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071966"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="6685e-102">Различия между аргументами Modifiable и Nonmodifiable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6685e-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>

<span data-ttu-id="6685e-103">При вызове процедуры в нее обычно передается один или несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="6685e-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="6685e-104">Каждый аргумент соответствует базовому программному элементу.</span><span class="sxs-lookup"><span data-stu-id="6685e-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="6685e-105">Как базовые элементы, так и сами аргументы могут быть либо изменяемыми, либо неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="6685e-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="6685e-106">Изменяемые и неизменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="6685e-106">Modifiable and Nonmodifiable Elements</span></span>  

 <span data-ttu-id="6685e-107">Программным элементом может быть *изменяемый элемент*, для которого может быть изменено значение, или *неизменяемый элемент*, имеющий фиксированное значение после создания.</span><span class="sxs-lookup"><span data-stu-id="6685e-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="6685e-108">В следующей таблице перечислены изменяемые и неизменяемые элементы программирования.</span><span class="sxs-lookup"><span data-stu-id="6685e-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="6685e-109">Изменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="6685e-109">Modifiable elements</span></span>|<span data-ttu-id="6685e-110">Неизменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="6685e-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="6685e-111">Локальные переменные (объявленные в процедурах), включая переменные объекта, за исключением только для чтения</span><span class="sxs-lookup"><span data-stu-id="6685e-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="6685e-112">Переменные, поля и свойства только для чтения</span><span class="sxs-lookup"><span data-stu-id="6685e-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="6685e-113">Поля (переменные-члены модулей, классов и структур), кроме только для чтения</span><span class="sxs-lookup"><span data-stu-id="6685e-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="6685e-114">Константы и литералы</span><span class="sxs-lookup"><span data-stu-id="6685e-114">Constants and literals</span></span>|  
|<span data-ttu-id="6685e-115">Свойства, кроме "только для чтения"</span><span class="sxs-lookup"><span data-stu-id="6685e-115">Properties, except for read-only</span></span>|<span data-ttu-id="6685e-116">Члены перечисления</span><span class="sxs-lookup"><span data-stu-id="6685e-116">Enumeration members</span></span>|  
|<span data-ttu-id="6685e-117">Элементы массива</span><span class="sxs-lookup"><span data-stu-id="6685e-117">Array elements</span></span>|<span data-ttu-id="6685e-118">Выражения (даже если их элементы являются изменяемыми)</span><span class="sxs-lookup"><span data-stu-id="6685e-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="6685e-119">Изменяемые и неизменяемые аргументы</span><span class="sxs-lookup"><span data-stu-id="6685e-119">Modifiable and Nonmodifiable Arguments</span></span>  

 <span data-ttu-id="6685e-120">*Изменяемый аргумент* — это один из изменяемых базовых элементов.</span><span class="sxs-lookup"><span data-stu-id="6685e-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="6685e-121">Вызывающий код может сохранить новое значение в любое время, и при передаче аргумента [ByRef](../../../language-reference/modifiers/byref.md)код в процедуре также может изменить базовый элемент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="6685e-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="6685e-122">*Неизменяемый аргумент* либо имеет неизменяемый базовый элемент, либо передается [ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="6685e-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="6685e-123">Процедура не может изменить базовый элемент в вызывающем коде, даже если это изменяемый элемент.</span><span class="sxs-lookup"><span data-stu-id="6685e-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="6685e-124">Если это неизменяемый элемент, то сам вызывающий код не может изменить его.</span><span class="sxs-lookup"><span data-stu-id="6685e-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="6685e-125">Вызванная процедура может изменить свою локальную копию неизменяемого аргумента, но это изменение не влияет на базовый элемент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="6685e-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6685e-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6685e-126">See also</span></span>

- [<span data-ttu-id="6685e-127">Процедуры</span><span class="sxs-lookup"><span data-stu-id="6685e-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6685e-128">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="6685e-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6685e-129">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="6685e-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="6685e-130">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="6685e-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="6685e-131">Различия между передачей аргумента по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="6685e-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="6685e-132">Практическое руководство. Изменение значения аргумента процедуры</span><span class="sxs-lookup"><span data-stu-id="6685e-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="6685e-133">Практическое руководство. Защита аргумента процедуры от изменений значения</span><span class="sxs-lookup"><span data-stu-id="6685e-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="6685e-134">Практическое руководство. Принудительная передача аргумента по значению</span><span class="sxs-lookup"><span data-stu-id="6685e-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="6685e-135">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="6685e-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="6685e-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6685e-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
