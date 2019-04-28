---
title: Определение анонимного типа (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 832d56f5c51aea87185f36ec306c3fec036a40e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780852"
---
# <a name="anonymous-type-definition-visual-basic"></a>Определение анонимного типа (Visual Basic)

В ответ на объявление экземпляра анонимного типа компилятор создает определение нового класса, который содержит указанные свойства для типа.

## <a name="compiler-generated-code"></a>Созданный компилятором код

Для следующее определение `product`, компилятор создает определение нового класса, который содержит свойства `Name`, `Price`, и `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Определение класса содержит определения свойств следующего вида. Обратите внимание, что не `Set` метод для ключевых свойств. Значения свойств ключа доступны только для чтения.

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

Кроме того определения анонимного типа содержат конструктор по умолчанию. Конструкторы, требующие параметры не допускаются.

Если в объявлении анонимного типа содержит по крайней мере одно ключевое свойство, определение переопределяет три члена, унаследованные от <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, и <xref:System.Object.ToString%2A>. При объявлении ключевые свойства, а только <xref:System.Object.ToString%2A> переопределяется. Переопределение предоставляет следующие функциональные возможности:

- `Equals` Возвращает `True` Если два экземпляра анонимного типа являются одним экземпляром или при соблюдении следующих условий:

  - Они имеют такое же количество свойств.

  - Свойства объявляются в том же порядке, с теми же именами и те же возвращаемые типы. Сравнение имен регистр не учитывается.

  - По крайней мере одно из свойств является свойством ключа и `Key` те же свойства применяется ключевое слово.

  - Сравнение каждой соответствующей пары ключевых свойств возвращает `True`.

    Например, в следующих примерах `Equals` возвращает `True` только для `employee01` и `employee08`. Комментарий перед каждой строке указывается причина, почему нового экземпляра не соответствует `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` предоставляет соответствующим образом уникальный алгоритм GetHashCode. Алгоритм использует только ключевые свойства для вычисления хэш-код.

- `ToString` Возвращает строку объединены значения свойств, как показано в следующем примере. Включены ключевые и неключевые свойства.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Явно именованные свойства анонимного типа не должны конфликтовать с эти созданные методы. То есть нельзя использовать `.Equals`, `.GetHashCode`, или `.ToString` для имени свойства.

Определения анонимного типа, включающих по крайней мере одно ключевое свойство, также реализуют <xref:System.IEquatable%601?displayProperty=nameWithType> интерфейс, где `T` тип анонимного типа.

> [!NOTE]
> Объявления анонимного типа создать анонимный тип аналогично только в том случае, если они встречаются в той же сборке, их свойства имеют те же имена и те же возвращаемые типы, свойства объявляются в том же порядке и те же свойства, помечаются как ключевые свойства.

## <a name="see-also"></a>См. также

- [Анонимные типы](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
