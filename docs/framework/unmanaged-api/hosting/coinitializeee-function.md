---
title: Функция CoInitializeEE
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18f1a4ede1a362860df1271835600e7b867eac00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127768"
---
# <a name="coinitializeee-function"></a>Функция CoInitializeEE
Гарантирует, что ядро выполнения среды выполнения загружается в процесс. Эта функция является устаревшей в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Используйте [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) метод вместо этого.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `fFlags`  
 [in] Один из [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) константы перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает стандартные коды ошибок COM, как определено в файле Winerror.h, а также значения в следующей таблице.  
  
|Код возврата|Описание|  
|-----------------|-----------------|  
|S_OK|Подсистема выполнения была успешно загружена.|  
|S_FALSE|Подсистема выполнения уже загружен.|  
|E_FAIL|Не удалось загрузить подсистему выполнения.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод загружает ядро выполнения, если он не был загружен ранее.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Cor.h  
  
 **Библиотека:** Включена как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Глобальные статические функции метаданных](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
