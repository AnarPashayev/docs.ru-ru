---
title: Результаты вывода XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f51a657135d9e22d960743b428057e13c1b23804
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590368"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="b610c-102">Результаты вывода XslTransform</span><span class="sxs-lookup"><span data-stu-id="b610c-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="b610c-103">Поскольку таблицы стилей могут определять формат вывода с помощью инструкции `<xsl:output>` с атрибутом `method`, в следующей таблице описан формат вывода при использовании для записи вывода метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> и объявлении этого формата как <xref:System.IO.Stream> или <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b610c-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b610c-104">Класс <xref:System.Xml.Xsl.XslTransform> в версии [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] устарел.</span><span class="sxs-lookup"><span data-stu-id="b610c-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="b610c-105">Можно выполнять XSLT-преобразование, используя класс <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="b610c-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="b610c-106">См. дополнительные сведения об [использовании класса XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) и [миграции из класса XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="b610c-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="b610c-107">Поскольку таблицы стилей могут определять формат вывода с помощью инструкции `<xsl:output>` с атрибутом `method`, в следующей таблице описан формат вывода при использовании для записи вывода метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> и объявлении этого формата как <xref:System.IO.Stream> или <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b610c-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="b610c-108">В следующей таблице показано, что происходит, если тип вывода декларирован методом <xref:System.Xml.Xsl.XslTransform.Transform%2A> в сочетании с инструкцией `<xsl:output>`.</span><span class="sxs-lookup"><span data-stu-id="b610c-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="b610c-109">\<xsl:output method = > attribute</span><span class="sxs-lookup"><span data-stu-id="b610c-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="b610c-110">Формат результата</span><span class="sxs-lookup"><span data-stu-id="b610c-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="b610c-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="b610c-111">method="xml"</span></span>|<span data-ttu-id="b610c-112">XML</span><span class="sxs-lookup"><span data-stu-id="b610c-112">XML</span></span>|  
|<span data-ttu-id="b610c-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="b610c-113">method="html"</span></span>|<span data-ttu-id="b610c-114">HTML</span><span class="sxs-lookup"><span data-stu-id="b610c-114">HTML</span></span>|  
|<span data-ttu-id="b610c-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="b610c-115">method="text"</span></span>|<span data-ttu-id="b610c-116">Text</span><span class="sxs-lookup"><span data-stu-id="b610c-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b610c-117">Примечание. Инструкция `<xsl:output>` пропускается, если выходными данными метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> является <xref:System.Xml.XmlReader> или <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b610c-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b610c-118">Следующие атрибуты поддерживаются, если выходными данными метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> является объект <xref:System.IO.Stream> или <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="b610c-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="b610c-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="b610c-119">encoding\*</span></span>  
  
- <span data-ttu-id="b610c-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="b610c-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="b610c-121">Автономный</span><span class="sxs-lookup"><span data-stu-id="b610c-121">standalone</span></span>  
  
- <span data-ttu-id="b610c-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="b610c-122">doctype-public</span></span>  
  
- <span data-ttu-id="b610c-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="b610c-123">doctype-system</span></span>  
  
- <span data-ttu-id="b610c-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="b610c-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="b610c-125">indent</span><span class="sxs-lookup"><span data-stu-id="b610c-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b610c-126">\*Атрибут encoding пропускается, если метод <xref:System.Xml.Xsl.XslTransform.Transform%2A> отправляет выходные данные в объект <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b610c-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="b610c-127">Вместо него в объекте <xref:System.IO.TextWriter> используется свойство encoding.</span><span class="sxs-lookup"><span data-stu-id="b610c-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="b610c-128">Следующий атрибут пропускается, если выходом метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> является <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b610c-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="b610c-129">Версия: всегда используется версия 1.0</span><span class="sxs-lookup"><span data-stu-id="b610c-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="b610c-130">Тип носителя: используемый тип носителя</span><span class="sxs-lookup"><span data-stu-id="b610c-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="b610c-131">Экранирование специальных символов</span><span class="sxs-lookup"><span data-stu-id="b610c-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="b610c-132">Тег `<xsl:text disable-output-escaping>` используется для указания, следует ли экранировать специальные символы в XML-формате (например, использовать `<&lt>` вместо `"<"`) или оставлять их в текущем состоянии.</span><span class="sxs-lookup"><span data-stu-id="b610c-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="b610c-133">Атрибут `disable-output-escaping` не учитывать при преобразовании в объект <xref:System.Xml.XmlReader> или <xref:System.Xml.XmlWriter> и не влияет на специальные символы.</span><span class="sxs-lookup"><span data-stu-id="b610c-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b610c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="b610c-134">See also</span></span>

- [<span data-ttu-id="b610c-135">Реализация классом XslTransform XSLT-процессора</span><span class="sxs-lookup"><span data-stu-id="b610c-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
