---
title: Константы, определенные пользователем
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 351bdb6963e278341c13e53ef19aea0876010aa9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095646"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="84a72-102">Константы, определенные пользователем (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84a72-102">User-Defined Constants (Visual Basic)</span></span>

<span data-ttu-id="84a72-103">Константа — это понятное имя, которое принимает позицию числа или строки, которые не меняются.</span><span class="sxs-lookup"><span data-stu-id="84a72-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="84a72-104">Как можно понять из их названия, константы хранят значения, которые остаются постоянными в ходе выполнения приложения.</span><span class="sxs-lookup"><span data-stu-id="84a72-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="84a72-105">Вы можете использовать константы, определенные элементами управления или компонентами, с которыми вы работаете, или создать собственный.</span><span class="sxs-lookup"><span data-stu-id="84a72-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="84a72-106">Константы, созданные самостоятельно, описаны как *определяемые пользователем*.</span><span class="sxs-lookup"><span data-stu-id="84a72-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="84a72-107">Вы объявляете константу с `Const` инструкцией, используя те же рекомендации, что и при создании имени переменной.</span><span class="sxs-lookup"><span data-stu-id="84a72-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="84a72-108">Если `Option Strict` имеет значение `On` , необходимо явно объявить константный тип.</span><span class="sxs-lookup"><span data-stu-id="84a72-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="84a72-109">Использование инструкции const</span><span class="sxs-lookup"><span data-stu-id="84a72-109">Const Statement Usage</span></span>  

 <span data-ttu-id="84a72-110">`Const`Оператор может представлять математическое или значение даты и времени:</span><span class="sxs-lookup"><span data-stu-id="84a72-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="84a72-111">Он также может определять `String` константы:</span><span class="sxs-lookup"><span data-stu-id="84a72-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="84a72-112">Выражение в правой части знака равенства ( `=` ) часто представляет собой число или литеральную строку, но оно также может быть выражением, результатом которого является число или строка (хотя это выражение не может содержать вызовы функций).</span><span class="sxs-lookup"><span data-stu-id="84a72-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="84a72-113">Константы можно даже определять с точки зрения ранее определенных констант:</span><span class="sxs-lookup"><span data-stu-id="84a72-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="84a72-114">Область определяемых пользователем констант</span><span class="sxs-lookup"><span data-stu-id="84a72-114">Scope of User-Defined Constants</span></span>  

 <span data-ttu-id="84a72-115">`Const`Область действия инструкции аналогична области видимости переменной, объявленной в том же расположении.</span><span class="sxs-lookup"><span data-stu-id="84a72-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="84a72-116">Указать область можно одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="84a72-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="84a72-117">Чтобы создать константу, которая существует только в пределах процедуры, объявите ее внутри этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="84a72-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="84a72-118">Чтобы создать константу, доступную для всех процедур в классе, но не для кода за пределами этого модуля, объявите ее в разделе Declarations класса.</span><span class="sxs-lookup"><span data-stu-id="84a72-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="84a72-119">Чтобы создать константу, доступную всем членам сборки, но не внешним клиентам сборки, объявите ее с помощью `Friend` ключевого слова в разделе Declarations класса.</span><span class="sxs-lookup"><span data-stu-id="84a72-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="84a72-120">Чтобы создать константу, доступную во всем приложении, объявите ее с помощью `Public` ключевого слова в разделе объявлений класс.</span><span class="sxs-lookup"><span data-stu-id="84a72-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="84a72-121">Дополнительные сведения см. [в разделе инструкции. Объявление константы](how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="84a72-121">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="84a72-122">Предотвращение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="84a72-122">Avoiding Circular References</span></span>  

 <span data-ttu-id="84a72-123">Поскольку константы могут быть определены с точки зрения других констант, можно случайно создать *цикл*или циклическую ссылку между двумя или более константами.</span><span class="sxs-lookup"><span data-stu-id="84a72-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="84a72-124">Цикл происходит при наличии двух или более открытых констант, каждая из которых определена в терминах другого, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="84a72-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="84a72-125">При возникновении цикла Visual Basic выдает ошибку компилятора.</span><span class="sxs-lookup"><span data-stu-id="84a72-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a72-126">См. также</span><span class="sxs-lookup"><span data-stu-id="84a72-126">See also</span></span>

- [<span data-ttu-id="84a72-127">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="84a72-127">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="84a72-128">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="84a72-128">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="84a72-129">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="84a72-129">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="84a72-130">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="84a72-130">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="84a72-131">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="84a72-131">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="84a72-132">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="84a72-132">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="84a72-133">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="84a72-133">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="84a72-134">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="84a72-134">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="84a72-135">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="84a72-135">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
