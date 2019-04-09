---
title: Наследование реляционной структуры набора данных от схемы XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119695"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Наследование реляционной структуры набора данных от схемы XML (XSD)
В этом разделе приведены общие сведения о построении реляционной схемы `DataSet` на основе документа схемы на языке XSD. Как правило, для каждого `complexType` дочерний элемент элемента схемы, будет создана таблица в `DataSet`. Структура таблицы задается определением сложного типа. Таблицы создаются в `DataSet` для элементов верхнего уровня в схеме. Тем не менее, только создается таблица для верхнего уровня `complexType` элемент при `complexType` элемент вложен в другой `complexType` случае вложенный элемент, в котором `complexType` элемент сопоставлен с `DataTable` в `DataSet`.  
  
 Дополнительные сведения о языке XSD см. в разделе World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/)и [XML Schema Part 2: Рекомендация по типам данных](https://www.w3.org/TR/xmlschema-2/).  
  
 В следующем примере показано XML-схемы где `customers` является дочерним элементом элемента `MyDataSet` элемент, который является **набора данных** элемент.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 В предыдущем примере элемент `customers` является элементом сложного типа. Поэтому проводится синтаксический анализ определения сложного типа, а процесс сопоставления создает следующую таблицу.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Тип данных каждого столбца в таблице получается из типа схемы XML соответствующего элемента или указанного атрибута.  
  
> [!NOTE]
>  Если элемент `customers` является простого типа данных схемы XML, такие как **целое число**, то таблица не создается. Таблицы создаются только для элементов верхнего уровня, которые являются сложными типами.  
  
 В следующей схеме XML **схемы** элемент имеет два дочерних элемента `InStateCustomers` и `OutOfStateCustomers`.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Дочерние элементы `InStateCustomers` и `OutOfStateCustomers` являются элементами сложного типа (`customerType`). Таким образом, процесс сопоставления создает две следующие одинаковые таблицы в `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>В этом разделе  
 [Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Описывает элементы схемы XML, используемые для создания ограничений уникального и внешнего ключа в `DataSet`.  
  
 [Создание отношений наборов данных из схемы XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Описывает элементы схемы XML, используемые для создания связей между столбцами таблиц в `DataSet`.  
  
 [Ограничения и отношения схемы XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Описывает, как неявного создания связей при использовании элементов схемы XML для создания ограничений в `DataSet`.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Использование XML в наборах данных](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Описывает, как для загрузки и сохранения реляционной структуры и данных в `DataSet` как XML-данных.  
  
## <a name="see-also"></a>См. также

- [Управляемые поставщики ADO.NET и центр разработчиков DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
