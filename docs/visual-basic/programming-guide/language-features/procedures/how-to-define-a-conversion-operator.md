---
title: Практическое руководство. Определить оператор преобразования (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: cf7bfdd09c7f3429f9c730a7aec34b24af3f2e9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863718"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Практическое руководство. Определить оператор преобразования (Visual Basic)
Если вы определили, класса или структуры, можно определить оператор преобразования типа между типом класса или структуры и другой тип данных (таких как `Integer`, `Double`, или `String`).  
  
 Определите преобразование типа как [функция CType](../../../../visual-basic/language-reference/functions/ctype-function.md) процедуры внутри класса или структуры. Все процедуры преобразования должны быть `Public Shared`, и каждый из них необходимо указать либо [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) или [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Определение оператора в классе или структуре также называется *перегрузка* оператора.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется операторы преобразования между структурой `digit` и `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Вы можете проверить структуру `digit` следующим кодом.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>См. также

- [Процедуры операторов](./operator-procedures.md)
- [Практическое руководство. Определение оператора](./how-to-define-an-operator.md)
- [Практическое руководство. Вызов процедуры оператора](./how-to-call-an-operator-procedure.md)
- [Практическое руководство. Используйте класс, в котором определяются операторы](./how-to-use-a-class-that-defines-operators.md)
- [Оператор Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Оператор Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Практическое руководство. Объявление структуры](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Явные и неявные преобразования](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Расширяющие и сужающие преобразования](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
