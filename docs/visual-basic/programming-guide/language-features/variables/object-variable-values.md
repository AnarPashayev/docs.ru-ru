---
title: Значения объектных переменных (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004583"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="01e2d-102">Значения объектных переменных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01e2d-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="01e2d-103">Переменная [типа данных Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) может ссылаться на данные любого типа.</span><span class="sxs-lookup"><span data-stu-id="01e2d-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="01e2d-104">Значение, сохраняемое в переменной `Object`, хранится в любом месте в памяти, а сама переменная содержит указатель на данные.</span><span class="sxs-lookup"><span data-stu-id="01e2d-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="01e2d-105">Функции-классификаторы объектов</span><span class="sxs-lookup"><span data-stu-id="01e2d-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="01e2d-106">Visual Basic предоставляет функции, возвращающие сведения о том, на что ссылается переменная `Object`, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="01e2d-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="01e2d-107">Функция</span><span class="sxs-lookup"><span data-stu-id="01e2d-107">Function</span></span>|<span data-ttu-id="01e2d-108">Возвращает значение true, если объектная переменная ссылается на</span><span class="sxs-lookup"><span data-stu-id="01e2d-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="01e2d-109">Массив значений, а не одно значение</span><span class="sxs-lookup"><span data-stu-id="01e2d-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="01e2d-110">Значение [типа данных Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) или строка, которая может быть интерпретирована как значение даты и времени</span><span class="sxs-lookup"><span data-stu-id="01e2d-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="01e2d-111">Объект типа <xref:System.DBNull>, представляющий отсутствующие или несуществующие данные</span><span class="sxs-lookup"><span data-stu-id="01e2d-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="01e2d-112">Объект Exception, производный от <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="01e2d-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="01e2d-113">[Ничего](../../../../visual-basic/language-reference/nothing.md), т. е. в данный момент ни один объект не назначен переменной</span><span class="sxs-lookup"><span data-stu-id="01e2d-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="01e2d-114">Число или строка, которую можно интерпретировать как число</span><span class="sxs-lookup"><span data-stu-id="01e2d-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="01e2d-115">Ссылочный тип (например, строка, массив, делегат или тип класса);</span><span class="sxs-lookup"><span data-stu-id="01e2d-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="01e2d-116">Эти функции можно использовать, чтобы избежать отправки недопустимого значения в операцию или процедуру.</span><span class="sxs-lookup"><span data-stu-id="01e2d-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="01e2d-117">Оператор TypeOf</span><span class="sxs-lookup"><span data-stu-id="01e2d-117">TypeOf Operator</span></span>  
 <span data-ttu-id="01e2d-118">[Оператор typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) также можно использовать для определения того, относится ли переменная объекта к конкретному типу данных.</span><span class="sxs-lookup"><span data-stu-id="01e2d-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="01e2d-119">Выражение `TypeOf`... `Is` принимает значение `True`, если тип времени выполнения операнда является производным от или реализует указанный тип.</span><span class="sxs-lookup"><span data-stu-id="01e2d-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="01e2d-120">В следующем примере `TypeOf` используется для переменных объекта, ссылающихся на значения и ссылочные типы.</span><span class="sxs-lookup"><span data-stu-id="01e2d-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="01e2d-121">В предыдущем примере в окно **отладки** записываются следующие строки:</span><span class="sxs-lookup"><span data-stu-id="01e2d-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="01e2d-122">Объектная переменная `num` ссылается на данные типа `Integer`, а `frm` — на объект класса <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="01e2d-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="01e2d-123">Массивы объектов</span><span class="sxs-lookup"><span data-stu-id="01e2d-123">Object Arrays</span></span>  
 <span data-ttu-id="01e2d-124">Можно объявить и использовать массив переменных типа `Object`.</span><span class="sxs-lookup"><span data-stu-id="01e2d-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="01e2d-125">Это полезно, когда необходимо управлять множеством типов данных и классов объектов.</span><span class="sxs-lookup"><span data-stu-id="01e2d-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="01e2d-126">Все элементы в массиве должны иметь один и тот же объявленный тип данных.</span><span class="sxs-lookup"><span data-stu-id="01e2d-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="01e2d-127">Объявление этого типа данных как `Object` позволяет хранить объекты и экземпляры классов вместе с другими типами данных в массиве.</span><span class="sxs-lookup"><span data-stu-id="01e2d-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e2d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="01e2d-128">See also</span></span>

- [<span data-ttu-id="01e2d-129">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="01e2d-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="01e2d-130">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="01e2d-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="01e2d-131">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="01e2d-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- <span data-ttu-id="01e2d-132">[Практическое руководство. Ссылка на текущий экземпляр объекта @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="01e2d-132">[How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)</span></span>
- <span data-ttu-id="01e2d-133">[Практическое руководство. Определение типа, на который ссылается объектная переменная, в значение @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="01e2d-133">[How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)</span></span>
- <span data-ttu-id="01e2d-134">[Практическое руководство. Определить, связаны ли два объекта, @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="01e2d-134">[How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)</span></span>
- <span data-ttu-id="01e2d-135">[Практическое руководство. Определить, идентичны ли два объекта @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="01e2d-135">[How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)</span></span>
- [<span data-ttu-id="01e2d-136">Типы данных</span><span class="sxs-lookup"><span data-stu-id="01e2d-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
