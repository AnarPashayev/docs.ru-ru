---
title: Структура FUSION_INSTALL_REFERENCE
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688813"
---
# <a name="fusion_install_reference-structure"></a>Структура FUSION_INSTALL_REFERENCE

Представляет ссылку, которую приложение делает с сборкой, установленной приложением в глобальном кэше сборок.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`cbSize`|Размер структуры в байтах.|  
|`dwFlags`|Зарезервировано для будущего расширения. Это значение должно быть равно 0 (нулю).|  
|`guidScheme`|Сущность, которая добавляет ссылку. Это поле может иметь одно из следующих значений:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: на сборку ссылается приложение, которое было установлено с помощью Microsoft установщик Windows. `szIdentifier`Поле имеет значение `MSI` , а `szNonCanonicalData` поле имеет значение `Windows Installer` . Эта схема используется для параллельных сборок Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: на сборку ссылается приложение, которое отображается в интерфейсе " **Установка и удаление программ** ". `szIdentifier`Поле предоставляет маркер, регистрирующий приложение с помощью интерфейса « **Установка и удаление программ** ».<br />-FUSION_REFCOUNT_FILEPATH_GUID. на сборку ссылается приложение, представленное файлом в файловой системе. `szIdentifier`Поле предоставляет путь к этому файлу.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: на сборку ссылается приложение, представленное только непрозрачной строкой. `szIdentifier`Поле предоставляет эту непрозрачную строку. Глобальный кэш сборок не проверяет наличие непрозрачных ссылок при удалении этого значения.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: это значение зарезервировано.|  
|`szIdentifier`|Уникальная строка, идентифицирующая приложение, которое установило сборку в глобальный кэш сборок. Его значение зависит от значения `guidScheme` поля.|  
|`szNonCanonicalData`|Строка, понятная только сущности, которая добавляет ссылку. Глобальный кэш сборок хранит эту строку, но не использует ее.|  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** Fusion. h  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Структуры Fusion](fusion-structures.md)
- [Глобальный кэш сборок](../../app-domains/gac.md)
