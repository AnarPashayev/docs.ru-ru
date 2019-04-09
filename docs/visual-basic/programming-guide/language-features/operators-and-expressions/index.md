---
title: Операторы и выражения в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: b762c3002913cbd925579ef28f2aa01411976c32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073654"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Операторы и выражения в Visual Basic
*Оператор* представляет собой элемент кода, который выполняет операцию с одним элементом кода или несколькими, содержащими значения. К элементам значений относятся переменные, константы, литералы, свойства, возвращаемые значения из процедур `Function` и `Operator`, а также выражения.  
  
 *Выражение* представляет собой набор элементов значений в сочетании с операторами, результатом которого является новое значение. Операторы работают с элементами значений, выполняя вычисления, сравнения и другие операции.  
  
## <a name="types-of-operators"></a>Типы операторов  
 Visual Basic предоставляет следующие типы операторов:  
  
-   [Арифметические операторы](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) выполняют обычные вычисления с числовыми значениями, включая сдвиг их битовых шаблонов.  
  
-   [Операторы сравнения](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) сравнивают два выражения и возвращают значение `Boolean`, соответствующее результату сравнения.  
  
-   [Операторы объединения](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) соединяют несколько строк в одну.  
  
-   [Логические и побитовые операторы в Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) объединяют `Boolean` или числовые значения и возвращают результат того же типа данных, что и значения.  
  
 Элементы значений, объединенные с оператором, называются *операндами* этого оператора. Операторы, объединенные с элементами значений, формируют выражения. Исключением является оператор присваивания, который образует *инструкцию*. Дополнительные сведения см. в разделе [Выписки](../../../../visual-basic/programming-guide/language-features/statements.md).  
  
## <a name="evaluation-of-expressions"></a>Вычисление выражений  
 Конечный результат выражения представляет собой значение, которое обычно имеет знакомый тип данных, например `Boolean`, `String` или числовой тип.  
  
 Ниже приведены примеры выражений.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Несколько операторов могут выполнять действия в одном выражении или инструкции, как показано в следующем примере.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 В приведенном выше примере Visual Basic выполняет операции в выражении справа от оператора присваивания (`=`), затем присваивает результирующее значение переменной `x` слева. С практической точки зрения в выражение можно объединять сколько угодно операторов, но следует учитывать [приоритет операторов в Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) для получения желаемых результатов.  

## <a name="see-also"></a>См. также

- [Операторы](../../../../visual-basic/language-reference/operators/index.md)
- [Эффективное сочетание операторов](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Операторы](../../../../visual-basic/language-reference/statements/index.md)
