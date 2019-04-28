---
title: Ограничения определения
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879649"
---
# <a name="inference-limitations"></a><span data-ttu-id="6c18b-102">Ограничения определения</span><span class="sxs-lookup"><span data-stu-id="6c18b-102">Inference Limitations</span></span>
<span data-ttu-id="6c18b-103">Процесс вывода схемы <xref:System.Data.DataSet> из XML-кода может приводиться в различных схемах в зависимости от XML-элементов в каждом документе.</span><span class="sxs-lookup"><span data-stu-id="6c18b-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="6c18b-104">Например, рассмотрим следующие XML-документы.</span><span class="sxs-lookup"><span data-stu-id="6c18b-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="6c18b-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="6c18b-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6c18b-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="6c18b-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6c18b-107">Для «Документ1», в процессе вывода создается **набора данных** с именем «DocumentElement» и таблица с именем «Элемент1», так как «Элемент1» является повторяющимся элементом.</span><span class="sxs-lookup"><span data-stu-id="6c18b-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="6c18b-108">**Набор данных:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6c18b-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6c18b-109">**Таблица:** Element1</span><span class="sxs-lookup"><span data-stu-id="6c18b-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6c18b-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="6c18b-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="6c18b-111">Text1</span><span class="sxs-lookup"><span data-stu-id="6c18b-111">Text1</span></span>|  
|<span data-ttu-id="6c18b-112">Text2</span><span class="sxs-lookup"><span data-stu-id="6c18b-112">Text2</span></span>|  
  
 <span data-ttu-id="6c18b-113">Тем не менее, для «Document2», в процессе вывода создается **набора данных** с именем «NewDataSet» и таблица с именем «DocumentElement.»</span><span class="sxs-lookup"><span data-stu-id="6c18b-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="6c18b-114">Element1 выводится в виде столбца, потому что не имеет атрибутов и дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="6c18b-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="6c18b-115">**Набор данных:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="6c18b-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="6c18b-116">**Таблица:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6c18b-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="6c18b-117">Element1</span><span class="sxs-lookup"><span data-stu-id="6c18b-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="6c18b-118">Text1</span><span class="sxs-lookup"><span data-stu-id="6c18b-118">Text1</span></span>|  
  
 <span data-ttu-id="6c18b-119">Эти два XML-документа, возможно, должны были выдавать одну и ту же схему, но процесс вывода дает значительно различающиеся результаты в зависимости от элементов, содержащихся в каждом документе.</span><span class="sxs-lookup"><span data-stu-id="6c18b-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="6c18b-120">Чтобы избежать несоответствий, которые могут произойти при создании схемы из XML-документа, рекомендуется явно задавать схему с помощью языка определения схемы XML (XSD) или XML-Data Reduced (XDR), при загрузке **набора данных** из XML-ФАЙЛ.</span><span class="sxs-lookup"><span data-stu-id="6c18b-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="6c18b-121">Дополнительные сведения о явном задании **набора данных** схему со схемой XML, см. в разделе [наследование реляционной структуры DataSet из схемы XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="6c18b-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c18b-122">См. также</span><span class="sxs-lookup"><span data-stu-id="6c18b-122">See also</span></span>

- [<span data-ttu-id="6c18b-123">Определение реляционной структуры DataSet из XML</span><span class="sxs-lookup"><span data-stu-id="6c18b-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="6c18b-124">Загрузка DataSet из XML</span><span class="sxs-lookup"><span data-stu-id="6c18b-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="6c18b-125">Загрузка сведений о схеме DataSet из XML</span><span class="sxs-lookup"><span data-stu-id="6c18b-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="6c18b-126">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="6c18b-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="6c18b-127">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="6c18b-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="6c18b-128">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c18b-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
