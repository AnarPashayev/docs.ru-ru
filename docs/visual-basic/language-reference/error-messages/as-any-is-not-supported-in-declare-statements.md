---
title: "'As Any' не поддерживается в операторах Declare"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310698"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'As Any' не поддерживается в операторах Declare
`Any` Использовался тип данных с помощью `Declare` операторов в Visual Basic 6.0 и более ранних версий, чтобы разрешить использование аргументов, которые могут содержать данные любого типа. Visual Basic поддерживает перегрузку, тем не менее и это делает `Any` устаревший тип данных.  
  
 **Идентификатор ошибки:** BC30828  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Объявите параметры конкретного типа, который вы хотите использовать; Например.  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. Используйте <xref:System.Runtime.InteropServices.MarshalAsAttribute> атрибут для указания `As Any` при `Void*` ожидается вызываемой процедуры.  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Пошаговое руководство: Вызов API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Оператор Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Создание прототипов в управляемом коде](../../../framework/interop/creating-prototypes-in-managed-code.md)
