---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 1a486d0fadce8135fe01d9eecd611081c986bfae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647690"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="0c12e-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c12e-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="0c12e-103">Указывает, что переменная или свойство можно читать, но не записываются.</span><span class="sxs-lookup"><span data-stu-id="0c12e-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c12e-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="0c12e-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0c12e-105">Правила</span><span class="sxs-lookup"><span data-stu-id="0c12e-105">Rules</span></span>  
  
- <span data-ttu-id="0c12e-106">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="0c12e-106">**Declaration Context.**</span></span> <span data-ttu-id="0c12e-107">`ReadOnly` можно использовать только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="0c12e-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="0c12e-108">Это означает, что контекст объявления для `ReadOnly` элемент должен быть класс, структура или модуль и не может быть исходный файл, пространство имен или процедуры.</span><span class="sxs-lookup"><span data-stu-id="0c12e-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="0c12e-109">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="0c12e-109">**Combined Modifiers.**</span></span> <span data-ttu-id="0c12e-110">Нельзя указать `ReadOnly` вместе с `Static` в одном объявлении.</span><span class="sxs-lookup"><span data-stu-id="0c12e-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="0c12e-111">**Присвоение значения.**</span><span class="sxs-lookup"><span data-stu-id="0c12e-111">**Assigning a Value.**</span></span> <span data-ttu-id="0c12e-112">Использование кода `ReadOnly` свойство невозможно задать его значение.</span><span class="sxs-lookup"><span data-stu-id="0c12e-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="0c12e-113">Но код, который имеет доступ в базовом хранилище можно назначить или изменить значение в любое время.</span><span class="sxs-lookup"><span data-stu-id="0c12e-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="0c12e-114">Можно присвоить значение `ReadOnly` переменной только при объявлении или в конструкторе класса или структуры, в котором он определен.</span><span class="sxs-lookup"><span data-stu-id="0c12e-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="0c12e-115">Когда следует использовать переменную только для чтения</span><span class="sxs-lookup"><span data-stu-id="0c12e-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="0c12e-116">Существуют ситуации, в которых нельзя использовать [оператор Const](../../../visual-basic/language-reference/statements/const-statement.md) объявить переменную и присвоить значение константы.</span><span class="sxs-lookup"><span data-stu-id="0c12e-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="0c12e-117">Например `Const` инструкция может не поддерживать тип данных, который вы хотите назначить, или вы не может для вычисления значения во время компиляции с константным выражением.</span><span class="sxs-lookup"><span data-stu-id="0c12e-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="0c12e-118">Вам могут даже не знать значение во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="0c12e-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="0c12e-119">В таких случаях можно использовать `ReadOnly` переменной для хранения значение константы.</span><span class="sxs-lookup"><span data-stu-id="0c12e-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c12e-120">Если тип данных переменной является ссылочным типом, например, массив или экземпляр класса, можно изменить его члены, даже если сама переменная `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="0c12e-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="0c12e-121">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0c12e-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="0c12e-122">При инициализации массива, на которые указывают `characterArray()` содержит «x», «y» и «z».</span><span class="sxs-lookup"><span data-stu-id="0c12e-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="0c12e-123">Так как переменная `characterArray` — `ReadOnly`, его значение нельзя изменить после инициализации; это, нельзя назначить новый массив.</span><span class="sxs-lookup"><span data-stu-id="0c12e-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="0c12e-124">Тем не менее можно изменить значения одного или нескольких элементов массива.</span><span class="sxs-lookup"><span data-stu-id="0c12e-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="0c12e-125">После вызова процедуры `changeArrayElement`, массив, на которые указывают `characterArray()` содержит «x», «M» и «z».</span><span class="sxs-lookup"><span data-stu-id="0c12e-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="0c12e-126">Обратите внимание, что это похоже на объявление параметра процедуры [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), который запрещает изменять аргумент вызова процедуры, но позволяет менять ее членов.</span><span class="sxs-lookup"><span data-stu-id="0c12e-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c12e-127">Пример</span><span class="sxs-lookup"><span data-stu-id="0c12e-127">Example</span></span>  
 <span data-ttu-id="0c12e-128">В следующем примере определяется `ReadOnly` свойство для даты, на котором сотрудник был принят на работу.</span><span class="sxs-lookup"><span data-stu-id="0c12e-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="0c12e-129">Класс хранит значение свойства как внутренне `Private` переменной, а только код внутри класса, это значение можно изменить.</span><span class="sxs-lookup"><span data-stu-id="0c12e-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="0c12e-130">Тем не менее, свойство является `Public`, и любой код, который можно получить доступ к классу можно считать свойство.</span><span class="sxs-lookup"><span data-stu-id="0c12e-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="0c12e-131">Модификатор `ReadOnly` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="0c12e-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0c12e-132">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="0c12e-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="0c12e-133">Оператор Property</span><span class="sxs-lookup"><span data-stu-id="0c12e-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c12e-134">См. также</span><span class="sxs-lookup"><span data-stu-id="0c12e-134">See also</span></span>

- [<span data-ttu-id="0c12e-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="0c12e-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="0c12e-136">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="0c12e-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
