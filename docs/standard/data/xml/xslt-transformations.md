---
title: Преобразования XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 4bbecfbf1b163a9d7bfe6957806095b5b17fbab7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709638"
---
# <a name="xslt-transformations"></a><span data-ttu-id="ed708-102">Преобразования XSLT</span><span class="sxs-lookup"><span data-stu-id="ed708-102">XSLT Transformations</span></span>
<span data-ttu-id="ed708-103">Язык XSLT позволяет преобразовать содержимое исходного XML-документа в другой документ, отличный по формату или структуре.</span><span class="sxs-lookup"><span data-stu-id="ed708-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="ed708-104">Например, с помощью XSLT можно преобразовать XML в HTML для использования на веб-узле или преобразовать в документ, в котором будут только поля, необходимые приложению.</span><span class="sxs-lookup"><span data-stu-id="ed708-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="ed708-105">Этот процесс преобразования описывается в [документации консорциума W3C по преобразованиям XSLT версии 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="ed708-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="ed708-106">Класс <xref:System.Xml.Xsl.XslCompiledTransform> является обработчиком XSLT в платформе .NET.</span><span class="sxs-lookup"><span data-stu-id="ed708-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="ed708-107">Класс <xref:System.Xml.Xsl.XslCompiledTransform> поддерживает [рекомендации W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="ed708-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed708-108">Класс <xref:System.Xml.Xsl.XslTransform> в платформе .NET Framework версии 2.0 является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="ed708-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="ed708-109">Класс <xref:System.Xml.Xsl.XslCompiledTransform> является новой реализацией обработчика XSLT.</span><span class="sxs-lookup"><span data-stu-id="ed708-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="ed708-110">Улучшена его производительность и добавлены новые средства безопасности.</span><span class="sxs-lookup"><span data-stu-id="ed708-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="ed708-111">XSLT-приложения рекомендуется создавать с помощью класса <xref:System.Xml.Xsl.XslCompiledTransform></span><span class="sxs-lookup"><span data-stu-id="ed708-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed708-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="ed708-112">In This Section</span></span>  
 [<span data-ttu-id="ed708-113">Использование класса XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="ed708-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ed708-114">Содержит сведения об использовании класса <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="ed708-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="ed708-115">Миграция с класса XslTransform</span><span class="sxs-lookup"><span data-stu-id="ed708-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="ed708-116">Обсуждается перенос кода из класса <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="ed708-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="ed708-117">Компилятор XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="ed708-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="ed708-118">Предоставляются сведения об использовании XSLT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="ed708-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="ed708-119">XSLT-преобразования с помощью класса XslTransform</span><span class="sxs-lookup"><span data-stu-id="ed708-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="ed708-120">Содержит сведения об использовании класса <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="ed708-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ed708-121">Справочные сведения</span><span class="sxs-lookup"><span data-stu-id="ed708-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="ed708-122">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="ed708-122">Related Sections</span></span>  
 [<span data-ttu-id="ed708-123">XML-документы и данные</span><span class="sxs-lookup"><span data-stu-id="ed708-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
