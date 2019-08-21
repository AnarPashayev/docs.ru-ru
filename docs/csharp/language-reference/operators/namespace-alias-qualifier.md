---
title: Оператор ::. Справочник по C#
ms.custom: seodec18
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971245"
---
# <a name="-operator-c-reference"></a>Оператор :: (справочник по C#)

Используйте квалификатор псевдонима пространства имен `::` для доступа к элементам пространства имен, обозначенного псевдонимом. Квалификатор `::` используется между двумя идентификаторами. Левый идентификатор может быть любым из следующих псевдонимов:

- Псевдоним пространства имен, созданный с помощью [директивы псевдонима using](../keywords/using-directive.md):
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Псевдоним extern](../keywords/extern-alias.md).
- Псевдоним `global`, который является псевдонимом глобального пространства имен. Глобальное пространство имен — это пространство имен, которое содержит пространства имен и типы, не объявленные в именованном пространстве имен. При использовании с квалификатором `::` псевдоним `global` всегда ссылается на глобальное пространство имен, даже если существует определяемый пользователем псевдоним пространства имен `global`.
  
  В следующем примере используется псевдоним `global` для доступа к пространству имен .NET <xref:System>, которое является элементом глобального пространства имен. Без псевдонима `global` доступ к определяемому пользователем пространству имен `System`, которое является элементом пространства имен `MyCompany.MyProduct`, будет осуществляться следующим образом:

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }
  
      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```
  
  > [!NOTE]
  > Ключевое слово `global` является псевдонимом глобального пространства имен, только если оно является левым идентификатором квалификатора `::`.

Можно также использовать [оператор доступа к элементам `.`](member-access-operators.md#member-access-operator-) для доступа к элементам пространства имен, обозначенного псевдонимом. Но оператор `.` также используется для доступа к элементам типа. Квалификатор `::` гарантирует, что его левый идентификатор всегда ссылается на псевдоним пространства имен, даже если существует тип или пространство имен с таким же именем.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в описании [квалификаторов псевдонимов пространства имен](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) в [спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы в C#](index.md)
- [Использование пространств имен](../../programming-guide/namespaces/using-namespaces.md)
