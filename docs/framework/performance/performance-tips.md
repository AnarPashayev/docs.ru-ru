---
title: Советы по производительности .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 14ed06bbd09d7551707628060b460584816e4711
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046282"
---
# <a name="net-performance-tips"></a>Советы по производительности .NET
Под *производительностью* обычно понимается скорость выполнения программы. В некоторых случаях ее можно увеличить, следуя определенным основным правилам написания исходного кода. В некоторых программах важно тщательно проверить код и с помощью профилировщиков убедиться, что он выполняется максимально быстро. В других случаях такая оптимизация не требуется, поскольку код выполняется достаточно быстро в своем первоначальном виде. В этой статье описываются основные причины снижения производительности и приводятся рекомендации по ее повышению, а также ссылки на разделы с дополнительной информацией. Дополнительные сведения о планировании и измерении производительности см. в разделе [Производительность](index.md)  
  
## <a name="boxing-and-unboxing"></a>Упаковка–преобразование и распаковка–преобразование  
 Не рекомендуется использовать типы значений в тех случаях, где они многократно упаковываются, например в классах неуниверсальных коллекций, таких как <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Чтобы избежать упаковки типов значений, используйте универсальные коллекции, такие как <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Операции упаковки и распаковки являются весьма затратными процессами с точки зрения вычислений. При упаковке типа значений создается полностью новый объект. Это может занимать почти в 20 раз больше времени, чем простое присваивание ссылки. Процесс приведения при распаковке также занимает в 4 раза больше времени, чем присваивание. Дополнительные сведения см. в разделе [Упаковка-преобразование и распаковка-преобразование](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Строки  
 При сцеплении большого числа строковых переменных, например в непрерывном цикле, используйте <xref:System.Text.StringBuilder?displayProperty=nameWithType> вместо [оператора + (C#)](../../csharp/language-reference/operators/addition-operator.md) или [операторов сцепления (Visual Basic)](../../visual-basic/language-reference/operators/concatenation-operators.md). Дополнительные сведения см. в разделе [Практическое руководство. Объедините несколько строк](../../csharp/how-to/concatenate-multiple-strings.md) и [операторов объединения в Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Деструкторы  
 Пустые деструкторы использовать не следует. Если класс содержит деструктор, то в очереди метода Finalize создается запись. При вызове деструктора вызывается сборщик мусора, выполняющий обработку очереди. Если деструктор пустой, это приводит только к ненужному снижению производительности. Дополнительные сведения см. в разделе [деструкторы](../../csharp/programming-guide/classes-and-structs/destructors.md) и [время существования объекта: Как создаются и уничтожаются](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)объекты.  
  
## <a name="other-resources"></a>Другие ресурсы  
  
- [Написание более быстрого управляемого кода: Сведения о стоимости](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
- [Создание высокопроизводительных управляемых приложений: Учебник](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
- [Общие сведения о сборке мусора и советы по повышению производительности](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
- [Советы и рекомендации по повышению производительности в приложениях .NET](https://go.microsoft.com/fwlink/?LinkId=99297)  

- [Советы по повышению производительности от Рико Мариани](https://go.microsoft.com/fwlink/?LinkId=115679)  

- [Блог Вэнс Моррисон](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>См. также

- [Производительность](index.md)
- [Руководство по программированию на Visual Basic](../../visual-basic/programming-guide/index.md)
- [Руководство по программированию на C#](../../csharp/programming-guide/index.md)
