---
title: Создание отношений наборов данных из схемы XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 29c0e9ee96c376c6da392692febccbbae3c6a33f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034324"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="5fa26-102">Создание отношений наборов данных из схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="5fa26-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="5fa26-103">В <xref:System.Data.DataSet> взаимосвязь между двумя или несколькими столбцами формируется путем создания отношения «родитель-потомок».</span><span class="sxs-lookup"><span data-stu-id="5fa26-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="5fa26-104">Существует три способа представления **набора данных** отношения в схему языка определения схемы XML:</span><span class="sxs-lookup"><span data-stu-id="5fa26-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="5fa26-105">Задайте вложенные сложные типы.</span><span class="sxs-lookup"><span data-stu-id="5fa26-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="5fa26-106">Используйте **msdata: Relationship** заметки.</span><span class="sxs-lookup"><span data-stu-id="5fa26-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="5fa26-107">Укажите **xs: keyref** без **msdata: constraintonly** заметки.</span><span class="sxs-lookup"><span data-stu-id="5fa26-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="5fa26-108">Вложенные сложные типы</span><span class="sxs-lookup"><span data-stu-id="5fa26-108">Nested Complex Types</span></span>  
 <span data-ttu-id="5fa26-109">Определения вложенных сложных типов в схеме указывают на связь элементов по модели «родитель-потомок».</span><span class="sxs-lookup"><span data-stu-id="5fa26-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="5fa26-110">В следующем фрагменте схемы XML показано, что **OrderDetail** является дочерним элементом элемента **порядок** элемент.</span><span class="sxs-lookup"><span data-stu-id="5fa26-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="5fa26-111">Процесс сопоставления схем XML создает таблицы в **набора данных** , соответствующие вложенным сложным типам в схеме.</span><span class="sxs-lookup"><span data-stu-id="5fa26-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="5fa26-112">Он также создает дополнительные столбцы, которые используются в качестве родительского**-** дочерних столбцов в созданных таблицах.</span><span class="sxs-lookup"><span data-stu-id="5fa26-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="5fa26-113">Обратите внимание, что их родительский**-** дочерние столбцы задают связи, который не так же, как и при указании ограничений primary key/foreign key.</span><span class="sxs-lookup"><span data-stu-id="5fa26-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="5fa26-114">Заметка msdata:Relationship</span><span class="sxs-lookup"><span data-stu-id="5fa26-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="5fa26-115">**Msdata: Relationship** заметки можно явно указать иерархические отношения между элементами в схеме, которые не являются вложенными.</span><span class="sxs-lookup"><span data-stu-id="5fa26-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="5fa26-116">В следующем примере показана структура **связь** элемент.</span><span class="sxs-lookup"><span data-stu-id="5fa26-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="5fa26-117">Атрибуты **msdata: Relationship** заметки идентификации элементов, входящую в связь родитель потомок, а также как **parentkey** и **childkey** элементы и атрибуты, участвующие в связи.</span><span class="sxs-lookup"><span data-stu-id="5fa26-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="5fa26-118">Процесс сопоставления использует эти сведения для создания таблиц в **набора данных** и для создания первичного/внешнего ключа связи между этими таблицами.</span><span class="sxs-lookup"><span data-stu-id="5fa26-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="5fa26-119">Например, следующий фрагмент схемы задает **порядок** и **OrderDetail** элементов того же уровня (не вложенные).</span><span class="sxs-lookup"><span data-stu-id="5fa26-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="5fa26-120">Схема задает **msdata: Relationship** заметки, который указывает связь «родители потомки» между этими элементами.</span><span class="sxs-lookup"><span data-stu-id="5fa26-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="5fa26-121">В этом случае явную связь необходимо указать с помощью **msdata: Relationship** заметки.</span><span class="sxs-lookup"><span data-stu-id="5fa26-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="5fa26-122">Процесс сопоставления использует **связь** элемент, чтобы создать отношение "родитель потомок" между **OrderNumber** столбца в **порядок** таблицы и **OrderNo** столбца в **OrderDetail** в таблицу **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="5fa26-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="5fa26-123">Процесс сопоставления только указывает связь, он не задает автоматически ограничения значений в этих столбцах подобно ограничениям первичного/внешнего ключа в реляционных базах данных.</span><span class="sxs-lookup"><span data-stu-id="5fa26-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="5fa26-124">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="5fa26-124">In This Section</span></span>  
 [<span data-ttu-id="5fa26-125">Сопоставление неявных отношений между вложенными элементами схемы</span><span class="sxs-lookup"><span data-stu-id="5fa26-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="5fa26-126">Описание ограничений и связей, неявно создаваемых в **набора данных** при в схеме XML встречаются вложенные элементы.</span><span class="sxs-lookup"><span data-stu-id="5fa26-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="5fa26-127">Сопоставление отношений, заданных для вложенных элементов</span><span class="sxs-lookup"><span data-stu-id="5fa26-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="5fa26-128">Описание способов явной установки связей в **набора данных** для вложенных элементов в схеме XML.</span><span class="sxs-lookup"><span data-stu-id="5fa26-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="5fa26-129">Указание отношений между элементами без вложенности</span><span class="sxs-lookup"><span data-stu-id="5fa26-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="5fa26-130">Описывает создание отношений в **набора данных** между элементами схемы XML, которые не являются вложенными.</span><span class="sxs-lookup"><span data-stu-id="5fa26-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="5fa26-131">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="5fa26-131">Related Sections</span></span>  
 [<span data-ttu-id="5fa26-132">Наследование реляционной структуры DataSet от схемы XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="5fa26-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="5fa26-133">Описывает реляционную структуру, или схему, **набора данных** , созданную из схемы языка определения схемы XML.</span><span class="sxs-lookup"><span data-stu-id="5fa26-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="5fa26-134">Сопоставление ограничений схемы XML (XSD) с ограничениями DataSet</span><span class="sxs-lookup"><span data-stu-id="5fa26-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="5fa26-135">Описывает элементы схемы XML, используемые для создания ограничений уникального и внешнего ключа в **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="5fa26-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa26-136">См. также</span><span class="sxs-lookup"><span data-stu-id="5fa26-136">See also</span></span>

- [<span data-ttu-id="5fa26-137">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5fa26-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
