---
title: Сортировка и фильтрация данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 8d8bd85f65adfde5f239e1e2dd79d65517b745a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166248"
---
# <a name="sorting-and-filtering-data"></a>Сортировка и фильтрация данных
<xref:System.Data.DataView> предоставляет несколько способов сортировки и фильтрации данных в <xref:System.Data.DataTable>.  
  
-   Можно использовать свойство <xref:System.Data.DataView.Sort%2A> для задания одного или нескольких порядков сортировки столбцов и включить параметры ASC (по возрастанию) и DESC (по убыванию).  
  
-   Свойство <xref:System.Data.DataView.ApplyDefaultSort%2A> служит для автоматического создания порядка сортировки по возрастанию на основании столбца или столбцов первичного ключа таблицы. <xref:System.Data.DataView.ApplyDefaultSort%2A> применяется, только когда **сортировки** свойство является пустой ссылкой или пустой строкой, и если таблица имеет первичный ключ.  
  
-   Свойство <xref:System.Data.DataView.RowFilter%2A> можно использовать для задания подмножеств строк на основании значений их столбцов. Дополнительные сведения о допустимых выражениях для **RowFilter** свойство, см. в справочных сведениях для <xref:System.Data.DataColumn.Expression%2A> свойство <xref:System.Data.DataColumn> класса.  
  
     Если вы хотите вернуть результаты определенного запроса данных, а не динамическое представление подмножества данных, используйте <xref:System.Data.DataView.Find%2A> или <xref:System.Data.DataView.FindRows%2A> методы **DataView** для обеспечения лучшей производительности вместо Установка **RowFilter** свойство. Установка **RowFilter** свойство перестраивается индекс данных, что добавляет нагрузку на приложение и снижает производительность. **RowFilter** свойство лучше всего использовать в приложении привязкой к данным где элемент связывания отображает отфильтрованные результаты. **Найти** и **FindRows** методы используют текущий индекс, не требуя его перестроения. Дополнительные сведения о **найти** и **FindRows** методы, см. в разделе [поиск строк](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Свойство <xref:System.Data.DataView.RowStateFilter%2A> можно использовать для определения, какие версии строк следует просматривать. **DataView** неявно управляет версией строки, используемой для предоставления, в зависимости от **RowState** основной строки. Например если **RowStateFilter** присваивается **DataViewRowState.Deleted**, **DataView** предоставляет **исходного** версии все **Deleted** строк, так как существует не **текущей** версию строки. Можно определить, какая версия строки строку предоставляется с помощью **RowVersion** свойство **DataRowView**.  
  
     В следующей таблице показаны параметры для **DataViewRowState**.  
  
    |Параметры DataViewRowState|Описание|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Текущей** из всех **Unchanged**, **Added**, и **Modified** строк. Это значение по умолчанию.|  
    |**Добавлен**|**Текущей** из всех **Added** строк.|  
    |**Удален**|**Исходного** из всех **Deleted** строк.|  
    |**ModifiedCurrent**|**Текущей** из всех **Modified** строк.|  
    |**ModifiedOriginal**|**Исходного** из всех **Modified** строк.|  
    |**None**|Нет строк.|  
    |**OriginalRows**|**Исходного** из всех **Unchanged**, **Modified**, и **Deleted** строк.|  
    |**без изменений**|**Текущей** из всех **Unchanged** строк.|  
  
 Дополнительные сведения о состояниях и версиях строк см. в разделе [строки состояния и версии строк](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 В следующем примере кода создается представление, которое показывает все продукты, где число элементов на складе меньше или равно уровню переупорядочения, отсортированного вначале по идентификаторам поставщиков, а затем по названиям продуктов.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Объекты DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](https://go.microsoft.com/fwlink/?LinkId=217917)
