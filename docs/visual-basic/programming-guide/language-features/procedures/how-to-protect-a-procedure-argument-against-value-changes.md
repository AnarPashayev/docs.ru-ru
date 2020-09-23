---
title: Практическое руководство. Защита аргумента процедуры от изменений значения
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 84eadf3d364b69120221d80e464b1175b1602e13
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071486"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="da437-102">Практическое руководство. Защита аргумента процедуры от изменения значения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da437-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>

<span data-ttu-id="da437-103">Если процедура объявляет параметр как [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic предоставляет коду процедуры прямую ссылку на программный элемент, лежащий в основе аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="da437-103">If a procedure declares a parameter as [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="da437-104">Это позволяет процедуре изменять значение, которое является базовым для аргумента в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="da437-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="da437-105">В некоторых случаях вызывающему коду может потребоваться защититься от такого изменения.</span><span class="sxs-lookup"><span data-stu-id="da437-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="da437-106">Вы всегда можете защитить аргумент от изменения, объявив соответствующий параметр [ByVal](../../../language-reference/modifiers/byval.md) в процедуре.</span><span class="sxs-lookup"><span data-stu-id="da437-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="da437-107">Если вы хотите иметь возможность изменять заданный аргумент в некоторых случаях, но не в других, можно объявить его `ByRef` и позволить вызывающему коду определить механизм передачи в каждом вызове.</span><span class="sxs-lookup"><span data-stu-id="da437-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="da437-108">Это достигается путем заключения соответствующего аргумента в круглые скобки для передачи его по значению или его заключения в круглые скобки для передачи его по ссылке.</span><span class="sxs-lookup"><span data-stu-id="da437-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="da437-109">Дополнительные сведения см. [в разделе инструкции. Принудительная передача аргумента по значению](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="da437-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da437-110">Пример</span><span class="sxs-lookup"><span data-stu-id="da437-110">Example</span></span>  

 <span data-ttu-id="da437-111">В следующем примере показаны две процедуры, которые принимают переменную массива и работают с ее элементами.</span><span class="sxs-lookup"><span data-stu-id="da437-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="da437-112">`increase`Процедура просто добавляет по одной к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="da437-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="da437-113">`replace`Процедура присваивает параметру новый массив `a()` , а затем добавляет его к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="da437-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="da437-114">Однако переназначение не влияет на базовую переменную массива в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="da437-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="da437-115">Первый `MsgBox` вызов выводит "после увеличения (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="da437-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="da437-116">Поскольку массив `n` является ссылочным типом, `increase` может изменить его члены, даже если используется механизм передачи `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="da437-116">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="da437-117">Второй `MsgBox` вызов отображает "After Replace (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="da437-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="da437-118">Поскольку `n` передается `ByVal` , `replace` не может изменить переменную `n` в вызывающем коде, назначив ей новый массив.</span><span class="sxs-lookup"><span data-stu-id="da437-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="da437-119">Когда `replace` создает новый экземпляр массива `k` и присваивает его локальной переменной `a` , он теряет ссылку, `n` переданную в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="da437-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="da437-120">При изменении членов изменяется `a` только локальный массив `k` .</span><span class="sxs-lookup"><span data-stu-id="da437-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="da437-121">Таким образом, не `replace` увеличивает значения массива `n` в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="da437-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="da437-122">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="da437-122">Compile the code</span></span>  

 <span data-ttu-id="da437-123">По умолчанию в Visual Basic передаются аргументы по значению.</span><span class="sxs-lookup"><span data-stu-id="da437-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="da437-124">Однако рекомендуется включать ключевое слово [ByVal](../../../language-reference/modifiers/byval.md) или [ByRef](../../../language-reference/modifiers/byref.md) с каждым объявленным параметром.</span><span class="sxs-lookup"><span data-stu-id="da437-124">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="da437-125">Это упрощает чтение кода.</span><span class="sxs-lookup"><span data-stu-id="da437-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da437-126">См. также</span><span class="sxs-lookup"><span data-stu-id="da437-126">See also</span></span>

- [<span data-ttu-id="da437-127">Процедуры</span><span class="sxs-lookup"><span data-stu-id="da437-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="da437-128">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="da437-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="da437-129">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="da437-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="da437-130">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="da437-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="da437-131">Различия между изменяемыми и неизменяемыми аргументами</span><span class="sxs-lookup"><span data-stu-id="da437-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="da437-132">Различия между передачей аргумента по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="da437-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="da437-133">Практическое руководство. Изменение значения аргумента процедуры</span><span class="sxs-lookup"><span data-stu-id="da437-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="da437-134">Практическое руководство. Принудительная передача аргумента по значению</span><span class="sxs-lookup"><span data-stu-id="da437-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="da437-135">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="da437-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="da437-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="da437-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
