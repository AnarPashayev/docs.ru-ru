---
title: Обработка значений NULL в выражениях запросов (LINQ в C#)
description: Узнайте, как обрабатывать значения NULL в выражениях запросов LINQ в C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 38a5c5e4a869cc44be78f70cbf0e50166baaab16
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353322"
---
# <a name="handle-null-values-in-query-expressions"></a>Обработка значений NULL в выражениях запросов

В этом примере показано, как обрабатывать возможные нулевые значения в исходных коллекциях. Коллекция объектов, например <xref:System.Collections.Generic.IEnumerable%601>, может содержать элементы со значением [NULL](../language-reference/keywords/null.md). Если исходная коллекция имеет значение NULL или содержит элемент со значением NULL, а запрос не обрабатывает такие значения, при выполнении этого запроса возникает исключение <xref:System.NullReferenceException>.

## <a name="example"></a>Пример

Чтобы избежать исключения в связи с пустой ссылкой, можно составить защитный код, как показано в следующем примере:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

В предыдущем примере предложение `where` отфильтровывает все пустые элементы в последовательности категорий. Этот метод не связан с проверкой на наличие пустых значений в предложении join. Условное выражение со значением NULL в этом примере работает, поскольку `Products.CategoryID` типа `int?` является сокращением от `Nullable<int>`.

## <a name="example"></a>Пример

Если в предложении join тип, допускающий значение NULL, имеет только один из ключей сравнения, остальные типы в выражении запроса можно привести к типу, допускающему значение NULL. В следующем примере предполагается, что `EmployeeID` — это столбец, содержащий значения типа `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Nullable%601>
- [LINQ](index.md)
- [Типы значений, допускающие значение NULL](../programming-guide/nullable-types/index.md)
