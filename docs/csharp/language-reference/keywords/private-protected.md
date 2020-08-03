---
title: Справочник по C#. Комбинация ключевых слов private protected
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301805"
---
# <a name="private-protected-c-reference"></a>private protected (справочник по C#)

Комбинация ключевых слов `private protected` является модификатором доступа к члену. К члену private protected имеют доступ типы, производные от содержащего класса, но только в пределах содержащей сборки. Сравнение модификатора `private protected` с другими модификаторами доступа см. в разделе [Уровни доступности](accessibility-levels.md).

> [!NOTE]
> Модификатор доступа `private protected` допустим в C# 7.2 и более поздних версий.

## <a name="example"></a>Пример

Член базового класса private protected доступен из производных типов в содержащей сборке только в том случае, если статический тип переменной является типом производного класса. Для примера рассмотрим следующий сегмент кода:

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

Этот пример содержит два файла, `Assembly1.cs` и `Assembly2.cs`.
Первый файл содержит открытый базовый класс, `BaseClass`, и производный от него тип, `DerivedClass1`. `BaseClass` владеет членом private protected, `myValue`, к которому `DerivedClass1` пытается получить доступ двумя способами. Первая попытка доступа к `myValue` через экземпляр `BaseClass` приведет к ошибке. Однако попытка использовать его в качестве наследуемого члена в `DerivedClass1` завершится успешно.

Во втором файле попытка получить доступ к `myValue` в качестве наследуемого члена `DerivedClass2` приведет к ошибке, поскольку он доступен только для производных типов в Assembly1.

Если `Assembly1.cs` содержит <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> с именем `Assembly2`, производный класс `DerivedClass1` будет иметь доступ к членам `private protected`, объявленным в `BaseClass`. `InternalsVisibleTo` делает члены `private protected` видимыми для производных классов в других сборках.

Элементы структуры не могут иметь модификатор `private protected`, поскольку структура не может наследоваться.

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Модификаторы доступа](access-modifiers.md)
- [Уровни доступности](accessibility-levels.md)
- [Модификаторы](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Вопросы безопасности, связанные с использованием ключевых слов internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
