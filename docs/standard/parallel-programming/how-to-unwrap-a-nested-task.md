---
title: Практическое руководство. Извлечение вложенной задачи из оболочки
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288034"
---
# <a name="how-to-unwrap-a-nested-task"></a>Практическое руководство. Извлечение вложенной задачи из оболочки
Вы можете вернуть задачу из метода, и затем ожидать ее выполнения или продолжить работу после нее, как показано в следующем примере.  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 В предыдущем примере свойство <xref:System.Threading.Tasks.Task%601.Result%2A> имеет тип `string` (`String` в Visual Basic).  
  
 Но в некоторых сценариях будет удобно создать в задаче другую задачу и возвратить эту вложенную задачу. В этом случае `TResult` вызывающей задачи является новой задачей. В следующем примере в свойстве Result возвращается `Task<Task<string>>` (в C#) или `Task(Of Task(Of String))` (в Visual Basic).  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Вы можете написать свой код, который распаковывает внешнюю задачу и извлекает исходную задачу и ее свойство <xref:System.Threading.Tasks.Task%601.Result%2A>. Но обработка исключений и возможных запросов отмены существенно усложняет такой код. Поэтому в такой ситуации мы рекомендуем использовать один из методов расширения <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, как показано в следующем примере.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 С помощью методов <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> можно преобразовать любой объект `Task<Task>` или `Task<Task<TResult>>` (`Task(Of Task)` или `Task(Of Task(Of TResult))` в Visual Basic) в `Task` или `Task<TResult>` (`Task(Of TResult)` в Visual Basic). Новая задача в полной мере представляет внутреннюю вложенную задачу с поддержкой состояния отмены и всех исключений.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать методы расширения <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Асинхронное программирование на основе задач](task-based-asynchronous-programming.md)
