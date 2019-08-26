---
title: Практическое руководство. Управление порядком в запросе PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7416f2f9c200d687d3f2c1f14b01cafdb48f85b1
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988191"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Практическое руководство. Управление порядком в запросе PLINQ
В этих примерах показано, как управлять правилами упорядочения в запросе PLINQ с помощью метода расширения <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
> [!WARNING]
> Эти примеры предназначены в основном для демонстрации использования, и могут выполняться быстрее или не быстрее аналогичных последовательных запросов LINQ to Objects.  
  
## <a name="example"></a>Пример  
 В следующем примере сохраняется порядок исходной последовательности. Иногда это необходимо. Например, некоторым операторам запроса нужна упорядоченная исходная последовательность для предоставления правильных результатов.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано несколько операторов запроса, для которых может ожидаться упорядоченная исходная последовательность. Эти операторы могут работать и с неупорядоченными последовательностями, но иногда возвращают непредвиденные результаты.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Чтобы запустить этот метод, вставьте его в класс PLINQDataSample из проекта [Пример данных PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) и нажмите клавишу F5.  
  
## <a name="example"></a>Пример  
 В следующем примере сохраняется порядок последовательности в первой части запроса, затем отменяется упорядочение, чтобы повысить производительность предложения join, и снова применяется упорядочение для конечной результирующей последовательности.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Чтобы запустить этот метод, вставьте его в класс PLINQDataSample из проекта [Пример данных PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) и нажмите клавишу F5.  
  
## <a name="see-also"></a>См. также

- <xref:System.Linq.ParallelEnumerable>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
