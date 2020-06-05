---
title: Анализ XML
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3517a0925e886dcd3d2d7860be606c4e44127cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406863"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="a878b-102">Синтаксический анализ XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="a878b-103">Подразделы в данном разделе описывают синтаксический анализ XML-документов.</span><span class="sxs-lookup"><span data-stu-id="a878b-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a878b-104">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="a878b-104">In This Section</span></span>  
  
|<span data-ttu-id="a878b-105">Раздел</span><span class="sxs-lookup"><span data-stu-id="a878b-105">Topic</span></span>|<span data-ttu-id="a878b-106">Описание</span><span class="sxs-lookup"><span data-stu-id="a878b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a878b-107">Руководство. анализ строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-107">How to: Parse a String (Visual Basic)</span></span>](how-to-parse-a-string.md)|<span data-ttu-id="a878b-108">Показывает, как анализировать строку для создания XML-дерева.</span><span class="sxs-lookup"><span data-stu-id="a878b-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="a878b-109">Как загрузить XML из файла (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-109">How to: Load XML from a File (Visual Basic)</span></span>](how-to-load-xml-from-a-file.md)|<span data-ttu-id="a878b-110">Показывает, как загружать XML из URI-кода с помощью метода <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="a878b-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="a878b-111">Сохранение пробелов при загрузке и анализе XML</span><span class="sxs-lookup"><span data-stu-id="a878b-111">Preserving White Space while Loading or Parsing XML</span></span>](preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="a878b-112">Описывает, как управлять поведением пробелов [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] при загрузке XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="a878b-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="a878b-113">Как перехватывать ошибки синтаксического анализа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](how-to-catch-parsing-errors.md)|<span data-ttu-id="a878b-114">Показывает, как выявлять плохо отформатированные или недопустимые коды XML.</span><span class="sxs-lookup"><span data-stu-id="a878b-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="a878b-115">Как создать дерево из XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="a878b-116">Показывает, как создавать XML-дерево непосредственно из <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a878b-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="a878b-117">Последующее: потоковая передача фрагментов XML из XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="a878b-118">Показывает, как организовать поток XML-фрагментов с помощью <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a878b-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="a878b-119">При обработке объемных XML-файлов может оказаться, что загрузка в память всего дерева XML неосуществима.</span><span class="sxs-lookup"><span data-stu-id="a878b-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="a878b-120">Вместо этого можно организовать поток XML-фрагментов.</span><span class="sxs-lookup"><span data-stu-id="a878b-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a878b-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a878b-121">See also</span></span>

- [<span data-ttu-id="a878b-122">Создание деревьев XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a878b-122">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
