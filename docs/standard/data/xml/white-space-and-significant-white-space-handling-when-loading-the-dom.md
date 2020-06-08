---
title: Обработка незначительных и значительных пробелов при загрузке DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 520d965737b82fda082aa44029f2a4042d948deb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281781"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Обработка незначительных и значительных пробелов при загрузке DOM
При загрузке документа можно установить параметр, требующий сохранять пробелы и создавать узлы **XmlWhitespace** в дереве документа. Чтобы создавать узлы пробелов, задайте для свойства **PreserveWhitespace** значение true. Если свойство имеет значение **false**, используемое по умолчанию, то узлы пробелов не создаются. Узлы существенных пробелов сохраняются всегда, и узлы **XmlSignificantWhitespace** всегда создаются в памяти для представления этих данных, независимо от значения флага **PreserveWhitespace**.  
  
 Если документ загружается из средства чтения, то свойства флага **PreserveWhitespace** для класса **XmlDocument** влияют на создание узлов **XmlWhitespace** только в том случае, когда свойство **WhitespaceHandling** для **XmlTextReader** не имеет значения **WhitespaceHandling.None**. Значение свойства **WhitespaceHandling** в средстве чтения имеет приоритет над значением этого флага для **XmlDocument**. Дополнительные сведения о флаге **XmlSignificantWhitespace** см. в статье <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>См. также

- [Модель объектов документов XML (DOM)](xml-document-object-model-dom.md)
