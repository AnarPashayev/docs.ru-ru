---
title: Оператор Implements (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 865e99aa0e27591d10fde1465047a2e6bf183bbf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581792"
---
# <a name="implements-statement"></a><span data-ttu-id="92230-102">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="92230-102">Implements Statement</span></span>
<span data-ttu-id="92230-103">Указывает один или несколько интерфейсов или элементов интерфейса, которые должны быть реализованы в определении класса или структуры, в котором они отображаются.</span><span class="sxs-lookup"><span data-stu-id="92230-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92230-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92230-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="92230-105">Части</span><span class="sxs-lookup"><span data-stu-id="92230-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="92230-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="92230-106">Required.</span></span> <span data-ttu-id="92230-107">Интерфейс, свойства, процедуры и события которого должны быть реализованы соответствующими элементами в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="92230-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="92230-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="92230-108">Required.</span></span> <span data-ttu-id="92230-109">Член реализуемого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="92230-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92230-110">Заметки</span><span class="sxs-lookup"><span data-stu-id="92230-110">Remarks</span></span>  
 <span data-ttu-id="92230-111">Интерфейс — это коллекция прототипов, представляющих члены (свойства, процедуры и события), которые инкапсулирует интерфейс.</span><span class="sxs-lookup"><span data-stu-id="92230-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="92230-112">Интерфейсы содержат только объявления для членов; классы и структуры реализуют эти члены.</span><span class="sxs-lookup"><span data-stu-id="92230-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="92230-113">Дополнительные сведения см. в статье [Интерфейсы](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="92230-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="92230-114">Оператор `Implements` должен следовать непосредственно за инструкцией `Class` или `Structure`.</span><span class="sxs-lookup"><span data-stu-id="92230-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="92230-115">При реализации интерфейса необходимо реализовать все члены, объявленные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="92230-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="92230-116">Пропуск любого члена считается синтаксической ошибкой.</span><span class="sxs-lookup"><span data-stu-id="92230-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="92230-117">Для реализации отдельного элемента необходимо указать ключевое слово [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (отдельно от оператора `Implements`) при объявлении члена в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="92230-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="92230-118">Дополнительные сведения см. в статье [Интерфейсы](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="92230-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="92230-119">Классы могут использовать [закрытые](../../../visual-basic/language-reference/modifiers/private.md) реализации свойств и процедур, но эти члены доступны только путем приведения экземпляра реализующего класса к переменной, объявленной как тип интерфейса.</span><span class="sxs-lookup"><span data-stu-id="92230-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92230-120">Пример</span><span class="sxs-lookup"><span data-stu-id="92230-120">Example</span></span>  
 <span data-ttu-id="92230-121">В следующем примере показано, как использовать оператор `Implements` для реализации членов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="92230-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="92230-122">Он определяет интерфейс с именем `ICustomerInfo` с событием, свойством и процедурой.</span><span class="sxs-lookup"><span data-stu-id="92230-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="92230-123">Класс `customerInfo` реализует все члены, определенные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="92230-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="92230-124">Обратите внимание, что класс `customerInfo` использует инструкцию `Implements` в отдельной строке исходного кода, чтобы указать, что класс реализует все члены интерфейса `ICustomerInfo`.</span><span class="sxs-lookup"><span data-stu-id="92230-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="92230-125">Затем каждый член класса использует ключевое слово `Implements` как часть его объявления члена, чтобы указать, что он реализует этот член интерфейса.</span><span class="sxs-lookup"><span data-stu-id="92230-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92230-126">Пример</span><span class="sxs-lookup"><span data-stu-id="92230-126">Example</span></span>  
 <span data-ttu-id="92230-127">В следующих двух процедурах показано, как можно использовать интерфейс, реализованный в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="92230-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="92230-128">Чтобы протестировать реализацию, добавьте эти процедуры в проект и вызовите процедуру `testImplements`.</span><span class="sxs-lookup"><span data-stu-id="92230-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="92230-129">См. также</span><span class="sxs-lookup"><span data-stu-id="92230-129">See also</span></span>

- [<span data-ttu-id="92230-130">Implements</span><span class="sxs-lookup"><span data-stu-id="92230-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="92230-131">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="92230-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="92230-132">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="92230-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
