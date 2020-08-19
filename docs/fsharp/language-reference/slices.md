---
title: Срезы
description: 'Узнайте, как использовать срезы для существующих типов данных F # и как определять собственные срезы для других типов данных.'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559015"
---
# <a name="slices"></a>Срезы

В F # срез — это подмножество любого типа данных, имеющего `GetSlice` метод в его определении или в [расширении типа](type-extensions.md)в области. Чаще всего он используется с массивами и списками F #. В этой статье объясняется, как создавать срезы из существующих типов F # и как определять собственные срезы.

Срезы похожи на [индексаторы](./members/indexed-properties.md), но вместо получения одного значения из базовой структуры данных они получают несколько.

В настоящее время F # поддерживает встроенную поддержку для срезов строк, списков, массивов и двумерных массивов.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Базовый срез с списками и массивами F #

Наиболее распространенными типами данных, которые являются срезами, являются списки и массивы F #. В следующем примере показано, как это сделать с помощью списков.

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

Массивы срезов так же, как и списки срезов:

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a>Многомерные массивы с срезами

F # поддерживает многомерные массивы в основной библиотеке F #. Как и в случае с одномерным массивами, можно также использовать срезы многомерных массивов. Однако введение дополнительных измерений требует немного другого синтаксиса, чтобы можно было создавать срезы конкретных строк и столбцов.

В следующих примерах показано, как выполнить срез 2D-массива:

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

Основная библиотека F # в настоящее время не определена `GetSlice` для трехмерных массивов. Если вы хотите разделить трехмерные массивы или другие массивы большего размера, определите `GetSlice` элемент самостоятельно.

## <a name="defining-slices-for-other-data-structures"></a>Определение срезов для других структур данных

Основная библиотека F # определяет срезы для ограниченного набора типов. Если вы хотите определить срезы для большего числа типов данных, это можно сделать либо в самом определении типа, либо в расширении типа.

Например, ниже показано, как можно определить срезы для класса, <xref:System.ArraySegment%601> чтобы обеспечить удобную обработку данных:

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

Еще один пример использования <xref:System.Span%601> <xref:System.ReadOnlySpan%601> типов и:

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a>Встроенные срезы F # являются конечными включительно

Все внутренние срезы в F # являются конечными включительно. то есть верхняя граница включается в срез. Для данного среза с начальным индексом `x` и конечным индексом `y` результирующий срез будет включать значение *ИС* .

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a>См. также раздел

- [Индексированные свойства](./members/indexed-properties.md)
