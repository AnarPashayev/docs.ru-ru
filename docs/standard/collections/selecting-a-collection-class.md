---
title: Выбор класса коллекции
description: Сведения о том, как выбрать класс коллекции в .NET. Неправильный тип может ограничить возможности использования коллекции.
ms.date: 03/18/2019
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
ms.openlocfilehash: 7af08949df999ab80fce1308927d87a8935e3b5d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818730"
---
# <a name="selecting-a-collection-class"></a>Выбор класса коллекции

Внимательно относитесь к выбору класса коллекции. Неправильный тип может ограничить возможности использования коллекции.

> [!IMPORTANT]
> Не используйте такие типы в пространстве имен <xref:System.Collections>. Рекомендуется использовать универсальные и параллельные версии коллекций из-за более высокой безопасности типов и других усовершенствований.

Ответьте на следующие вопросы.

- Нужен ли вам последовательный список, элемент которого обычно удаляется сразу после извлечения его значения?

  - Если да, то рассмотрите возможность использования класса <xref:System.Collections.Queue> или универсального класса <xref:System.Collections.Generic.Queue%601>, если требуется обработка по принципу "первым поступил — первым обслужен" (FIFO). Рассмотрите возможность использования класса <xref:System.Collections.Stack> или универсального класса <xref:System.Collections.Generic.Stack%601>, если требуется обработка по принципу "последним поступил — первым обслужен" (LIFO). Для безопасного доступа из нескольких потоков используйте параллельные версии классов <xref:System.Collections.Concurrent.ConcurrentQueue%601> и <xref:System.Collections.Concurrent.ConcurrentStack%601>. Для неизменности рассмотрите неизменяемые версии, <xref:System.Collections.Immutable.ImmutableQueue%601> и <xref:System.Collections.Immutable.ImmutableStack%601>.

  - Если нет, то следует использовать другие коллекции.

- Нужен ли доступ к элементам в определенном порядке (FIFO, LIFO) или в произвольным порядке?

  - Класс <xref:System.Collections.Queue>, а также универсальные классы <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> и <xref:System.Collections.Immutable.ImmutableQueue%601> предоставляют доступ по методу FIFO. Дополнительные сведения см. в разделе [Преимущества использования потокобезопасных коллекций](thread-safe/when-to-use-a-thread-safe-collection.md).

  - Класс <xref:System.Collections.Stack>, а также универсальные классы <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601> и <xref:System.Collections.Immutable.ImmutableStack%601> предоставляют доступ по методу LIFO. Дополнительные сведения см. в разделе [Преимущества использования потокобезопасных коллекций](thread-safe/when-to-use-a-thread-safe-collection.md).

  - Универсальный класс <xref:System.Collections.Generic.LinkedList%601> предоставляет последовательный доступ от начала к концу списка или наоборот.

- Требуется ли доступ к каждому элементу по индексу?

  - Классы <xref:System.Collections.ArrayList> и <xref:System.Collections.Specialized.StringCollection> и универсальный класс <xref:System.Collections.Generic.List%601> предоставляют доступ к элементам по отсчитываемому от нуля индексу элемента. Для неизменности рассмотрите неизменяемые универсальные версии, <xref:System.Collections.Immutable.ImmutableArray%601> и <xref:System.Collections.Immutable.ImmutableList%601>.

  - Классы <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary> и <xref:System.Collections.Specialized.StringDictionary> и универсальные классы <xref:System.Collections.Generic.Dictionary%602> и <xref:System.Collections.Generic.SortedDictionary%602> предоставляют доступ к элементам по ключу элемента. Кроме того, существуют неизменяемые версии нескольких соответствующих типов: <xref:System.Collections.Immutable.ImmutableHashSet%601>, <xref:System.Collections.Immutable.ImmutableDictionary%602>, <xref:System.Collections.Immutable.ImmutableSortedSet%601> и <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>.

  - Классы <xref:System.Collections.Specialized.NameObjectCollectionBase> и <xref:System.Collections.Specialized.NameValueCollection> и универсальные классы <xref:System.Collections.ObjectModel.KeyedCollection%602> и <xref:System.Collections.Generic.SortedList%602> предоставляют доступ к элементам по отсчитываемому от нуля индексу или по ключу элемента.

- Будет ли каждый элемент содержать только одно значение, сочетание из одного ключа и одного значения или сочетание из одного ключа и нескольких значений?

  - Одно значение: используйте любую коллекцию, основанную на интерфейсе <xref:System.Collections.IList> или на универсальном интерфейсе <xref:System.Collections.Generic.IList%601>. Для неизменяемого параметра рассмотрим универсальный интерфейс <xref:System.Collections.Immutable.IImmutableList%601>.

  - Один ключ и одно значение: используйте любую коллекцию, основанную на интерфейсе <xref:System.Collections.IDictionary> или на универсальном интерфейсе <xref:System.Collections.Generic.IDictionary%602>. Для неизменяемого параметра рассмотрим универсальный интерфейс <xref:System.Collections.Immutable.IImmutableSet%601> или <xref:System.Collections.Immutable.IImmutableDictionary%602>.

  - Одно значение с внедренным ключом: используйте универсальный класс <xref:System.Collections.ObjectModel.KeyedCollection%602>.

  - Один ключ и несколько значений: используйте класс <xref:System.Collections.Specialized.NameValueCollection>.

- Требуется ли сортировать элементы в порядке, отличном от порядка их поступления?

  - Класс <xref:System.Collections.Hashtable> сортирует элементы по хэш-коду.

  - В классе <xref:System.Collections.SortedList> и универсальных классах <xref:System.Collections.Generic.SortedList%602> и <xref:System.Collections.Generic.SortedDictionary%602> элементы сортируются по ключу. Порядок сортировки зависит от реализации интерфейса <xref:System.Collections.IComparer> для класса <xref:System.Collections.SortedList> и от реализации универсального интерфейса <xref:System.Collections.Generic.IComparer%601> для универсальных классов <xref:System.Collections.Generic.SortedList%602> и <xref:System.Collections.Generic.SortedDictionary%602>. Из двух универсальных типов <xref:System.Collections.Generic.SortedDictionary%602> обеспечивает более высокую производительность, чем <xref:System.Collections.Generic.SortedList%602>, но <xref:System.Collections.Generic.SortedList%602> потребляет меньше памяти.

  - Класс <xref:System.Collections.ArrayList> предоставляет метод <xref:System.Collections.ArrayList.Sort%2A>, который принимает реализацию <xref:System.Collections.IComparer> в качестве параметра. Его универсальный аналог, универсальный класс <xref:System.Collections.Generic.List%601>, предоставляет метод <xref:System.Collections.Generic.List%601.Sort%2A>, который принимает реализацию универсального интерфейса <xref:System.Collections.Generic.IComparer%601> в качестве параметра.

- Требуются ли быстрый поиск и получение данных?

  - <xref:System.Collections.Specialized.ListDictionary> быстрее, чем <xref:System.Collections.Hashtable>, для небольших коллекций (10 элементов или меньше). Универсальный класс <xref:System.Collections.Generic.Dictionary%602> обеспечивает более быстрый поиск, чем универсальный класс <xref:System.Collections.Generic.SortedDictionary%602>. Многопоточной реализацией является <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> обеспечивает быструю многопоточную вставку для неупорядоченных данных. Дополнительные сведения об обоих многопоточных типах см. в разделе [Преимущества использования потокобезопасных коллекций](thread-safe/when-to-use-a-thread-safe-collection.md).

- Требуются ли вам коллекции, принимающие только строки?

  - Классы <xref:System.Collections.Specialized.StringCollection> (на основе <xref:System.Collections.IList>) и <xref:System.Collections.Specialized.StringDictionary> (на основе <xref:System.Collections.IDictionary>) находятся в пространстве имен <xref:System.Collections.Specialized>.

  - Кроме того, можно использовать любой из универсальных классов коллекций в пространстве имен <xref:System.Collections.Generic> как строго типизированную строковую коллекцию, указав класс <xref:System.String> в качестве аргумента универсального типа. Например, можно объявить переменную с типом [List\<String>](xref:System.Collections.Generic.List%601) или [Dictionary<String,String>](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects и PLINQ

Язык LINQ to Objects позволяет использовать запросы LINQ для доступа к объектам в памяти при условии, что тип объекта реализует интерфейс <xref:System.Collections.IEnumerable> или <xref:System.Collections.Generic.IEnumerable%601>. Запросы LINQ обеспечивают общий шаблон для доступа к данным, обычно являются более четкими и удобочитаемыми, чем стандартные циклы `foreach`, а также предоставляют возможности фильтрации, сортировки и группировки. Дополнительные сведения см. в разделах [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) и [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

Язык PLINQ предоставляет параллельную реализацию языка LINQ to Objects, которая может обеспечить более быстрое выполнение запросов во многих сценариях за счет более эффективного использования многоядерных компьютеров. Дополнительные сведения см. в разделе [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>См. также

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Потокобезопасные коллекции](thread-safe/index.md)
