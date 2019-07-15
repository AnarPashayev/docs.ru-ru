---
title: Метод ICorProfilerInfo::GetInprocInspectionInterface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780568"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>Метод ICorProfilerInfo::GetInprocInspectionInterface
Возвращает объект, который можно запросить для интерфейса «ICorDebugProcess». Этот метод является устаревшим в .NET Framework версии 2.0.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Параметры  
 `ppicd`  
 [out](/cpp/atl/iunknown) объект, который можно запросить для `ICorDebugProcess` интерфейс.  
  
## <a name="remarks"></a>Примечания  
 Общеязыковой среды выполнения (CLR), API отладки поддерживается только в процессе отладки в .NET Framework версии 1.0. В процессе отладки включить профилировщик для использования для проверки часть API отладки. В результате отзывов в процессе отладки удален из .NET Framework версии 2.0 и заменены набором функциональных возможностей, которые лучше соответствуют API профилирования.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** 1.0  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
