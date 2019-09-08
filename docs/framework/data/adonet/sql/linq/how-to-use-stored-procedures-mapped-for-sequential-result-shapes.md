---
title: Практическое руководство. Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: bae10e823a274304f21292cf55947a4d4eaccc10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781460"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Практическое руководство. Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами
Этот тип хранимых процедур может создавать несколько результирующих форм, но всегда известно, в каком порядке возвращаются результаты. Этот сценарий противоположен сценарию, в котором порядок возвращения результатов не известен. Дополнительные сведения см. в разделе [Практическое руководство. Используйте хранимые процедуры, сопоставленные](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)с несколькими результирующими формами.  
  
## <a name="example"></a>Пример  
 Ниже представлен код T-SQL для хранимой процедуры, которая последовательно возвращает несколько результирующих наборов.  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Пример  
 Для выполнения этой хранимой процедуры следует использовать код, который выглядит следующим образом:  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>См. также

- [Хранимые процедуры](stored-procedures.md)
