---
title: Руководство по программированию на C#. Исключения, создаваемые компилятором
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 28e6ba0c20948aa769a1517c664db80b5beb6b68
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398033"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Исключения, создаваемые компилятором (Руководство по программированию в C#)
Некоторые исключения создаются средой .NET Framework CLR (CLR) автоматически, когда происходит сбой основной операции. В следующей таблице перечислены эти исключения и условия возникновения ошибок.  
  
|Исключение|ОПИСАНИЕ|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Базовый класс для исключений, которые возникают при выполнении арифметических операций, таких как <xref:System.DivideByZeroException> и <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Возникает, если массив не может сохранить данный элемент, поскольку фактический тип элемента несовместим с фактическим типом массива.|  
|<xref:System.DivideByZeroException>|Возникает при попытке деления целого значения на ноль.|  
|<xref:System.IndexOutOfRangeException>|Возникает при попытке индексирования массива, если индекс меньше нуля или выходит за границы массива.|  
|<xref:System.InvalidCastException>|Возникает, если явное преобразование из базового типа в интерфейс или в производный тип завершается ошибкой во время выполнения.|  
|<xref:System.NullReferenceException>|Возникает при попытке сослаться на объект, имеющий значение [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Возникает, если попытка распределения памяти с помощью оператора [new](../../../csharp/language-reference/operators/new-operator.md) завершается ошибкой. Это означает, что ресурсы памяти, доступные для среды CLR, исчерпаны.|  
|<xref:System.OverflowException>|Возникает при переполнении арифметической операции в контексте `checked`.|  
|<xref:System.StackOverflowException>|Возникает, когда чрезмерное количество ожидающих вызовов метода истощает стек выполнения; обычно это указывает на крайне глубокую или бесконечную рекурсию.|  
|<xref:System.TypeInitializationException>|Возникает, когда статический конструктор создает исключение, а совместимого предложения `catch` для его захвата нет.|  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Исключения и обработка исключений](../../../csharp/programming-guide/exceptions/index.md)
- [Обработка исключений](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
