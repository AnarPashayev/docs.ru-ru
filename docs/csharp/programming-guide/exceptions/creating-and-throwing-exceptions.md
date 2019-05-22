---
title: Руководство по программированию C#. Создание и генерация исключений
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: e569742943e121faeae340512544956b674da083
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595359"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Создание и генерация исключений (Руководство по программированию C#)
Исключения позволяют обозначить, что во время выполнения программы произошла ошибка. Объекты исключений, описывающие ошибку, создаются и затем *вызываются* с помощью ключевого слова [throw](../../../csharp/language-reference/keywords/throw.md). Далее среда выполнения ищет наиболее совместимый обработчик исключений.  
  
 Программисты должны вызывать исключения при выполнении одного или нескольких из перечисленных ниже условий.  
  
- Метод не способен выполнить свои функции.  
  
     Например, если значение параметра метода является недопустимым:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- На основе состояния объекта выполнен неправильный вызов объекта.  
  
     В качестве примера можно привести попытку записи в файл, доступный только для чтения. В случаях, когда состояние объекта не допускает выполнения операции, вызывается экземпляр <xref:System.InvalidOperationException> или объекта на основе наследования этого класса. Ниже приведен пример метода, который вызывает объект <xref:System.InvalidOperationException>:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Когда аргумент метода вызывает исключение.  
  
     В этом случае должно быть перехвачено исходное исключение и создан экземпляр <xref:System.ArgumentException>. Исходное исключение должно передаваться конструктору <xref:System.ArgumentException> в качестве параметра <xref:System.Exception.InnerException%2A>:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Исключения содержат свойство с именем <xref:System.Exception.StackTrace%2A>. Строка содержит имена методов в текущем стеке вызовов вместе с именем файла и номером строки, в которой было вызвано исключение для каждого метода. Объект <xref:System.Exception.StackTrace%2A> создается автоматически средой CLR из точки оператора `throw`, так что исключения должны вызываться из той точки, где должна начинаться трассировка стека.  
  
 Все исключения содержат свойство с именем <xref:System.Exception.Message%2A>. Эта строка должна содержать сообщение с объяснением причины исключения. Обратите внимание, что важные с точки зрения безопасности сведения не следует помещать в текст сообщения. Помимо <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> содержит свойство с именем <xref:System.ArgumentException.ParamName%2A>, которому должно присваиваться имя аргумента, ставшего причиной возникновения исключения. Для метода задания свойства <xref:System.ArgumentException.ParamName%2A> должно получать значение `value`.  
  
 Открытые и защищенные методы должны вызывать исключения каждый раз, когда не удается выполнить назначенные им функции. Вызываемый класс исключения должен быть самым конкретным доступным исключением, удовлетворяющим условиям ошибки. Эти исключения должны документироваться в составе функций класса, а производные классы или обновления исходного класса должны сохранять то же поведение для обеспечения обратной совместимости.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Чего следует избегать при вызове исключений  
 Ниже приводятся рекомендации по тому, чего следует избегать при вызове исключений.  
  
- Исключения не рекомендуется использовать для изменения потока программы в рамках обычного выполнения. Исключения следует использовать только для сообщения о состояниях ошибки и их обработки.  
  
- Исключения должны генерироваться, а не возвращаться в качестве возвращаемого значения или параметра.  
  
- Не следует вызывать <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType> или <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> из собственного исходного кода намеренно.  
  
- Не рекомендуется создавать исключения, которые могут вызываться в режиме отладки, а не в режиме выпуска. Чтобы определить ошибки времени выполнения на этапе разработки, используйте Debug Assert.  
  
## <a name="defining-exception-classes"></a>Определение классов исключений  
 Программы могут вызывать предопределенный класс исключений в пространстве имен <xref:System> (кроме указанных ранее случаев) или создавать собственные классы исключений путем наследования от <xref:System.Exception>. Производные классы должны определять по крайней мере четыре конструктора: один конструктор без параметров, один конструктор, задающий свойство сообщения, и еще один, задающий свойства <xref:System.Exception.Message%2A> и <xref:System.Exception.InnerException%2A>. Четвертый конструктор служит для сериализации исключения. Новые классы исключений должны быть сериализуемыми. Например:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Новые свойства следует добавлять к классу исключений только в том случае, если данные в них могут помочь в разрешении исключения. При добавлении новых свойств в производный класс исключений метод `ToString()` необходимо переопределить так, чтобы он возвращал добавленные сведения.  
  
## <a name="c-language-specification"></a>Спецификация языка C#  

Дополнительные сведения см. в разделах [Исключения](~/_csharplang/spec/exceptions.md) и [Оператор throw](~/_csharplang/spec/statements.md#the-throw-statement) в [Спецификации языка C#](../../language-reference/language-specification/index.md). Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Исключения и обработка исключений](../../../csharp/programming-guide/exceptions/index.md)
- [Иерархия исключений](../../../standard/exceptions/index.md)
- [Обработка исключений](../../../csharp/programming-guide/exceptions/exception-handling.md)
