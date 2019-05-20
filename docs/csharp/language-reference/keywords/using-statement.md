---
title: Справочник по C#. Оператор using
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: e1a1a960fa69be593ea01cab51be576b0055fd5e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632901"
---
# <a name="using-statement-c-reference"></a>Оператор using (справочник по C#)

Предоставляет удобный синтаксис, обеспечивающий правильное использование объектов <xref:System.IDisposable>.

## <a name="example"></a>Пример

В следующем примере показано использование оператора `using`.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a>Примечания

<xref:System.IO.File> и <xref:System.Drawing.Font> представляют собой примеры управляемых типов, которые обращаются к неуправляемым ресурсам (в данном случае это обработчики файлов и контексты устройств). Существуют и многие другие виды неуправляемых ресурсов и типов библиотек классов, которые их инкапсулируют. Все эти типы реализуют интерфейс <xref:System.IDisposable>.

Когда время существования объекта `IDisposable` ограничено одним методом, необходимо объявить его и создать его экземпляр в операторе `using`. Оператор `using` правильно вызывает метод <xref:System.IDisposable.Dispose%2A> для объектов, а также (если он используется, как показано выше) становится причиной выхода объекта из области действия, как только вызывается метод <xref:System.IDisposable.Dispose%2A>. В блоке `using` объект доступен только для чтения, и изменить или переназначить его нельзя.

Использование оператора `using` обеспечивает вызов метода <xref:System.IDisposable.Dispose%2A>, даже если в блоке `using` возникает исключение. Тот же результат можно получить, поместив объект в блок `try`, а затем вызвав метод <xref:System.IDisposable.Dispose%2A> в блоке `finally`; фактически компилятор переводит оператор `using` именно так. Во время компиляции представленный выше код разворачивается в следующий (обратите внимание на дополнительные фигурные скобки, создающие ограниченную область действия для объекта):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Дополнительные сведения об операторе `try`-`finally` см. в разделе [try-finally](try-finally.md).

В операторе `using` можно объявить сразу несколько экземпляров типа, как показано в следующем примере:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Вы можете создать экземпляр объекта ресурсов, а затем передать переменную в оператор `using`, однако делать этого не рекомендуется. В этом случае объект остается в области действия и после того, как блок `using` теряет контроль, хотя доступа к неуправляемым ресурсам у него, скорее всего, не будет. Иными словами, он уже не полностью инициализируется. При попытке использовать объект за пределами блока `using` может возникнуть исключение. По этой причине лучше создать экземпляр объекта в операторе `using` и ограничить область действия блоком `using`.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Дополнительные сведения об утилизации объектов `IDisposable` см. в разделе [Использование объектов, реализующих IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Оператор using](~/_csharplang/spec/statements.md#the-using-statement) в статье [Спецификации языка C#](../language-specification/index.md). Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Директива using](using-directive.md)
- [Сборка мусора](../../../standard/garbage-collection/index.md)
- [Использование объектов, реализующих IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Интерфейс IDisposable](xref:System.IDisposable)
