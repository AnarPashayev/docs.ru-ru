---
title: Сравнение и сортировка в коллекциях
description: Вы можете осуществлять сравнения и сортировки с помощью классов System.Collections в .NET, которые помогают найти элемент для удаления или возвратить значение пары "ключ — значение".
ms.date: 04/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: aa001e8469947a532d77059bd52024c6b47b508e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769201"
---
# <a name="comparisons-and-sorts-within-collections"></a>Сравнение и сортировка в коллекциях

Классы <xref:System.Collections> выполняют сравнения почти во всех процессах управления коллекциями — будь то поиск элемента для удаления или возвращение значения пары "ключ-значение".

В коллекциях обычно используется компаратор проверки на равенство и (или) компаратор упорядочения. Для сравнения используются две конструкции.

<a name="BKMK_Checkingforequality"></a>
## <a name="check-for-equality"></a>Проверка на равенство

Такие методы, как `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>и `Remove` , используют компаратор проверки на равенство для элементов коллекции. Если коллекция является универсальной, элементы проверяются на равенство согласно следующим правилам:

- Если тип T реализует универсальный интерфейс <xref:System.IEquatable%601> , компаратором проверки на равенство является метод <xref:System.IEquatable%601.Equals%2A> этого интерфейса.

- Если тип T не реализует <xref:System.IEquatable%601>, используется <xref:System.Object.Equals%2A?displayProperty=nameWithType> .

Кроме того, некоторые перегрузки конструктора для коллекций словаря принимают реализацию <xref:System.Collections.Generic.IEqualityComparer%601>, которая используется для сравнения ключей на равенство. Пример см. в конструкторе <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> .

<a name="BKMK_Determiningsortorder"></a>
## <a name="determine-sort-order"></a>Определение порядка сортировки

Такие методы, как `BinarySearch` и `Sort` , используют компаратор упорядочения для элементов коллекции. Сравнение может проводиться между элементами коллекции или между элементом и заданным значением. В процессе сравнения объектов существует понятие `default comparer` и `explicit comparer`.

Для реализации интерфейса **IComparable** компаратор по умолчанию использует по крайней мере один из сравниваемых объектов. Интерфейс **IComparable** рекомендуется реализовать во всех классах, используемых в качестве значений в коллекциях списков или в качестве ключей в коллекциях словарей. В универсальной коллекции сравнение на равенство определяется в соответствии со следующими правилами.

- Если тип T реализует универсальный интерфейс <xref:System.IComparable%601?displayProperty=nameWithType> , компаратором по умолчанию является метод <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> этого интерфейса.

- Если тип T реализует неуниверсальный интерфейс <xref:System.IComparable?displayProperty=nameWithType> , компаратором по умолчанию является метод <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> этого интерфейса.

- Если тип T не реализует интерфейс, это значит, что функция сравнения по умолчанию отсутствует, и она или делегат сравнения должны быть предоставлены явно.

Для осуществления явных сравнений некоторые методы принимают реализацию **IComparer** в качестве параметра. Например, метод <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> принимает реализацию <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> .

Текущее значение языка и региональных параметров системы может влиять на сравнения и сортировки в рамках коллекции. По умолчанию сравнения и сортировки в классах **Collections** зависят от языка и региональных параметров. Чтобы игнорировать параметр языка и региональные параметры и получить согласованные результаты сравнения и сортировки, используйте <xref:System.Globalization.CultureInfo.InvariantCulture%2A> с перегрузками элементов, принимающими <xref:System.Globalization.CultureInfo>. Дополнительные сведения см. в разделах [Выполнение в коллекциях строковых операций, не зависящих от языка и региональных параметров](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) и [Выполнение в массивах строковых операций, не зависящих от языка и региональных параметров](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).

<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Пример сортировки и проверки на равенство

В следующем примере демонстрируется реализация <xref:System.IEquatable%601> и <xref:System.IComparable%601> в простом бизнес-объекте. Кроме того, когда объект сохраняется в списке и сортируется, вы увидите, что вызов метода <xref:System.Collections.Generic.List%601.Sort> приведет к использованию компаратора по умолчанию для типа `Part` , а метод <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> будет реализован с помощью анонимного метода.

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a>См. также

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
