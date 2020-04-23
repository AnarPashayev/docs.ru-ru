---
title: Практическое руководство. Анализ строк с помощью метода String.Split (руководство по C#)
description: Метод String.Split возвращает массив строк, разбитых по набору разделителей. Это простой и удобный способ анализа строк.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: cf8307517213b54041b272843232eb595660b2e9
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389507"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>Анализ строк с помощью метода String.Split в C\#

Метод <xref:System.String.Split%2A?displayProperty=nameWithType> создает массив подстрок, разбивая входную строку по одному или нескольким разделителям. Часто это самый простой способ разделить строку по границам слов. Он также используется для разбиения строк по другим конкретным символам или строкам.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Следующий код разбивает обычную фразу на массив строк для каждого слова.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Каждый экземпляр знака разделения создает значение в возвращаемом массиве. Последовательные знаки разделения создают пустую строку в виде значения в возвращаемом массиве. В следующем примере показано создание пустой строки с использованием символа пробела в качестве разделителя.

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Такое поведение упрощает работу с такими форматами, как файл данных с разделителями-запятыми (CSV), которые представляют табличные данные. Идущие подряд запятые представляют пустой столбец.

Чтобы исключить из возвращаемого массива все пустые строки, можно передать необязательный параметр <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>. Для более сложной обработки возвращенной коллекции можно использовать [LINQ](../programming-guide/concepts/linq/index.md), чтобы управлять результирующей последовательностью.

<xref:System.String.Split%2A?displayProperty=nameWithType> может использовать несколько знаков разделения.
В приведенном ниже примере в качестве знаков разделения используются пробелы, запятые, точки, двоеточия и символы табуляции, которые передаются в метод <xref:System.String.Split%2A> в виде массива.
Цикл в конце кода отображает каждое из слов в возвращенном массиве.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Последовательные экземпляры любого разделителя создают пустую строку в выходном массиве:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

Метод <xref:System.String.Split%2A?displayProperty=nameWithType> может принимать массив строк (в этом случае в качестве разделителей при анализе целевой строки используются последовательности символов, а не отдельные символы).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Вы можете оценить эти примеры, просмотрев код в нашем [репозитории GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Или можете загрузить образцы [в ZIP-файле](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../programming-guide/index.md)
- [Строки](../programming-guide/strings/index.md)
- [Регулярные выражения .NET](../../standard/base-types/regular-expressions.md)
