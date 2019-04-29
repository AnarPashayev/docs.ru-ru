---
title: Запись сведений о схеме набора данных как XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 8403f9d9be88f34e473fd3512f5499193245d227
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607053"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Запись сведений о схеме набора данных как XSD
Можно записать схему набора данных <xref:System.Data.DataSet> в виде схемы на языке XSD, чтобы можно было передать ее в XML-документ с взаимосвязанными данными или без них. XML-схемы могут записываться в файл, поток, <xref:System.Xml.XmlWriter>, или строку; это полезно для создания строго типизированного **набора данных**. Дополнительные сведения о строго типизированных **набора данных** объектов, см. в разделе [типизированных наборов DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Можно указать, как столбец таблицы представляется в XML-схемы с помощью **ColumnMapping** свойство <xref:System.Data.DataColumn> объекта. Дополнительные сведения см. в разделе «Сопоставление столбцов с XML-элементов, атрибутов и текст» в [запись содержимого набора данных как XML-данные](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Чтобы записать схему набора **набора данных** виде схемы XML, в файл, поток, или **XmlWriter**, использовать **WriteXmlSchema** метод **набора данных**. **WriteXmlSchema** принимает один параметр, указывающий место назначения результирующей схемы XML. В следующих примерах кода показано, как для записи XML-схемы **набора данных** в файл, передав строку, содержащую имя файла и <xref:System.IO.StreamWriter> объекта.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Для получения схемы объекта **набора данных** и его записи в виде строки схемы XML, используйте **GetXmlSchema** метод, как показано в следующем примере.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>См. также

- [Использование XML в наборах данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Запись содержимого DataSet как данных XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [Типизированные наборы данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Наборы данных, таблицы данных и объекты DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](https://go.microsoft.com/fwlink/?LinkId=217917)
