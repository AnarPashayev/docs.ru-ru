---
title: Универсальные интерфейсы
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET]
- equality comparisons [.NET]
- generics [.NET], interfaces
- ordering comparisons [.NET]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
ms.openlocfilehash: 6e107250cef38d532310cd193c9324d1d39c096a
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064058"
---
# <a name="generic-interfaces"></a>Универсальные интерфейсы

В этой статье приводится обзор универсальных интерфейсов, которые предоставляют общие функциональные возможности для различных семейств универсальных типов.  
  
Универсальные интерфейсы — это типобезопасные аналоги неуниверсальных интерфейсов, предназначенные для сортировки и сравнения на равенство, а также для реализации функциональности, совместно используемой универсальными коллекциями.  
  
> [!NOTE]
> Параметры типов нескольких универсальных интерфейсов помечены как ковариантные или контрвариантные, что обеспечивает дополнительную гибкость при назначении и использовании типов, реализующих эти интерфейсы. См. раздел [Ковариация и контрвариация](covariance-and-contravariance.md).  
  
## <a name="equality-and-ordering-comparisons"></a>Упорядочение и сравнение на равенство  
 В пространстве имен <xref:System> универсальные интерфейсы <xref:System.IComparable%601?displayProperty=nameWithType> и <xref:System.IEquatable%601?displayProperty=nameWithType>, как и их неуниверсальные аналоги, определяют методы для упорядочения и сравнения на равенство соответственно. Типы реализуют эти интерфейсы для предоставления способности выполнять такие сравнения.  
  
 В пространстве имен <xref:System.Collections.Generic> универсальные интерфейсы <xref:System.Collections.Generic.IComparer%601> и <xref:System.Collections.Generic.IEqualityComparer%601> позволяют определить операции упорядочения или сравнения на равенство для типов, которые не реализуют универсальный интерфейс <xref:System.IComparable%601?displayProperty=nameWithType> или <xref:System.IEquatable%601?displayProperty=nameWithType>. Кроме того, они позволяют переопределить эти отношения для типов, реализующих эти интерфейсы. Эти интерфейсы используются методами и конструкторами многих универсальных классов коллекций. Например, можно передать универсальный объект <xref:System.Collections.Generic.IComparer%601> в конструктор класса <xref:System.Collections.Generic.SortedDictionary%602>, чтобы указать порядок сортировки для типа, который не реализует универсальный интерфейс <xref:System.IComparable%601?displayProperty=nameWithType>. Предусмотрены перегрузки универсального статического метода <xref:System.Array.Sort%2A?displayProperty=nameWithType> и метода экземпляра <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> для сортировки массивов и списков с помощью реализаций универсального интерфейса <xref:System.Collections.Generic.IComparer%601>.  
  
 Универсальные классы <xref:System.Collections.Generic.Comparer%601> и <xref:System.Collections.Generic.EqualityComparer%601> предоставляют базовые классы для реализаций универсальных интерфейсов <xref:System.Collections.Generic.IComparer%601> и <xref:System.Collections.Generic.IEqualityComparer%601>. Кроме того, они предоставляют операции упорядочения и сравнения на равенство по умолчанию через соответствующие свойства <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> и <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType>.  
  
## <a name="collection-functionality"></a>Функциональные возможности коллекций  
 Универсальный интерфейс <xref:System.Collections.Generic.ICollection%601> представляет собой базовый интерфейс для универсальных типов коллекций. Он предоставляет базовые функции для добавления, удаления, копирования и перечисления элементов. <xref:System.Collections.Generic.ICollection%601> наследуется от универсального интерфейса <xref:System.Collections.Generic.IEnumerable%601> и неуниверсального интерфейса <xref:System.Collections.IEnumerable>.  
  
 Универсальный интерфейс <xref:System.Collections.Generic.IList%601> расширяет универсальный интерфейс <xref:System.Collections.Generic.ICollection%601> с помощью методов для получения элементов по индексу.  
  
 Универсальный интерфейс <xref:System.Collections.Generic.IDictionary%602> расширяет универсальный интерфейс <xref:System.Collections.Generic.ICollection%601> с помощью методов для получения элементов по ключу. Универсальные типы словарей в библиотеке базовых классов .NET также реализуют неуниверсальный интерфейс <xref:System.Collections.IDictionary>.  
  
 Универсальный интерфейс <xref:System.Collections.Generic.IEnumerable%601> предоставляет структуру универсального перечислителя. Универсальный интерфейс <xref:System.Collections.Generic.IEnumerator%601>, реализуемый универсальными перечислителями, наследуется от неуниверсального интерфейса <xref:System.Collections.IEnumerator>. Члены <xref:System.Collections.IEnumerator.MoveNext%2A> и <xref:System.Collections.IEnumerator.Reset%2A>, которые не зависят от параметра типа `T`, присутствуют только в неуниверсальном интерфейсе. Это означает, что любой потребитель неуниверсального интерфейса также может использовать универсальный интерфейс.  
  
## <a name="see-also"></a>См. также

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Универсальные шаблоны](index.md)
- [Универсальные коллекции в .NET](collections.md)
- [Универсальные методы-делегаты для управления массивами и списками](delegates-for-manipulating-arrays-and-lists.md)
- [Ковариация и контрвариантность](covariance-and-contravariance.md)
