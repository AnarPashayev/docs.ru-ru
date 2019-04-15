---
title: Включение или импорт XML-схем
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45f6b402ae01b7f762f8ef10dcfb0bc46f949db6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343575"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="6e7ab-102">Включение или импорт XML-схем</span><span class="sxs-lookup"><span data-stu-id="6e7ab-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="6e7ab-103">Схема XML может содержать элементы `<xs:import />`, `<xs:include />` и `<xs:redefine />`.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="6e7ab-104">Эти элементы схемы ссылаются на другие схемы XML, которые можно использовать в дополнение к структуре схемы, их включающей или импортирующей.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="6e7ab-105">Классы <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> и <xref:System.Xml.Schema.XmlSchemaRedefine> сопоставляются с этими элементами в API модели SOM.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="6e7ab-106">Включение или импорт схемы XML</span><span class="sxs-lookup"><span data-stu-id="6e7ab-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="6e7ab-107">В следующем примере кода [пользовательская схема XML](../../../../docs/standard/data/xml/building-xml-schemas.md) дополняется схемой адресов.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="6e7ab-108">Добавление к пользовательской схеме схемы адресов делает типы адресов доступными в пользовательской схеме.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="6e7ab-109">Схему адресов можно добавить с помощью элементов `<xs:include />` или `<xs:import />`, использующих компоненты схемы адресов без изменения, или с помощью элемента `<xs:redefine />`, который изменяет компоненты схемы в соответствии с задачами пользовательской схемы.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="6e7ab-110">Поскольку схема адресов имеет пространство имен `targetNamespace`, которое отличается от пользовательской схемы, используется элемент `<xs:import />` и семантика импорта.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="6e7ab-111">Пример кода включает пользовательскую схему со следующими шагами.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="6e7ab-112">Добавление пользовательской схемы и схемы адресов в новый объект <xref:System.Xml.Schema.XmlSchemaSet> и компиляция схем.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="6e7ab-113">Все предупреждения и ошибки проверки схемы, обнаруженные в процессе чтения или компиляции, обрабатываются делегатом <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="6e7ab-114">Получение скомпилированных объектов <xref:System.Xml.Schema.XmlSchema> для пользовательской схемы и схемы адресов из <xref:System.Xml.Schema.XmlSchemaSet> путем прохода по свойству <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="6e7ab-115">Так как схемы скомпилированы, доступны свойства информационного набора PSCI.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="6e7ab-116">Создание объекта <xref:System.Xml.Schema.XmlSchemaImport>, задание в свойстве импорта <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> пространства имен схемы адресов, задание в свойстве импорта <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> объекта <xref:System.Xml.Schema.XmlSchema> схемы адресов и добавление импорта в свойство <xref:System.Xml.Schema.XmlSchema.Includes%2A> пользовательской схемы.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="6e7ab-117">Повторная обработка и компиляция измененного объекта <xref:System.Xml.Schema.XmlSchema> с помощью методов <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> и <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> и последующая запись объекта в консоль.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="6e7ab-118">Заключительный шаг - рекурсивная запись всех схем, импортированных в пользовательскую схему, в консоль с помощью свойства <xref:System.Xml.Schema.XmlSchema.Includes%2A> пользовательской схемы.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="6e7ab-119">Свойство <xref:System.Xml.Schema.XmlSchema.Includes%2A> предоставляет доступ ко всем объектам, добавленным в схему путем включения, импорта или переопределения.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="6e7ab-120">Далее приведен полный пример кода, а также пользовательская схема и схема адресов, записанные в консоль.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="6e7ab-121">Дополнительные сведения об элементах `<xs:import />`, `<xs:include />` и `<xs:redefine />`, а также классах <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> и <xref:System.Xml.Schema.XmlSchemaRedefine> см. в [документации консорциума W3C по схемам XML](https://www.w3.org/XML/Schema) и в справочной документации по классу пространства имен <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e7ab-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7ab-122">См. также</span><span class="sxs-lookup"><span data-stu-id="6e7ab-122">See also</span></span>

- [<span data-ttu-id="6e7ab-123">Общие сведения об модели объектов XML-схемы</span><span class="sxs-lookup"><span data-stu-id="6e7ab-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="6e7ab-124">Чтение и запись XML-схем</span><span class="sxs-lookup"><span data-stu-id="6e7ab-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="6e7ab-125">Построение XML-схем</span><span class="sxs-lookup"><span data-stu-id="6e7ab-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="6e7ab-126">Обход XML-схем</span><span class="sxs-lookup"><span data-stu-id="6e7ab-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="6e7ab-127">Изменение XML-схем</span><span class="sxs-lookup"><span data-stu-id="6e7ab-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="6e7ab-128">XmlSchemaSet для компиляции схемы</span><span class="sxs-lookup"><span data-stu-id="6e7ab-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
