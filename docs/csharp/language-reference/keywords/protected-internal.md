---
title: protected internal. Справочник по C#
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 2a06165714095a65c23826543c309a82c43c2f9a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633313"
---
# <a name="protected-internal-c-reference"></a>protected internal (справочник по C#)

Комбинация ключевых слов `protected internal` является модификатором доступа к члену. Доступ к членам с модификатором доступа protected internal может осуществляться из текущей сборки или типов, которые являются производными от содержащего класса. Сравнение модификатора `protected internal` с другими модификаторами доступа см. в разделе [Уровни доступности](accessibility-levels.md).

## <a name="example"></a>Пример

Член базового класса с модификатором доступа protected internal доступен из любого типа в пределах содержащей сборки. Он также доступен в производном классе, расположенном в другой сборке, только в том случае, если доступ осуществляется через переменную типа производного класса. Для примера рассмотрим следующий сегмент кода:

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

Этот пример содержит два файла, `Assembly1.cs` и `Assembly2.cs`.
Первый файл содержит открытый базовый класс, `BaseClass`, и еще один класс, `TestAccess`. `BaseClass` владеет членом protected internal, `myValue`, доступ к которому осуществляется типом `TestAccess`.
Во втором файле попытка получить доступ к `myValue` через экземпляр `BaseClass` приведет к ошибке во время доступа к этому члену через экземпляр производного класса. `DerivedClass` гарантирует успешное выполнение.

Элементы структуры не могут иметь модификатор `protected internal`, поскольку структура не может наследоваться.

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Модификаторы доступа](access-modifiers.md)
- [Уровни доступности](accessibility-levels.md)
- [Модификаторы](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Вопросы безопасности, связанные с использованием ключевых слов internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
