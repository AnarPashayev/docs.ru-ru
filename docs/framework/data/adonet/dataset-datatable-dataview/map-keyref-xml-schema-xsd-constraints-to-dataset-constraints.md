---
title: Сопоставление ограничений XML-схемы (XSD) keyref с ограничениями набора данных
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 4cc4cb530b7252f35469fd4bb43bf6da9c1a3e24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604021"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="c1236-102">Сопоставление ограничений XML-схемы (XSD) keyref с ограничениями набора данных</span><span class="sxs-lookup"><span data-stu-id="c1236-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="c1236-103">**Keyref** элемент позволяет устанавливать ссылки между элементами внутри документа.</span><span class="sxs-lookup"><span data-stu-id="c1236-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="c1236-104">Это похоже на связь по внешнему ключу в реляционной базе данных.</span><span class="sxs-lookup"><span data-stu-id="c1236-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="c1236-105">Если в схеме **keyref** элемент преобразуется в процессе сопоставления схемы для соответствующего ограничения внешнего ключа на столбцы в таблицах <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c1236-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c1236-106">По умолчанию **keyref** элемент также формирует связь с **ParentTable**, **ChildTable**, **ParentColumn**и  **ChildColumn** свойства, указанными в этой связи.</span><span class="sxs-lookup"><span data-stu-id="c1236-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="c1236-107">В следующей таблице описываются **msdata** атрибуты, можно указать в **keyref** элемент.</span><span class="sxs-lookup"><span data-stu-id="c1236-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="c1236-108">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="c1236-108">Attribute name</span></span>|<span data-ttu-id="c1236-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c1236-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c1236-110">**msdata: constraintonly**</span><span class="sxs-lookup"><span data-stu-id="c1236-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="c1236-111">Если **ConstraintOnly = «true»** заметка указывается для **keyref** элемент в схеме, создается ограничение, но не создается связь.</span><span class="sxs-lookup"><span data-stu-id="c1236-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="c1236-112">Если этот атрибут не указан (или имеет значение **False**), ограничения и отношения создаются в **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c1236-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="c1236-113">**msdata: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="c1236-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="c1236-114">Если **ConstraintName** атрибут указан, его значение используется в качестве имени ограничения.</span><span class="sxs-lookup"><span data-stu-id="c1236-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="c1236-115">В противном случае **имя** атрибут **keyref** элемент в схеме предоставляет имя ограничения в **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c1236-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="c1236-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="c1236-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="c1236-117">Если **UpdateRule** атрибут указан в **keyref** элемента в схеме, его значение будет назначено **UpdateRule** свойство ограничения в  **Набор данных**.</span><span class="sxs-lookup"><span data-stu-id="c1236-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="c1236-118">В противном случае **UpdateRule** свойству **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="c1236-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="c1236-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="c1236-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="c1236-120">Если **DeleteRule** атрибут указан в **keyref** элемента в схеме, его значение будет назначено **DeleteRule** свойство ограничения в  **Набор данных**.</span><span class="sxs-lookup"><span data-stu-id="c1236-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="c1236-121">В противном случае **DeleteRule** свойству **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="c1236-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="c1236-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="c1236-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="c1236-123">Если **AcceptRejectRule** атрибут указан в **keyref** элемента в схеме, его значение будет назначено **AcceptRejectRule** свойство ограничения в  **Набор данных**.</span><span class="sxs-lookup"><span data-stu-id="c1236-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="c1236-124">В противном случае **AcceptRejectRule** свойству **None**.</span><span class="sxs-lookup"><span data-stu-id="c1236-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="c1236-125">В следующем примере содержится схема, которая задает **ключ** и **keyref** связи между **OrderNumber** дочерний элемент элемента **заказа**  элемент и **OrderNo** дочерний элемент элемента **OrderDetail** элемент.</span><span class="sxs-lookup"><span data-stu-id="c1236-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="c1236-126">В примере **OrderNumber** дочерний элемент элемента **OrderDetail** элемент ссылается на **OrderNo** ключа дочерний элемент элемента **порядок**элемент.</span><span class="sxs-lookup"><span data-stu-id="c1236-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="c1236-127">Процесс сопоставления схемы языка XSD определения схемы XML формирует следующие **набора данных** с двумя таблицами:</span><span class="sxs-lookup"><span data-stu-id="c1236-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="c1236-128">Кроме того **набора данных** определяет следующие ограничения:</span><span class="sxs-lookup"><span data-stu-id="c1236-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="c1236-129">Ограничение уникальности на **порядок** таблицы.</span><span class="sxs-lookup"><span data-stu-id="c1236-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="c1236-130">Отношение между **порядок** и **OrderDetail** таблиц.</span><span class="sxs-lookup"><span data-stu-id="c1236-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="c1236-131">**Nested** свойству **False** так, как два элемента не являются вложенными в схеме.</span><span class="sxs-lookup"><span data-stu-id="c1236-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="c1236-132">Ограничение внешнего ключа для **OrderDetail** таблицы.</span><span class="sxs-lookup"><span data-stu-id="c1236-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c1236-133">См. также</span><span class="sxs-lookup"><span data-stu-id="c1236-133">See also</span></span>

- [<span data-ttu-id="c1236-134">Сопоставление ограничений схемы XML (XSD) с ограничениями DataSet</span><span class="sxs-lookup"><span data-stu-id="c1236-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c1236-135">Создание отношений DataSet из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="c1236-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c1236-136">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1236-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
