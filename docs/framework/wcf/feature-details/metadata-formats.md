---
title: Форматы метаданных
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 55f68f4b56e50b19da19ecc941e9ec537b846006
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038575"
---
# <a name="metadata-formats"></a>Форматы метаданных
Windows Communication Foundation (WCF) поддерживает форматы метаданных в следующей таблице.  
  
## <a name="metadata-specifications-and-usage"></a>Спецификации и использование метаданных  
  
|Протокол|Спецификация и использование|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF использует язык описания веб-служб (WSDL) для описания служб.|  
|схема XML|[XML Schema Part 2: DataTypes Second Edition](https://go.microsoft.com/fwlink/?LinkId=94861) и [XML Schema Part 1: Структуры, второе издание](https://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF использует схему XML для описания типов данных, используемых в сообщениях.|  
|WS Policy|[Web Services Policy 1.2 - платформа (WS-Policy)](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Web Services Policy 1.5 - платформа](https://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF использует WS-Policy 1.2 или 1.5 спецификации с доменными утверждениями для описания требований и возможностей служб.|  
|Вложения WS Policy|[Web Services Policy 1.2 - вложение (WS-PolicyAttachment)](https://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> В WCF реализована вложениями WS-Policy для прикрепления выражений политики в различных областях на языке WSDL.|  
|WS Metadata Exchange|[Web Services Metadata Exchange (WS-MetadataExchange) версии 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> В WCF реализована WS-MetadataExchange для извлечения схемы XML, WSDL и WS-Policy.|  
|Привязка WS Addressing для WSDL|[Web Services Addressing 1.0 - привязка WSDL](https://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> В WCF реализована привязки WS-Addressing для WSDL для вложения сведений об адресации в WSDL.|  
  
## <a name="see-also"></a>См. также

- [Протоколы веб-служб, поддерживаемые предоставляемыми системой привязками](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL и политика](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
