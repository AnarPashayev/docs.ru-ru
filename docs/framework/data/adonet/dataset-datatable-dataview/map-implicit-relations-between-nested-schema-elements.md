---
title: Сопоставление неявных отношений между вложенными элементами схемы
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 32f8bf67242143098717b47c3b7aa175317ba274
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201321"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="97585-102">Сопоставление неявных отношений между вложенными элементами схемы</span><span class="sxs-lookup"><span data-stu-id="97585-102">Map Implicit Relations Between Nested Schema Elements</span></span>

<span data-ttu-id="97585-103">Схема на языке XSD может иметь сложные типы, вложенные друг в друга.</span><span class="sxs-lookup"><span data-stu-id="97585-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="97585-104">В этом случае процесс сопоставления применяет сопоставление по умолчанию и создает в объекте <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="97585-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="97585-105">одну таблицу для каждого сложного типа (родительского и дочернего);</span><span class="sxs-lookup"><span data-stu-id="97585-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="97585-106">Если для родителя не существует ограничений UNIQUE, по одному дополнительному первичному ключевому столбцу для определения таблицы с именем *tablename*_Id, где *TableName* — это имя родительской таблицы.</span><span class="sxs-lookup"><span data-stu-id="97585-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="97585-107">Ограничение первичного ключа в родительской таблице, определяющее дополнительный столбец в качестве первичного ключа (путем присвоения свойству **IsPrimaryKey имеют значение** значения **true**).</span><span class="sxs-lookup"><span data-stu-id="97585-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="97585-108">Ограничению назначается имя Constraint\#, где \# - это 1, 2, 3 и т. д.</span><span class="sxs-lookup"><span data-stu-id="97585-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="97585-109">Например, имя первого ограничения по умолчанию - Constraint1;</span><span class="sxs-lookup"><span data-stu-id="97585-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="97585-110">ограничение внешнего ключа для дочерней таблицы, определяющее дополнительный столбец как внешний ключ, ссылающийся на первичный ключ родительской таблицы.</span><span class="sxs-lookup"><span data-stu-id="97585-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="97585-111">Ограничение называется *ParentTable_ChildTable* , где *паренттабле* — имя родительской таблицы, а *ChildTable* — имя дочерней таблицы.</span><span class="sxs-lookup"><span data-stu-id="97585-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="97585-112">связи данных между родительскими и дочерними таблицами.</span><span class="sxs-lookup"><span data-stu-id="97585-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="97585-113">В следующем примере показана схема, в которой **OrderDetail** является дочерним элементом **Order**.</span><span class="sxs-lookup"><span data-stu-id="97585-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="97585-114">Процесс сопоставления схем XML создает в **наборе данных**следующее:</span><span class="sxs-lookup"><span data-stu-id="97585-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="97585-115">**Заказ** и таблица **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="97585-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="97585-116">Ограничение UNIQUE для таблицы **Order** .</span><span class="sxs-lookup"><span data-stu-id="97585-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="97585-117">Обратите внимание, что свойство **IsPrimaryKey имеют значение** имеет значение **true**.</span><span class="sxs-lookup"><span data-stu-id="97585-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="97585-118">Ограничение внешнего ключа для таблицы **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="97585-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="97585-119">Связь между таблицами **Order** и **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="97585-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="97585-120">**Вложенному** свойству для этой связи присваивается **значение true** , поскольку элементы **Order** и **OrderDetail** вложены в схему.</span><span class="sxs-lookup"><span data-stu-id="97585-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97585-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="97585-121">See also</span></span>

- [<span data-ttu-id="97585-122">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="97585-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="97585-123">Сопоставление ограничений XML-схемы (XSD) с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="97585-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="97585-124">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="97585-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
