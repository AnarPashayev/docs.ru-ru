---
title: Практическое руководство. Добавление и удаление отдельных элементов коллекции BlockingCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: f895be4c20a0cccad23e27db3d488355a614cbfc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287891"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Практическое руководство. Добавление и удаление отдельных элементов коллекции BlockingCollection
В этом примере показано, как добавлять и удалять элементы <xref:System.Collections.Concurrent.BlockingCollection%601> с блокировкой и без блокировки. Дополнительные сведения о <xref:System.Collections.Concurrent.BlockingCollection%601> см. в разделе [Общие сведения о коллекции BlockingCollection](blockingcollection-overview.md).  
  
 Пример перечисления коллекции <xref:System.Collections.Concurrent.BlockingCollection%601>, пока она не станет пустой, и никакие элементы не будут добавляться, см. в разделе [Практическое руководство. Использование оператора ForEach для удаления элементов в коллекции BlockingCollection](how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Пример  
 В первом примере показано, как добавлять и удалять элементы так, чтобы операции блокировались, если коллекция временно пуста (при извлечении) или достигает максимальной емкости (при добавлении), или если заданное время ожидания истекло. Обратите внимание, что блокирование при максимальной заполненности доступно, только если BlockingCollection создана с указанием максимальной емкости в конструкторе.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Пример  
 Во втором примере показано, как добавлять и извлекать элементы без блокирования операций. Если истекло время ожидания, отсутствуют элементы или достигнута максимальная емкость ограниченной коллекции, то операция <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> или <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> возвращает значение false. Это позволяет потоку некоторое время выполнять другие полезные действия, чтобы позднее повторить попытку получить или добавить элемент, которая ранее завершилась неудачей. Программа также демонстрирует, как реализовать отмену при доступе к <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Общие сведения о коллекции BlockingCollection](blockingcollection-overview.md)
