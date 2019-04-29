---
title: Перечисление AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790108"
---
# <a name="assemblyoptions-enumeration"></a>Перечисление AssemblyOptions
Перечисляет параметры сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Поля  
  
|Поле|Описание|  
|-----------|-----------------|  
|optAssemTitle|Строка — определяет название сборки.|  
|optAssemDescription|Строка — содержит описание сборки.|  
|optAssemConfig|Строка — содержит конфигурацию сборки.|  
|optAssemOS|Строка - кодировке: «dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion».|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Строка — содержит языковой стандарт сборки.|  
|optAssemVersion|Строка - кодировке: «Основная.дополнительная.сборка.редакция».|  
|optAssemCompany|Строка — содержит компании.|  
|optAssemProduct|Строка — содержит имя продукта.|  
|optAssemProductVersion|Строка (также известный как InformationalVersion).|  
|optAssemCopyright|Строка — содержит сведения об авторских правах.|  
|optAssemTrademark|Строка — содержит сведения о товарном знаке.|  
|optAssemKeyFile|String (имя файла).|  
|optAssemKeyName|Строка (имя ключа).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (также известен как DelaySign).|  
|optAssemFileVersion|Строка - кодируется как «Основная.дополнительная.сборка.редакция»--так же, как ProductVersion.|  
|optAssemSatelliteVer|Строка - кодируется как «Основная.дополнительная.сборка.редакция».|  
|optLastAssemOption|Счетчик числа элементов.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** alink.h  
  
 **Библиотека**: alink.dll  
  
## <a name="see-also"></a>См. также

- [Al.exe (компоновщик сборок)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
