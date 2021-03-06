---
title: Схема веб-параметров
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: c3ac9b42aeff3f7b26f0b36480bc75ceda39e7e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185604"
---
# <a name="web-settings-schema"></a>Схема веб-параметров

Веб-параметры определяют настройки ЦП и настройки ASP.NET на уровне выполнения, которые относятся к поведению процессов, управляемых уровнем размещения ASP.NET. Эти параметры отличаются от параметров типа домена приложения, которые задаются в файле Web.config приложения ASP.NET.  
  
Веб-параметры содержатся в файлах Aspnet.config, которые находятся в папках установки версий .NET Framework. Например, файл Aspnet.config для .NET Framework 2,0 находится в следующей папке:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Веб-параметры не используются в других файлах конфигурации, таких как файл machine.config, корневой файл Web.config или файлы Web.config уровня приложения.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|Элемент|Описание|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Содержит сведения, используемые уровнем размещения ASP.NET.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Определяет настройки ЦП и настройки ASP.NET на уровне выполнения, которые относятся к поведению процессов, управляемых уровнем размещения ASP.NET.|  
  
## <a name="see-also"></a>См. также

- [Схема файла конфигурации](../index.md)
