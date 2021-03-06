---
title: Преобразования XSLT
ms.date: 03/30/2017
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 686b2d454eda99095bcb335c8b0edba9ecf2e304
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685062"
---
# <a name="xslt-transformations"></a>Преобразования XSLT

Язык XSLT позволяет преобразовать содержимое исходного XML-документа в другой документ, отличный по формату или структуре. Например, с помощью XSLT можно преобразовать XML в HTML для использования на веб-узле или преобразовать в документ, в котором будут только поля, необходимые приложению. Этот процесс преобразования описывается в [документации консорциума W3C по преобразованиям XSLT версии 1.0](https://www.w3.org/TR/xslt-10/).  
  
 Класс <xref:System.Xml.Xsl.XslCompiledTransform> является обработчиком XSLT в платформе .NET. Класс <xref:System.Xml.Xsl.XslCompiledTransform> поддерживает [рекомендации W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
> Класс <xref:System.Xml.Xsl.XslTransform> в платформе .NET Framework версии 2.0 является устаревшим. Класс <xref:System.Xml.Xsl.XslCompiledTransform> является новой реализацией обработчика XSLT. Улучшена его производительность и добавлены новые средства безопасности. XSLT-приложения рекомендуется создавать с помощью класса <xref:System.Xml.Xsl.XslCompiledTransform>  
  
## <a name="in-this-section"></a>В этом разделе  

 [Использование класса XslCompiledTransform](using-the-xslcompiledtransform-class.md)  
 Содержит сведения об использовании класса <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Миграция с класса XslTransform](migrating-from-the-xsltransform-class.md)  
 Обсуждается перенос кода из класса <xref:System.Xml.Xsl.XslTransform>.  
  
 [Компилятор XSLT (xsltc.exe)](xslt-compiler-xsltc-exe.md)  
 Предоставляются сведения об использовании XSLT-компилятора.  
  
 [XSLT-преобразования с помощью класса XslTransform](xslt-transformations-with-the-xsltransform-class.md)  
 Содержит сведения об использовании класса <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="reference"></a>Справочник  

 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Связанные разделы  

 [XML-документы и данные](index.md)
