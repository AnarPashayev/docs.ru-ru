---
title: Справочник по C#. Предложение let
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: e9e10957e7ebe93a6dea9bbb6233ca7733f68e20
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633459"
---
# <a name="let-clause-c-reference"></a>Предложение let (справочник по C#)

В выражении запроса иногда требуется сохранить результат вложенного выражения, который будет использоваться в последующих предложениях. Это можно сделать с помощью ключевого слова `let`, которое создает новую переменную диапазона и инициализирует ее, используя результат предоставленного выражения. После инициализации с использованием этого значения такую переменную диапазона нельзя использовать для хранения других значений. Тем не менее если переменная диапазона хранит запрашиваемый тип, к ней можно выполнять запросы.

## <a name="example"></a>Пример

В следующем примере показываются два способа использования `let`:

1. Создание перечисляемого типа, к которому можно выполнять запросы.

2. Реализация запроса с однократным вызовом `ToLower` для переменной диапазона `word`. Если ключевое слово `let` не используется, потребуется выполнять вызов `ToLower` в каждом предикате предложения `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../../language-reference/index.md)
- [Ключевые слова запроса (LINQ)](query-keywords.md)
- [LINQ](../../linq/index.md)
- [Приступая к работе с LINQ в C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [Обработка исключений в выражениях запросов](../../linq/handle-exceptions-in-query-expressions.md)
