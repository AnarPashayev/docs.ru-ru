---
title: Оператор OrElse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835243"
---
# <a name="orelse-operator-visual-basic"></a>Оператор OrElse (Visual Basic)
Выполняет сокращенное вычисление инклюзивного логического сложения двух выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Части  
 `result`  
 Обязательный. Произвольное выражение `Boolean` .  
  
 `expression1`  
 Обязательный. Произвольное выражение `Boolean` .  
  
 `expression2`  
 Обязательный. Произвольное выражение `Boolean` .  
  
## <a name="remarks"></a>Примечания  
 Логическая операция называется *сокращенной* , если скомпилированный код может обходить вычисление одного выражения в зависимости от результата другого выражения. Если результат вычисления первого выражения определяет окончательный результат операции, нет необходимости оценивать второе выражение, так как оно не может изменить окончательный результат. Сокращенное вычисление может повысить производительность, если пропущенное выражение является сложным или если оно включает вызовы процедур.  
  
 Если одно или оба выражения имеют значение `True`, `result` — `True`. В следующей таблице показано, как определяется `result`.  
  
|Если `expression1` имеет значение|И `expression2` является|Значение `result` равно|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(не вычислено)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Типы данных  
 Оператор `OrElse` определен только для [типа данных Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). При необходимости Visual Basic преобразует каждый операнд в `Boolean` перед вычислением выражения. Если результат присваивается числовому типу, Visual Basic преобразует его из `Boolean` в этот тип, чтобы `False` стало `0`, а `True` преобразуется в `-1`.
Дополнительные сведения см. в разделе [преобразования логических типов](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Перегрузка  
 [Оператор OR](../../../visual-basic/language-reference/operators/or-operator.md) и [оператор IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) могут быть *перегружены*, что означает, что класс или структура может переопределить их поведение, если операнд имеет тип этого класса или структуры. Перегрузка операторов `Or` и `IsTrue` влияет на поведение оператора `OrElse`. Если в коде используется `OrElse` для класса или структуры, которая перегружает `Or` и `IsTrue`, убедитесь, что вы понимаете их переопределенное поведение. Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Пример  
 В следующем примере оператор `OrElse` используется для выполнения логического сложения двух выражений. Результатом является значение `Boolean`, которое показывает, имеет ли одно из двух выражений значение true. Если первое выражение — `True`, второе значение не вычисляется.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 В предыдущем примере создаются результаты `True`, `True` и `False` соответственно. При вычислении `firstCheck` второе выражение не вычисляется, поскольку первый уже `True`. Однако второе выражение вычисляется в вычислении `secondCheck`.  
  
## <a name="example"></a>Пример  
 В следующем примере показана инструкция `If`... `Then`, содержащая два вызова процедур. Если первый вызов возвращает `True`, вторая процедура не вызывается. Это может привести к непредвиденным результатам, если вторая процедура выполняет важные задачи, которые всегда должны выполняться при выполнении этого раздела кода.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>См. также

- [Логические и битовые операторы (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Порядок применения операторов в Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Список операторов, сгруппированных по функциональному назначению](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Оператор Or](../../../visual-basic/language-reference/operators/or-operator.md)
- [Оператор IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Логические и побитовые операторы в Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
