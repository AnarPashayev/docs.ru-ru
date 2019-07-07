---
title: Практическое руководство. Выполнение кода очистки с использованием блока finally (Руководство по программированию на C#)
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 0ec661e5fb0e13eaf8c3c8e4a7b274ab58853f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978089"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Практическое руководство. Выполнение кода очистки с использованием блока finally (Руководство по программированию на C#)
Оператор `finally` позволяет гарантировать, что необходимая очистка объектов, как правило, объектов, занимающих внешние ресурсы, возникает немедленно, даже при создании исключения. Примером подобной очистки является вызов <xref:System.IO.Stream.Close%2A> для <xref:System.IO.FileStream> сразу после использования вместо ожидания сборки мусора, выполняемой для объекта средой CLR, следующим образом:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Пример  
 Чтобы преобразовать предыдущий код в оператор `try-catch-finally`, код очистки отделяется от рабочего кода следующим образом:  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Так как исключение может возникнуть в любой момент в блоке `try` до вызова `OpenWrite()`, или может произойти сбой самого вызова `OpenWrite()`, мы не можем гарантировать, что файл будет открыт при попытке закрыть его. Блок `finally` добавляет проверку того, что объект <xref:System.IO.FileStream> имеет отличное от `null` значение, прежде чем будет вызван метод <xref:System.IO.Stream.Close%2A>. Без проверки `null` блок `finally` может создавать собственное исключение <xref:System.NullReferenceException>, однако создания исключений в блоках `finally` следует по возможности избегать.  
  
 Подключение к базе данных — еще один подходящий кандидат для заключения в блок `finally`. Так как количество разрешенных подключений к серверу базы данных иногда ограничено, закрывать подключения к базе данных рекомендуется как можно быстрее. Если перед закрытием подключения возникает исключение, это еще один случай, когда использование блока `finally` предпочтительнее, чем ожидание сборки мусора.  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Исключения и обработка исключений](../../../csharp/programming-guide/exceptions/index.md)
- [Обработка исключений](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [Оператор using](../../../csharp/language-reference/keywords/using-statement.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
