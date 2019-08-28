---
title: Практическое руководство. Перебор каталогов с файлами с помощью PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f80f1903c4187a8da93d42ec6de363d097bcc37
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988175"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Практическое руководство. Перебор каталогов с файлами с помощью PLINQ
В этом примере показаны два простых способа параллельного выполнения операций с каталогами файлов. Первый запрос использует метод <xref:System.IO.Directory.GetFiles%2A>, чтобы заполнить массив имен всех файлов и подкаталогов в каталоге. Этот метод не возвращает результаты, пока не заполнит весь массив, поэтому в начале его работы можно ожидать существенную задержку. Но после заполнения массива PLINQ сможет очень быстро обрабатывать его параллельно.  
  
 Второй запрос использует статические методы <xref:System.IO.Directory.EnumerateDirectories%2A> и <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, которые сразу начинают возвращать результаты. Этот подход может оказаться быстрее, если вы просматриваете большие деревья каталогов, но разница с первым примером по времени обработки может зависеть от многих факторов.  
  
> [!WARNING]
> Этот пример предназначен только для демонстрации использования, и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects. См. дополнительные сведения об [ускорении выполнения в PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показан итеративный обход каталогов с файлами для простых сценариев, когда в дереве есть доступ ко всем каталогам, нет больших файлов и существенных задержек при доступе к ним. При таком подходе предполагается задержка в начале, пока код заполняет массив имен файлов.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Пример  
 В следующем примере показан итеративный обход каталогов с файлами для простых сценариев, когда в дереве есть доступ ко всем каталогам, нет больших файлов и существенных задержек при доступе к ним. При таком подходе результаты возвращаются гораздо быстрее, чем в предыдущем примере.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Если используется <xref:System.IO.Directory.GetFiles%2A>, следите за наличием нужных разрешений для всех каталогов в дереве. В противном случае создается исключение и результаты не возвращаются. При использовании <xref:System.IO.Directory.EnumerateDirectories%2A> в запросе PLINQ довольно трудно обрабатывать исключения ввода-вывода настолько мягко, чтобы можно было продолжить работу. Если код должен обрабатывать исключения с ошибками ввода-вывода или несанкционированного доступа, то мы рекомендуем применить другой подход, описанный в статье [Практическое руководство. Перебор каталогов с файлами с помощью параллельного класса](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Если есть риск задержки при операциях ввода-вывода (например, при обращении к файлу по сети), попробуйте один из асинхронных подходов, которые описаны в статье [Библиотека параллельных задач и традиционное асинхронное программирование .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) и [в этой записи блога](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>См. также

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
