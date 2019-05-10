---
title: Не удается преобразовать анонимный тип в дерево выражений, поскольку он содержит поле, которое было использовано в инициализации другого поля
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: 045061f403b301d460bc85d161c1d6dee9c7d9f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602405"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="d964a-102">Не удается преобразовать анонимный тип в дерево выражений, поскольку он содержит поле, которое было использовано в инициализации другого поля</span><span class="sxs-lookup"><span data-stu-id="d964a-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="d964a-103">Компилятор не принимает преобразование анонимных в дерево выражения, когда одно свойство анонимного типа используется для инициализации другого свойства анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="d964a-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="d964a-104">Например, в следующем коде `Prop1` объявлена в списке инициализации, а затем используется в качестве начального значения для `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="d964a-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d964a-105">**Идентификатор ошибки:** BC36548</span><span class="sxs-lookup"><span data-stu-id="d964a-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d964a-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d964a-106">To correct this error</span></span>  
  
- <span data-ttu-id="d964a-107">Назначать начальное значение для `Prop1` локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="d964a-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="d964a-108">Назначьте этой переменной к обоим `Prop1` и `Prop2`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="d964a-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d964a-109">См. также</span><span class="sxs-lookup"><span data-stu-id="d964a-109">See also</span></span>

- [<span data-ttu-id="d964a-110">Анонимные типы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d964a-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- <span data-ttu-id="d964a-111">[Expression Trees (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="d964a-111">[Expression Trees (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md)</span></span>
- [<span data-ttu-id="d964a-112">Практическое руководство. Использование деревьев выражений для построения динамических запросов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d964a-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
