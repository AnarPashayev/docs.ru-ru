---
title: Руководство по программированию на C#. Пространства имен
description: Сведения о работе с пространствами имен при программировании на C#. В этой статье приводятся общие сведения о свойствах пространств имен, а также ссылки на дополнительные ресурсы.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440345"
---
# <a name="namespaces-c-programming-guide"></a>Пространства имен (Руководство по программированию в C#)

Пространства имен часто используются в программировании на C# двумя способами. Первый способ — .NET использует пространства имен для упорядочения множества ее классов следующим образом:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System> является пространством имен, а <xref:System.Console> — это класс в нем. Можно использовать ключевое слово `using`, и тогда полное имя не потребуется. См. следующий пример:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

См. дополнительные сведения о [директиве using](../../language-reference/keywords/using-directive.md).

Второй способ — объявление собственных пространств имен поможет вам контролировать область имен классов и методов в более крупных проектах. Используйте ключевое слово [namespace](../../language-reference/keywords/namespace.md), чтобы объявить пространство имен, как показано в следующем примере:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

Имя пространства имен должно быть допустимым [именем идентификатора](../inside-a-program/identifier-names.md) C#.

## <a name="namespaces-overview"></a>Обзор пространств имен

Пространства имен имеют следующие свойства:

- Они помогают упорядочивать проекты с большим объемом кода.
- Они разделяются оператором `.`.
- Директива `using` позволяет не указывать название пространства имен для каждого класса.
- Пространство имен `global` является корневым: `global::System` всегда будет ссылаться на пространство имен <xref:System> в .NET.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в статье [Пространства имен](~/_csharplang/spec/namespaces.md) в разделе [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Использование пространств имен](using-namespaces.md)
- [Практическое руководство. Использование пространства имен My](how-to-use-the-my-namespace.md)
- [Имена идентификаторов](../inside-a-program/identifier-names.md)
- [Директива using](../../language-reference/keywords/using-directive.md)
- [:: Оператор](../../language-reference/operators/namespace-alias-qualifier.md)
