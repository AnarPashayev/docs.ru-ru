---
title: Примеры синтаксиса запросов на основе методов. Секционирование
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 42c562e7665a53053f125c17d073eb437574939f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250119"
---
# <a name="method-based-query-syntax-examples-partitioning"></a>Примеры синтаксиса запросов на основе методов. Секционирование
В примерах этого раздела показано <xref:System.Linq.Enumerable.Skip%2A>, как использовать методы и <xref:System.Linq.Enumerable.Take%2A> для запроса [модели AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples) с помощью синтаксиса выражений запросов. Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.  
  
 В примерах этого раздела используются следующие `using` / `Imports` инструкции:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a>Skip  
  
### <a name="example"></a>Пример  
 В следующем примере метод <xref:System.Linq.Enumerable.Skip%2A> используется для возврата всех контактов в таблице Contact, за исключением первых пяти.  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a>Пример  
 В следующем примере метод <xref:System.Linq.Enumerable.Skip%2A> используется для получения всех адресов в Сиэттле, кроме первых двух.  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a>Take  
  
### <a name="example"></a>Пример  
 В следующем примере метод <xref:System.Linq.Enumerable.Take%2A> используется для возврата первых пяти контактов из таблицы Contact.  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a>Пример  
 В следующем примере метод <xref:System.Linq.Enumerable.Take%2A> используется для получения первых трех адресов в Сиэттле.  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a>См. также

- [Запросы в LINQ to Entities](queries-in-linq-to-entities.md)
