---
title: Подробный синтаксис
description: 'Изучите разницу между подробным и упрощенным синтаксисом в языке программирования F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4e1725b58c8cb67c074ba12fd4ca25ce0c000a1e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97595181"
---
# <a name="verbose-syntax"></a>Подробный синтаксис

Существует две формы синтаксиса для многих конструкций языка F #: *подробный синтаксис* и *упрощенный синтаксис*. Синтаксис verbose не так часто используется, но имеет преимущество менее чувствительно к отступу. Упрощенный синтаксис короче и использует отступы, чтобы сообщить начало и конец конструкций, а не дополнительные ключевые слова, такие как `begin` , `end` , `in` и т. д. Синтаксис по умолчанию — упрощенный синтаксис. В этом разделе описывается синтаксис конструкций F #, если упрощенный синтаксис не включен. Подробный синтаксис всегда включен, поэтому даже если включен упрощенный синтаксис, для некоторых конструкций по-прежнему можно использовать подробный синтаксис. Упрощенный синтаксис можно отключить с помощью `#light "off"` директивы.

## <a name="table-of-constructs"></a>Таблица конструкций

В следующей таблице показан упрощенный и подробный синтаксис для языковых конструкций F # в контекстах, где существует разница между двумя формами. В этой таблице угловые скобки ( &lt; &gt; ) заключают определяемые пользователем элементы синтаксиса. Более подробные сведения о синтаксисе, используемом в этих конструкциях, см. в документации по каждой языковой конструкции.

<table>
<tr>
<th>Конструкция языка</th>
<th>Упрощенный синтаксис</th>
<th>Подробный синтаксис</th>
</tr>
<tr>
<td>
составные выражения
</td>
<td>

```fsharp
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

вложенные `let` привязки

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
блок кода
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
begin
    <expression1>;
    <expression2>;
end
```

</td>
</tr>
<tr><td>
`for...do`
</td><td>

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td>запись
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>class
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td>structure</td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>размеченное объединение</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>interface</td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>выражение объекта</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>реализация интерфейсов</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>расширение типа</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>module</td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a>См. также

- [Справочник по языку F#](index.md)
- [Директивы компилятора](compiler-directives.md)
- [Рекомендации по форматированию кода](../style-guide/formatting.md)
