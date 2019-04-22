---
title: '>>Оператор = (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838967"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1c3d3-102">>> =-оператор (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c3d3-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="1c3d3-103">Выполняет арифметическое смещение вправо от значения переменной или свойства и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c3d3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c3d3-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1c3d3-105">Части</span><span class="sxs-lookup"><span data-stu-id="1c3d3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1c3d3-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-106">Required.</span></span> <span data-ttu-id="1c3d3-107">Переменная или свойство целочисленного типа (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, или `ULong`).</span><span class="sxs-lookup"><span data-stu-id="1c3d3-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1c3d3-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-108">Required.</span></span> <span data-ttu-id="1c3d3-109">Числовое выражение типа данных, который расширяется до `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c3d3-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="1c3d3-110">Remarks</span></span>  
 <span data-ttu-id="1c3d3-111">Элемент, на левой стороне `>>=` оператор может быть простой скалярной переменной, свойства или элемента массива.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1c3d3-112">Не может быть переменной или свойству [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1c3d3-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1c3d3-113">`>>=` Оператор сначала выполняет арифметическое смещение вправо от значения переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1c3d3-114">Затем оператор присваивает результат этой операции переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1c3d3-115">Арифметические сдвиги не являются циклическими, это означает, что биты, сдвигаемые результата, не подставляются на другом конце.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1c3d3-116">В арифметического сдвига вправо биты, сдвигаемые дальше крайней правой позиции отбрасываются, а первый бит распространяется в позиции битов, освобожденные слева.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1c3d3-117">Это означает, что если `variableorproperty` имеет отрицательное значение, освобождаемые устанавливается один.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1c3d3-118">Если `variableorproperty` положительно, или если его тип данных является тип без знака, освобождаемые присваивается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1c3d3-119">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="1c3d3-119">Overloading</span></span>  
 <span data-ttu-id="1c3d3-120">[>> Оператор](../../../visual-basic/language-reference/operators/right-shift-operator.md) может быть *перегружены*, что означает, что класс или структура может переопределить его поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1c3d3-121">Перегрузка `>>` оператор влияет на поведение `>>=` оператор.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1c3d3-122">Если код использует `>>=` для класса или структуры, перегружающей `>>`, убедитесь, что его переопределенное.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1c3d3-123">Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1c3d3-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c3d3-124">Пример</span><span class="sxs-lookup"><span data-stu-id="1c3d3-124">Example</span></span>  
 <span data-ttu-id="1c3d3-125">В следующем примере используется `>>=` оператор, чтобы сдвинуть битовый шаблон из `Integer` переменной вправо на заданную величину и назначает полученное значение переменной.</span><span class="sxs-lookup"><span data-stu-id="1c3d3-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1c3d3-126">См. также</span><span class="sxs-lookup"><span data-stu-id="1c3d3-126">See also</span></span>

- [<span data-ttu-id="1c3d3-127">Оператор >></span><span class="sxs-lookup"><span data-stu-id="1c3d3-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="1c3d3-128">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="1c3d3-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="1c3d3-129">Операторы сдвига битов</span><span class="sxs-lookup"><span data-stu-id="1c3d3-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="1c3d3-130">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c3d3-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1c3d3-131">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="1c3d3-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1c3d3-132">Операторы</span><span class="sxs-lookup"><span data-stu-id="1c3d3-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
