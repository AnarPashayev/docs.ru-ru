---
title: AcceptChanges и RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: bbcc666b99c2bade479e5ee51750b043c820845d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172904"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges и RejectChanges
После проверки точности изменения, внесенные в данные в <xref:System.Data.DataTable>, вы можете принять изменения с помощью <xref:System.Data.DataRow.AcceptChanges%2A> метод <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, или <xref:System.Data.DataSet>, задающий **текущей** строки значения были **исходного** значения и задаст **RowState** свойства **Unchanged**. Принятие или отклонение изменений удаление всех **RowError** и свойству **HasErrors** свойства **false**. Принятие или отклонение изменений также может затрагивать обновление данных в источнике данных. Дополнительные сведения см. в разделе [обновление источников данных с объектами DataAdapter](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Если существуют ограничения внешнего ключа на **DataTable**, изменения, принятые или отклоненные с помощью **AcceptChanges** и **RejectChanges** распространяются на дочерние строки объекта  **DataRow** согласно **ForeignKeyConstraint.AcceptRejectRule**. Дополнительные сведения см. в разделе [ограничения таблиц данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 В следующем примере происходит проверка на наличие строк с ошибками, по возможности устраняются ошибки и отклоняются строки, в которых ошибка не может быть устранена. Обратите внимание, что применительно к устраненным ошибкам **RowError** значение сбрасывается на пустую строку, вызывая **HasErrors** свойству будет присвоено **false**. Когда все строки с ошибками после устранения ошибок или отклонения **AcceptChanges** вызывается для принятия всех изменений для всего **DataTable**.  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Управление данными в таблице данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Управляемые поставщики ADO.NET и центр разработчиков DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
