---
title: Практическое руководство. Объявление константы
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 138dd58dac9d1983e35e61f8b98a77810fc6e38b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058850"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="04b4f-102">Практическое руководство. Объявление константы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04b4f-102">How to: Declare A Constant (Visual Basic)</span></span>

<span data-ttu-id="04b4f-103">Используйте оператор, `Const` чтобы объявить константу и задать ее значение.</span><span class="sxs-lookup"><span data-stu-id="04b4f-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="04b4f-104">Объявляя константу, можно присвоить значение понятному имени.</span><span class="sxs-lookup"><span data-stu-id="04b4f-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="04b4f-105">После объявления константы ее нельзя изменить или присвоить ей новое значение.</span><span class="sxs-lookup"><span data-stu-id="04b4f-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="04b4f-106">Константа объявляется в процедуре или в разделе объявлений модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="04b4f-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="04b4f-107">Константы уровня класса или структуры `Private` по умолчанию, но также могут быть объявлены как `Public` , `Friend` , `Protected` или `Protected Friend` для соответствующего уровня доступа к коду.</span><span class="sxs-lookup"><span data-stu-id="04b4f-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="04b4f-108">Константа должна иметь допустимое символьное имя (правила совпадают с правилами для создания имен переменных) и выражение, состоящее из числовых или строковых констант и операторов (но не для вызовов функций).</span><span class="sxs-lookup"><span data-stu-id="04b4f-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="04b4f-109">Объявление константы</span><span class="sxs-lookup"><span data-stu-id="04b4f-109">To declare a constant</span></span>  
  
- <span data-ttu-id="04b4f-110">Напишите объявление, включающее описатель доступа, `Const` ключевое слово и выражение, как показано в следующих примерах:</span><span class="sxs-lookup"><span data-stu-id="04b4f-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="04b4f-111">Если [параметр Infer](../../../language-reference/statements/option-infer-statement.md) имеет значение `Off` и [Option строго](../../../language-reference/statements/option-strict-statement.md) имеет значение `On` , необходимо явно объявить константу, указав тип данных (,,,,,,,,, `Boolean` `Byte` `Char` `DateTime` `Decimal` `Double` `Integer` `Long` `Short` `Single` или `String` ).</span><span class="sxs-lookup"><span data-stu-id="04b4f-111">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="04b4f-112">Если `Option Infer` имеет значение `On` или `Option Strict` является `Off` , можно объявить константу без указания типа данных с `As` предложением.</span><span class="sxs-lookup"><span data-stu-id="04b4f-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="04b4f-113">Компилятор определяет тип константы на основе типа выражения.</span><span class="sxs-lookup"><span data-stu-id="04b4f-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="04b4f-114">Дополнительные сведения см. в разделе [константные и литеральные типы данных](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="04b4f-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="04b4f-115">Объявление константы с явно указанным типом данных</span><span class="sxs-lookup"><span data-stu-id="04b4f-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="04b4f-116">Напишите объявление, включающее `As` ключевое слово и явный тип данных, как показано в следующих примерах:</span><span class="sxs-lookup"><span data-stu-id="04b4f-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="04b4f-117">В одной строке можно объявить несколько констант, хотя код более удобен для чтения, если объявить только одну константу в строке.</span><span class="sxs-lookup"><span data-stu-id="04b4f-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="04b4f-118">При объявлении нескольких констант в одной строке все они должны иметь одинаковый уровень доступа ( `Public` ,,, `Private` `Friend` `Protected` или `Protected Friend` ).</span><span class="sxs-lookup"><span data-stu-id="04b4f-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="04b4f-119">Объявление нескольких констант в одной строке</span><span class="sxs-lookup"><span data-stu-id="04b4f-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="04b4f-120">Разделяйте объявления запятыми и пробелами, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="04b4f-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="04b4f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="04b4f-121">See also</span></span>

- [<span data-ttu-id="04b4f-122">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="04b4f-122">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="04b4f-123">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="04b4f-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="04b4f-124">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="04b4f-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="04b4f-125">Практическое руководство. Объявление константы</span><span class="sxs-lookup"><span data-stu-id="04b4f-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="04b4f-126">Константы, определенные пользователем</span><span class="sxs-lookup"><span data-stu-id="04b4f-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="04b4f-127">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="04b4f-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="04b4f-128">Практическое руководство. Группирование значений связанных констант</span><span class="sxs-lookup"><span data-stu-id="04b4f-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="04b4f-129">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="04b4f-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="04b4f-130">Практическое руководство. Объявление перечислений</span><span class="sxs-lookup"><span data-stu-id="04b4f-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="04b4f-131">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="04b4f-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="04b4f-132">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="04b4f-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="04b4f-133">Практическое руководство. Перебор элементов перечисления</span><span class="sxs-lookup"><span data-stu-id="04b4f-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="04b4f-134">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="04b4f-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="04b4f-135">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="04b4f-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="04b4f-136">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="04b4f-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="04b4f-137">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="04b4f-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="04b4f-138">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="04b4f-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="04b4f-139">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="04b4f-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="04b4f-140">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="04b4f-140">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="04b4f-141">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="04b4f-141">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
