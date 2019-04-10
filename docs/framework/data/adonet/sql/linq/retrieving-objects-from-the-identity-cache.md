---
title: Извлечение объектов из кэша идентификации
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211235"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Извлечение объектов из кэша идентификации
В этом разделе описаны типы запросов LINQ to SQL, которые возвращают объект из кэша идентификаторов, управляемого <xref:System.Data.Linq.DataContext>.  
  
 В LINQ to SQL в качестве одного из способов управления объектами <xref:System.Data.Linq.DataContext> регистрируют идентификаторы объектов в кэше идентификаторов во время выполнения запросов. В некоторых случаях LINQ to SQL пытается получить объект из кэша идентификаторов перед выполнением запроса в базе данных.  
  
 Обычно, чтобы запрос LINQ to SQL мог вернуть объект из кэша идентификаторов, запрос должен быть основан на первичном ключе объекта и должен возвращать одиночный объект. В частности, запрос должен иметь одну из общих форм, представленных далее.  
  
> [!NOTE]
>  Предварительно скомпилированные запросы не возвращают объекты из кэша идентификаторов. Дополнительные сведения о предварительно скомпилированных запросах см. в разделе <xref:System.Data.Linq.CompiledQuery> и [как: Store и повторное использование запросов](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Чтобы получить объект из кэша идентификаторов, запрос должен иметь одну из следующих общих форм.  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 В этих общих формах параметры `Function1`, `Function2` и `predicate` определяются следующим образом.  
  
 `Function1` может быть одним из следующих:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` может быть одним из следующих:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` должно быть выражением, в котором свойство первичного ключа объекта присваивается значение константы. Если первичный ключ определен в нескольких свойствах объекта, то в каждом свойстве должно быть задано постоянное значение. Далее представлены примеры формы, которую должен принимать параметр `predicate`.  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Пример  
 В следующем коде приводятся примеры типов запросов LINQ to SQL, которые получают объект из кэша идентификаторов.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>См. также

- [Основные принципы запросов](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Идентификация объектов](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Основные сведения](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Идентификация объектов](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
