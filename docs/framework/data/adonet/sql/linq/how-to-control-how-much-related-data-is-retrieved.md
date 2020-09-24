---
title: Практическое руководство. Как управлять объемом получаемых взаимосвязанных данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 77ac29eeeaa30ef438b635364dc8e883a0e4c158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161338"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Практическое руководство. Как управлять объемом получаемых взаимосвязанных данных

Используйте метод <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>, чтобы указать, какие данные, связанные с основными целевыми объектами, должны быть одновременно извлечены. Например, если известно, что понадобятся сведения о заказах клиентов, можно использовать метод <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>, чтобы гарантировать извлечение данных о заказах одновременно с извлечением с данных о клиентах. Благодаря такому подходу для получения обоих наборов сведений требуется одно обращение к базе данных.  
  
> [!NOTE]
> Данные, связанные с основными целевыми объектами запроса, можно извлекать посредством извлечения перекрестного произведения объектов в виде одной большой проекции, как, например, в случае извлечения заказов одновременно с извлечением клиентов. Однако такой подход имеет свои недостатки. Например, результаты являются всего лишь проекциями, а не сущностями, которые могут быть изменены и сохранены технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Кроме того, может извлекаться большой объем ненужных данных.  
  
## <a name="example"></a>Пример  

 В следующем примере при выполнении запроса извлекаются все заказы (`Orders`) для всех клиентов (`Customers`), расположенных в Лондоне. В результате, при последующем доступе к свойству `Orders` объекта `Customer` не инициируется новый запрос базы данных.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>См. также раздел

- [Запрос к базе данных](querying-the-database.md)
