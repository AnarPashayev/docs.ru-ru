---
title: Значения объектных переменных
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 1dd3e8cd68086fe116daf0678a1a19881f1ae9c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410352"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="e66fd-102">Значения объектных переменных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e66fd-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="e66fd-103">Переменная [типа данных Object](../../../language-reference/data-types/object-data-type.md) может ссылаться на данные любого типа.</span><span class="sxs-lookup"><span data-stu-id="e66fd-103">A variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="e66fd-104">Значение, сохраняемое в `Object` переменной, хранится в других местах памяти, а сама переменная содержит указатель на данные.</span><span class="sxs-lookup"><span data-stu-id="e66fd-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="e66fd-105">Функции-классификаторы объектов</span><span class="sxs-lookup"><span data-stu-id="e66fd-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="e66fd-106">Visual Basic предоставляет функции, возвращающие сведения о том `Object` , на что ссылается переменная, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="e66fd-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="e66fd-107">Функция</span><span class="sxs-lookup"><span data-stu-id="e66fd-107">Function</span></span>|<span data-ttu-id="e66fd-108">Возвращает значение true, если объектная переменная ссылается на</span><span class="sxs-lookup"><span data-stu-id="e66fd-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="e66fd-109">Массив значений, а не одно значение</span><span class="sxs-lookup"><span data-stu-id="e66fd-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="e66fd-110">Значение [типа данных Date](../../../language-reference/data-types/date-data-type.md) или строка, которая может быть интерпретирована как значение даты и времени</span><span class="sxs-lookup"><span data-stu-id="e66fd-110">A [Date Data Type](../../../language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="e66fd-111">Объект типа <xref:System.DBNull> , представляющий отсутствующие или несуществующие данные</span><span class="sxs-lookup"><span data-stu-id="e66fd-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="e66fd-112">Объект исключения, производный от<xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="e66fd-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="e66fd-113">[Ничего](../../../language-reference/nothing.md), т. е. в данный момент ни один объект не назначен переменной</span><span class="sxs-lookup"><span data-stu-id="e66fd-113">[Nothing](../../../language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="e66fd-114">Число или строка, которую можно интерпретировать как число</span><span class="sxs-lookup"><span data-stu-id="e66fd-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="e66fd-115">Ссылочный тип (например, строка, массив, делегат или тип класса);</span><span class="sxs-lookup"><span data-stu-id="e66fd-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="e66fd-116">Эти функции можно использовать, чтобы избежать отправки недопустимого значения в операцию или процедуру.</span><span class="sxs-lookup"><span data-stu-id="e66fd-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="e66fd-117">Оператор TypeOf</span><span class="sxs-lookup"><span data-stu-id="e66fd-117">TypeOf Operator</span></span>  
 <span data-ttu-id="e66fd-118">[Оператор typeof](../../../language-reference/operators/typeof-operator.md) также можно использовать для определения того, относится ли переменная объекта к конкретному типу данных.</span><span class="sxs-lookup"><span data-stu-id="e66fd-118">You can also use the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="e66fd-119">`TypeOf`Выражение... `Is` принимает значение, `True` Если тип операнда во время выполнения является производным от или реализует указанный тип.</span><span class="sxs-lookup"><span data-stu-id="e66fd-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="e66fd-120">В следующем примере используется `TypeOf` для объектных переменных, ссылающихся на значения и ссылочные типы.</span><span class="sxs-lookup"><span data-stu-id="e66fd-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
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
  
 <span data-ttu-id="e66fd-121">В предыдущем примере в окно **отладки** записываются следующие строки:</span><span class="sxs-lookup"><span data-stu-id="e66fd-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="e66fd-122">Объектная переменная `num` ссылается на данные типа `Integer` и `frm` ссылается на объект класса <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="e66fd-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="e66fd-123">Массивы объектов</span><span class="sxs-lookup"><span data-stu-id="e66fd-123">Object Arrays</span></span>  
 <span data-ttu-id="e66fd-124">Можно объявить и использовать массив `Object` переменных.</span><span class="sxs-lookup"><span data-stu-id="e66fd-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="e66fd-125">Это полезно, когда необходимо управлять множеством типов данных и классов объектов.</span><span class="sxs-lookup"><span data-stu-id="e66fd-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="e66fd-126">Все элементы в массиве должны иметь один и тот же объявленный тип данных.</span><span class="sxs-lookup"><span data-stu-id="e66fd-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="e66fd-127">Объявление этого типа данных как `Object` позволяет хранить объекты и экземпляры классов вместе с другими типами данных в массиве.</span><span class="sxs-lookup"><span data-stu-id="e66fd-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66fd-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e66fd-128">See also</span></span>

- [<span data-ttu-id="e66fd-129">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="e66fd-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e66fd-130">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="e66fd-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="e66fd-131">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="e66fd-131">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="e66fd-132">Практическое руководство. Ссылка на текущий экземпляр объекта</span><span class="sxs-lookup"><span data-stu-id="e66fd-132">How to: Refer to the Current Instance of an Object</span></span>](how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="e66fd-133">Практическое руководство. Определение типа, на который указывает объектная переменная</span><span class="sxs-lookup"><span data-stu-id="e66fd-133">How to: Determine What Type an Object Variable Refers To</span></span>](how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="e66fd-134">Практическое руководство. Определение наличия связи между двумя объектами</span><span class="sxs-lookup"><span data-stu-id="e66fd-134">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="e66fd-135">Практическое руководство. Определение идентичности двух объектов</span><span class="sxs-lookup"><span data-stu-id="e66fd-135">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="e66fd-136">Типы данных</span><span class="sxs-lookup"><span data-stu-id="e66fd-136">Data Types</span></span>](../data-types/index.md)
