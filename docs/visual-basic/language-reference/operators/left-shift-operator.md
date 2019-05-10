---
title: << Оператора (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: e11dbc453934f1aac4a8092cdc6539ec11f0cc21
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663183"
---
# <a name="-operator-visual-basic"></a>\<\< Operator (Visual Basic)
Выполняет арифметическое смещение влево битового шаблона.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Части  
 `result`  
 Обязательный. Целое числовое значение. Результат сдвига битового шаблона. Тип данных является таким же, как `pattern`.  
  
 `pattern`  
 Обязательный. Целое числовое выражение. Битовый шаблон должны сдвигаться. Тип данных должен быть целочисленный тип (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, или `ULong`).  
  
 `amount`  
 Обязательный. Числовое выражение. Количество битов для сдвига битового шаблона. Тип данных должен быть `Integer` или расширяющего преобразования к `Integer`.  
  
## <a name="remarks"></a>Примечания  
 Арифметические сдвиги не являются циклическими, это означает, что биты, сдвигаемые результата, не подставляются на другом конце. В арифметического сдвига влево биты, перемещен за пределы диапазона для типа данных результата отбрасываются и освободившиеся справа позиции битов заполняются нулями.  
  
 Чтобы предотвратить сдвиг на количество битов, превышающее битов результата, Visual Basic маскирует значение `amount` с маской размер, соответствующий тип данных `pattern`. Двоичное AND этих значений используется для сдвига. Далее приведены маски размера.  
  
|Тип данных `pattern`|Размер маски (десятичное)|Размер маски (шестнадцатеричный)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Если `amount` равно нулю, значение `result` идентично значению `pattern`. Если `amount` имеет отрицательное значение, он берется значение без знака и маскируется соответствующий размер маски.  
  
 Арифметические сдвиги никогда не создают исключения переполнения.  
  
> [!NOTE]
>  `<<` Оператор может быть *перегружены*, что означает, что класс или структура может переопределить его поведение, если операнд имеет тип этого класса или структуры. Если ваш код использует этот оператор для такого класса или структуры, убедитесь, что переопределенное его. Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Пример  
 В следующем примере используется `<<` оператор для выполнения арифметических левых сдвигов целых значений. Результат всегда имеет тот же тип данных, выражения был перемещен.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Далее приведены результаты предыдущего примера.  
  
- `result1` — 192 (0000 0000 1100 0000).  
  
- `result2` равен 3072 (0000 1100 0000 0000).  
  
- `result3` — от -32768 (1000 0000 0000 0000).  
  
- `result4` — 384 (0000 0001 1000 0000).  
  
- `result5` значение 0 (сдвигаются 15 разрядами слева).  
  
 Величина сдвига для `result4` вычисляется как 17 и 15, что равно 1.  
  
## <a name="see-also"></a>См. также

- [Операторы сдвига битов](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Операторы присваивания](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Оператор <<=](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Порядок применения операторов в Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Список операторов, сгруппированных по функциональному назначению](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Арифметические операторы в Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
