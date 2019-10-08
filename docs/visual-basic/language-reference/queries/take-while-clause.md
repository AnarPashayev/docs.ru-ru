---
title: Предложение Take While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004672"
---
# <a name="take-while-clause-visual-basic"></a>Предложение Take While (Visual Basic)
Включает элементы в коллекцию, если заданное условие имеет значение `true`, и пропускает остальные элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Части  
  
|Термин|Определение|  
|---|---|  
|`expression`|Обязательный. Выражение, представляющее условие для проверки элементов. Выражение должно возвращать значение `Boolean` или функциональный эквивалент, например `Integer` для оценки как `Boolean`.|  
  
## <a name="remarks"></a>Примечания  
 Предложение `Take While` включает элементы из начала результата запроса, пока переданный `expression` не возвращает `false`. После того как `expression` возвращает `false`, запрос будет обходить все оставшиеся элементы. @No__t-0 игнорируется для оставшихся результатов.  
  
 Предложение `Take While` отличается от предложения `Where` тем, что предложение @no__t 2 может использоваться для включения всех элементов из запроса, удовлетворяющего определенному условию. Предложение `Take While` включает элементы только до первого момента, когда условие не будет удовлетворено. Предложение `Take While` наиболее полезно при работе с упорядоченным результатом запроса.  
  
## <a name="example"></a>Пример  
 В следующем примере кода предложение `Take While` используется для получения результатов до тех пор, пока не будет найден первый клиент без заказов.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>См. также

- [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)
- [Запросы](../../../visual-basic/language-reference/queries/index.md)
- [Предложение Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Предложение From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Предложение Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Предложение Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Предложения Where](../../../visual-basic/language-reference/queries/where-clause.md)
