---
description: Модификатор static. Справочник по C#
title: Модификатор static. Справочник по C#
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654643"
---
# <a name="static-c-reference"></a>static (Справочник по C#)

На этой странице приводятся сведения о ключевом слове модификатора `static`. Ключевое слово `static` также является частью директивы [`using static`](using-static.md).

Модификатор `static` используется для объявления статического члена, принадлежащего собственно типу, а не конкретному объекту. Модификатор `static` можно использовать для объявления классов `static`. В классах, интерфейсах и структурах вы можете добавить модификатор `static` к полям, методам, свойствам, операторам, событиям и конструкторам. Модификатор `static` запрещено использовать с индексаторами или методами завершения. Дополнительные сведения см. в статье [Статические классы и члены статических классов](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Начиная с C# 8.0 можно добавить модификатор `static` в [локальную функцию](../../programming-guide/classes-and-structs/local-functions.md). Статическая локальная функция не может сохранять локальные переменные или состояние экземпляра.

Начиная с C# 9.0 можно добавить модификатор `static` в [лямбда-выражение](../operators/lambda-expressions.md) или [анонимный метод](../operators/delegate-operator.md). Статическое лямбда-выражение или анонимный метод не могут сохранять локальные переменные или состояние экземпляра.

## <a name="example---static-class"></a>Пример: статический класс

Следующий класс объявляется как `static` и содержит только методы `static`:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Объявление константы или типа неявно является членом `static`. На член `static` невозможно ссылаться через экземпляр, а можно только через имя типа. Например, рассмотрим следующий класс.

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Чтобы обратиться к члену `static` `x`, воспользуйтесь полным именем — `MyBaseC.MyStruct.x` (если только член не доступен из той же области действия).

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Так как экземпляр класса содержит отдельную копию всех полей экземпляра класса, каждому полю `static` соответствует только одна копия.

Невозможно использовать [`this`](this.md) для ссылки на методы `static` или методы доступа к свойствам.

Если к классу применяется ключевое слово `static`, все члены этого класса должны быть `static`.

Классы, интерфейсы и классы `static` могут иметь конструкторы `static`. Конструктор `static` вызывается на определенном этапе между запуском программы и созданием экземпляра класса.

> [!NOTE]
> Ключевое слово `static` имеет более ограниченное применение по сравнению с C++. Сведения о сравнении с ключевым словом С++ см. в статье [Классы хранения (C++)](/cpp/cpp/storage-classes-cpp#static).

В качестве демонстрации членов `static` рассмотрим класс, представляющий сотрудника компании. Предположим, что этот класс содержит метод для подсчета сотрудников и поле для хранения их числа. И метод, и поле не принадлежат никакому экземпляру сотрудника. Они принадлежат всему классу сотрудников. В связи с этим они должны объявляться как члены `static` класса.

## <a name="example---static-field-and-method"></a>Пример: статическое поле и метод

В этом примере выполняется чтение имени и идентификатора нового сотрудника, увеличение счетчика сотрудников на единицу, а также отображение сведений о новом сотруднике и новом числе сотрудников. Эта программа считывает текущее число сотрудников с клавиатуры.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Пример: статическая инициализация

В этом примере показано, как можно инициализировать поле `static`, используя другое поле `static`, которое еще не объявлено. Результаты будут неопределенными до тех пор, пока вы явно не присвоите значение полю `static`.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Модификаторы](index.md)
- [Директива using static](using-static.md)
- [Статические классы и члены статических классов](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
