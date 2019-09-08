---
title: Создание примечаний к типизированным наборам данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 351175b96d354a264a9280018ce21de8870beda2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784806"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="4b2f3-102">Создание примечаний к типизированным наборам данных</span><span class="sxs-lookup"><span data-stu-id="4b2f3-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="4b2f3-103">Заметки дают возможность изменять имена элементов в типизированных <xref:System.Data.DataSet> без изменения базовой схемы.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="4b2f3-104">Изменение имен элементов в базовой схеме приведет к тому, что типизированный **набор данных** будет ссылаться на объекты, не существующие в источнике данных, а также будет потеряна ссылка на объекты, существующие в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="4b2f3-105">С помощью заметок можно настроить имена объектов в типизированном **наборе данных** с более информативными именами, сделать код более удобочитаемым, а типизированный **набор данных** проще использовать для использования клиентами, при этом не изменяя базовую схему.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="4b2f3-106">Например, следующий элемент схемы для таблицы **Customers** базы данных **Northwind** приведет к появлению <xref:System.Data.DataRowCollection> имени объекта **DataRow** **кустомерсров** и именованных **клиентов**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="4b2f3-107">**Датаровколлектион** имя **клиентов** имеет смысл в клиентском коде, но имя **DataRow** **кустомерсров** является ошибочным, поскольку является одним объектом.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="4b2f3-108">Кроме того, в обычных сценариях объект будет называться без идентификатора **строки** , а вместо этого будет просто называться объектом **Customer** .</span><span class="sxs-lookup"><span data-stu-id="4b2f3-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="4b2f3-109">Решение заключается в создании заметка схемы и определении новых имен для объектов **DataRow** и **датаровколлектион** .</span><span class="sxs-lookup"><span data-stu-id="4b2f3-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="4b2f3-110">Далее приводится версия предыдущей схемы с добавленными заметками.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="4b2f3-111">При указании значения **типеднаме** для **Customer** будет выдаваться имя объекта **DataRow** **Customer**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="4b2f3-112">Указание значения **типедплурал** для **клиентов** сохраняет имя **датаровколлектион** **клиентов**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="4b2f3-113">В следующей таблице показаны доступные для использования заметки.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="4b2f3-114">Комментарий</span><span class="sxs-lookup"><span data-stu-id="4b2f3-114">Annotation</span></span>|<span data-ttu-id="4b2f3-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4b2f3-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4b2f3-116">**типеднаме**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-116">**typedName**</span></span>|<span data-ttu-id="4b2f3-117">Имя объекта.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-117">Name of the object.</span></span>|  
|<span data-ttu-id="4b2f3-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-118">**typedPlural**</span></span>|<span data-ttu-id="4b2f3-119">Имя коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="4b2f3-120">**типедпарент**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-120">**typedParent**</span></span>|<span data-ttu-id="4b2f3-121">Имя объекта при ссылке на родительскую связь.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="4b2f3-122">**типедчилдрен**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-122">**typedChildren**</span></span>|<span data-ttu-id="4b2f3-123">Имя метода, возвращающего объекты по дочерней связи.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="4b2f3-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-124">**nullValue**</span></span>|<span data-ttu-id="4b2f3-125">Значение, если базовое значение равно **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="4b2f3-126">См. следующую таблицу для **NullValue** Annotations.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="4b2f3-127">Значение по умолчанию — **_throw**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="4b2f3-128">В следующей таблице приведены значения, которые можно указать для аннотации **NullValue** .</span><span class="sxs-lookup"><span data-stu-id="4b2f3-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="4b2f3-129">Значение nullValue</span><span class="sxs-lookup"><span data-stu-id="4b2f3-129">nullValue Value</span></span>|<span data-ttu-id="4b2f3-130">Описание</span><span class="sxs-lookup"><span data-stu-id="4b2f3-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="4b2f3-131">*Заменяющее значение*</span><span class="sxs-lookup"><span data-stu-id="4b2f3-131">*Replacement Value*</span></span>|<span data-ttu-id="4b2f3-132">Задает возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-132">Specify a value to be returned.</span></span> <span data-ttu-id="4b2f3-133">Возвращаемое значение должно соответствовать типу элемента.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="4b2f3-134">Например, чтобы для целочисленных полей вместо null возвращался 0, используйте `nullValue="0"`.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="4b2f3-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-135">**_throw**</span></span>|<span data-ttu-id="4b2f3-136">Создание исключения.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-136">Throw an exception.</span></span> <span data-ttu-id="4b2f3-137">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-137">This is the default.</span></span>|  
|<span data-ttu-id="4b2f3-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-138">**_null**</span></span>|<span data-ttu-id="4b2f3-139">Возвращает ссылку null или создает исключение, если встречается примитивный тип.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="4b2f3-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-140">**_empty**</span></span>|<span data-ttu-id="4b2f3-141">Для строк возвращает **String. Empty**, в противном случае возвращает объект, созданный из пустого конструктора.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="4b2f3-142">Если встречается примитивный тип, вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="4b2f3-143">В следующей таблице показаны значения по умолчанию для объектов в типизированном **наборе данных** и доступных аннотациях.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="4b2f3-144">Объект/Метод/Событие</span><span class="sxs-lookup"><span data-stu-id="4b2f3-144">Object/Method/Event</span></span>|<span data-ttu-id="4b2f3-145">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="4b2f3-145">Default</span></span>|<span data-ttu-id="4b2f3-146">Комментарий</span><span class="sxs-lookup"><span data-stu-id="4b2f3-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="4b2f3-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-147">**DataTable**</span></span>|<span data-ttu-id="4b2f3-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="4b2f3-148">TableNameDataTable</span></span>|<span data-ttu-id="4b2f3-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="4b2f3-149">typedPlural</span></span>|  
|<span data-ttu-id="4b2f3-150">**DataTable** Метод</span><span class="sxs-lookup"><span data-stu-id="4b2f3-150">**DataTable** Methods</span></span>|<span data-ttu-id="4b2f3-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="4b2f3-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="4b2f3-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="4b2f3-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="4b2f3-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="4b2f3-153">DeleteTableNameRow</span></span>|<span data-ttu-id="4b2f3-154">typedName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-154">typedName</span></span>|  
|<span data-ttu-id="4b2f3-155">**датаровколлектион**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-155">**DataRowCollection**</span></span>|<span data-ttu-id="4b2f3-156">TableName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-156">TableName</span></span>|<span data-ttu-id="4b2f3-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="4b2f3-157">typedPlural</span></span>|  
|<span data-ttu-id="4b2f3-158">**Строку**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-158">**DataRow**</span></span>|<span data-ttu-id="4b2f3-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="4b2f3-159">TableNameRow</span></span>|<span data-ttu-id="4b2f3-160">typedName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-160">typedName</span></span>|  
|<span data-ttu-id="4b2f3-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-161">**DataColumn**</span></span>|<span data-ttu-id="4b2f3-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="4b2f3-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="4b2f3-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-163">DataRow.ColumnName</span></span>|<span data-ttu-id="4b2f3-164">typedName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-164">typedName</span></span>|  
|<span data-ttu-id="4b2f3-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="4b2f3-165">**Property**</span></span>|<span data-ttu-id="4b2f3-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-166">PropertyName</span></span>|<span data-ttu-id="4b2f3-167">typedName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-167">typedName</span></span>|  
|<span data-ttu-id="4b2f3-168">**Дочерний элемент** Возмож</span><span class="sxs-lookup"><span data-stu-id="4b2f3-168">**Child** Accessor</span></span>|<span data-ttu-id="4b2f3-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="4b2f3-169">GetChildTableNameRows</span></span>|<span data-ttu-id="4b2f3-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="4b2f3-170">typedChildren</span></span>|  
|<span data-ttu-id="4b2f3-171">**Родительский элемент** Возмож</span><span class="sxs-lookup"><span data-stu-id="4b2f3-171">**Parent** Accessor</span></span>|<span data-ttu-id="4b2f3-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="4b2f3-172">TableNameRow</span></span>|<span data-ttu-id="4b2f3-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="4b2f3-173">typedParent</span></span>|  
|<span data-ttu-id="4b2f3-174">**Набор данных** Событиях</span><span class="sxs-lookup"><span data-stu-id="4b2f3-174">**DataSet** Events</span></span>|<span data-ttu-id="4b2f3-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="4b2f3-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="4b2f3-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="4b2f3-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="4b2f3-177">typedName</span><span class="sxs-lookup"><span data-stu-id="4b2f3-177">typedName</span></span>|  
  
 <span data-ttu-id="4b2f3-178">Чтобы использовать зааннотации типизированного **набора данных** , необходимо включить следующую ссылку **xmlns** в схему языка определения схемы XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="4b2f3-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="4b2f3-179">Сведения о создании XSD на основе таблиц базы данных <xref:System.Data.DataSet.WriteXmlSchema%2A> см. в разделе или [Работа с DataSets в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4b2f3-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="4b2f3-180">Ниже приведен пример схемы с заметками, которая предоставляет таблицу **Customers** базы данных **Northwind** с отношением к включенной таблице **Orders** .</span><span class="sxs-lookup"><span data-stu-id="4b2f3-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="4b2f3-181">В следующем примере кода используется строго типизированный **набор данных** , созданный из образца схемы.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="4b2f3-182">Он использует один <xref:System.Data.SqlClient.SqlDataAdapter> из них для заполнения таблицы **Customers** , <xref:System.Data.SqlClient.SqlDataAdapter> а другой — для заполнения таблицы **Orders** .</span><span class="sxs-lookup"><span data-stu-id="4b2f3-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="4b2f3-183">Строго типизированный **набор данных** определяет **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="4b2f3-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b2f3-184">См. также</span><span class="sxs-lookup"><span data-stu-id="4b2f3-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="4b2f3-185">Типизированные наборы данных</span><span class="sxs-lookup"><span data-stu-id="4b2f3-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="4b2f3-186">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="4b2f3-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4b2f3-187">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4b2f3-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
