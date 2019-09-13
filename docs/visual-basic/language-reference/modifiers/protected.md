---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929459"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="6c60f-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c60f-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="6c60f-103">Модификатор доступа к члену, указывающий, что один или несколько объявленных программных элементов доступны только в своем собственном классе или производном классе.</span><span class="sxs-lookup"><span data-stu-id="6c60f-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c60f-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="6c60f-104">Remarks</span></span>  
 <span data-ttu-id="6c60f-105">Иногда программный элемент, объявленный в классе, содержит конфиденциальные данные или ограниченный код и требуется ограничить доступ к элементу.</span><span class="sxs-lookup"><span data-stu-id="6c60f-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="6c60f-106">Однако если класс является наследуемым и предполагается иерархия производных классов, то эти производные классы могут быть необходимы для доступа к данным или коду в этих производных классах.</span><span class="sxs-lookup"><span data-stu-id="6c60f-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="6c60f-107">В этом случае необходимо, чтобы элемент был доступен как из базового класса, так и из всех производных классов.</span><span class="sxs-lookup"><span data-stu-id="6c60f-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="6c60f-108">Чтобы ограничить доступ к элементу таким образом, его можно объявить с помощью `Protected`.</span><span class="sxs-lookup"><span data-stu-id="6c60f-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="6c60f-109">Модификатор `Protected` доступа можно сочетать с двумя другими модификаторами:</span><span class="sxs-lookup"><span data-stu-id="6c60f-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="6c60f-110">Модификатор [Protected Friend](protected-friend.md) делает член класса доступным из этого класса, из производных классов и из той же сборки, в которой определен класс.</span><span class="sxs-lookup"><span data-stu-id="6c60f-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="6c60f-111">Модификатор [Private protected](private-protected.md) делает член класса доступным для производных типов, но только внутри его содержащей сборки.</span><span class="sxs-lookup"><span data-stu-id="6c60f-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="6c60f-112">Правила</span><span class="sxs-lookup"><span data-stu-id="6c60f-112">Rules</span></span>  
  
- <span data-ttu-id="6c60f-113">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="6c60f-113">**Declaration Context.**</span></span> <span data-ttu-id="6c60f-114">Можно использовать `Protected` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="6c60f-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="6c60f-115">Это означает, что контекст объявления для `Protected` элемента должен быть классом и не может быть исходным файлом, пространством имен, интерфейсом, модулем, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="6c60f-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="6c60f-116">Поведение</span><span class="sxs-lookup"><span data-stu-id="6c60f-116">Behavior</span></span>  
  
- <span data-ttu-id="6c60f-117">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="6c60f-117">**Access Level.**</span></span> <span data-ttu-id="6c60f-118">Весь код в классе может обращаться к его элементам.</span><span class="sxs-lookup"><span data-stu-id="6c60f-118">All code in a class can access its elements.</span></span> <span data-ttu-id="6c60f-119">Код в любом классе, производном от базового класса, может обращаться ко `Protected` всем элементам базового класса.</span><span class="sxs-lookup"><span data-stu-id="6c60f-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="6c60f-120">Это справедливо для всех поколений наследования.</span><span class="sxs-lookup"><span data-stu-id="6c60f-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="6c60f-121">Это означает, что класс может обращаться к `Protected` элементам базового класса базового класса и т. д.</span><span class="sxs-lookup"><span data-stu-id="6c60f-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="6c60f-122">Защищенный доступ не является надмножеством или подмножеством дружественного доступа.</span><span class="sxs-lookup"><span data-stu-id="6c60f-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="6c60f-123">**Модификаторы доступа.**</span><span class="sxs-lookup"><span data-stu-id="6c60f-123">**Access Modifiers.**</span></span> <span data-ttu-id="6c60f-124">Ключевые слова, определяющие уровень доступа, называются *модификаторами доступа*.</span><span class="sxs-lookup"><span data-stu-id="6c60f-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6c60f-125">Сравнение модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6c60f-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="6c60f-126">Модификатор `Protected` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="6c60f-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6c60f-127">Оператор Class</span><span class="sxs-lookup"><span data-stu-id="6c60f-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6c60f-128">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="6c60f-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6c60f-129">Оператор Declare</span><span class="sxs-lookup"><span data-stu-id="6c60f-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6c60f-130">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="6c60f-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6c60f-131">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="6c60f-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6c60f-132">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="6c60f-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6c60f-133">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="6c60f-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6c60f-134">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="6c60f-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6c60f-135">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="6c60f-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6c60f-136">Оператор Property</span><span class="sxs-lookup"><span data-stu-id="6c60f-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6c60f-137">Оператор Structure</span><span class="sxs-lookup"><span data-stu-id="6c60f-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6c60f-138">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="6c60f-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c60f-139">См. также</span><span class="sxs-lookup"><span data-stu-id="6c60f-139">See also</span></span>

- [<span data-ttu-id="6c60f-140">Public</span><span class="sxs-lookup"><span data-stu-id="6c60f-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="6c60f-141">Friend</span><span class="sxs-lookup"><span data-stu-id="6c60f-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="6c60f-142">Закрытые</span><span class="sxs-lookup"><span data-stu-id="6c60f-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="6c60f-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="6c60f-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="6c60f-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="6c60f-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="6c60f-145">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c60f-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="6c60f-146">Процедуры</span><span class="sxs-lookup"><span data-stu-id="6c60f-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6c60f-147">Структуры</span><span class="sxs-lookup"><span data-stu-id="6c60f-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6c60f-148">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="6c60f-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
