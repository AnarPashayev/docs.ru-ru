---
title: Справочник по C#. Предложение where (ограничение универсального типа)
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: a71412a01045a445811898939624fd7cd7ab1cf1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633123"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (ограничение универсального типа) (справочник по C#)

Предложение `where` в универсальном определении задает ограничения на типы, которые используются в качестве аргументов для параметров типа в универсальном типе, методе, делегате или локальной функции. Ограничения могут задавать интерфейсы, базовые классы или требовать, чтобы универсальный тип был ссылочным типом, типом значения или неуправляемым типом. Они объявляют характеристики, которыми должен обладать аргумент типа.

Например, можно объявить универсальный класс `MyGenericClass` так, чтобы параметр типа `T` реализовывал интерфейс <xref:System.IComparable%601>:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Дополнительные сведения о предложении where в выражении запроса см. в разделе [Предложение where](where-clause.md).

Предложение `where` также может включать ограничение базового класса. Ограничение базового класса указывает, что тип, который должен использоваться как аргумент типа для этого универсального типа, имеет заданный класс в качестве базового класса (или является этим базовым классом), который должен использоваться как аргумент типа для этого универсального типа. Если ограничение базового класса используется, оно должно быть указано перед любыми другими ограничениями данного параметра типа. Некоторые типы не могут использоваться как ограничение базового класса: <xref:System.Object>, <xref:System.Array> и <xref:System.ValueType>. До C# 7.3 <xref:System.Enum>, <xref:System.Delegate> и <xref:System.MulticastDelegate> также не могли использоваться в качестве ограничений базового класса. Ниже приведен пример типов, которые теперь можно указать как базовый класс:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Предложение `where` может указывать, что тип является `class` или `struct`. Ограничение `struct` избавляет от необходимости указывать ограничение базового класса `System.ValueType`. Тип `System.ValueType` не может использоваться как ограничение базового класса. Ограничения `class` и `struct` показаны в следующем примере:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Предложение `where` также может включать ограничение `unmanaged`. Ограничение `unmanaged` позволяет использовать в качестве параметра типа только типы, называемые **неуправляемыми типами**. **Неуправляемый тип** — это тип, который не является ссылочным и не содержит поля ссылочного типа на любом уровне вложения. Ограничение `unmanaged` упрощает написание кода взаимодействия низкого уровня на языке C#. Это ограничение включает подпрограммы с возможностью повторного использования для всех неуправляемых типов. Ограничение `unmanaged` нельзя использовать с ограничением `class` или `struct`. Ограничение `unmanaged` требует тип `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Предложение `where` также может включать ограничение конструктора, `new()`. Это ограничение позволяет создать экземпляр параметра типа с помощью оператора `new`. [Ограничение new()](new-constraint.md) сообщает компилятору о том, что все предоставленные аргументы типа должны иметь доступный конструктор без параметров (или конструктор по умолчанию). Например:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Ограничение `new()` отображается в предложении `where` последним. Ограничение `new()` не может использоваться с ограничениями `struct` или `unmanaged`. Все типы, удовлетворяющие этим ограничениям, должны иметь доступ к конструктору без параметров, поэтому ограничение `new()` будет избыточным.

Если параметров типа несколько, для каждого из них необходимо использовать по одному предложению `where`, например:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Кроме того, ограничения можно присоединять к параметрам типа универсальных методов следующим образом:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Обратите внимание на то, что ограничения параметров типа для делегатов имеют такой же синтаксис, как и методы:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Дополнительные сведения об универсальных делегатах см. в разделе [Универсальные делегаты](../../../csharp/programming-guide/generics/generic-delegates.md).

Дополнительные сведения о синтаксисе и применении ограничений см. в разделе [Ограничения параметров типа](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>Спецификация языка C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Введение в универсальные шаблоны](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Ограничение new](../../../csharp/language-reference/keywords/new-constraint.md)
- [Ограничения параметров типа](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
