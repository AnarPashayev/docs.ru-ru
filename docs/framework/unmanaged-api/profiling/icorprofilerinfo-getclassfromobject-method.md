---
title: Метод ICorProfilerInfo::GetClassFromObject
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81afb9b40269b04a59c54636c7e88c1f67189593
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189551"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a>Метод ICorProfilerInfo::GetClassFromObject
Получает `ClassID` объекта, учитывая его `ObjectID`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a>Параметры  
 `objectId`  
 [in] Идентификатор объекта, для которого необходимо получить `ClassID`.  
  
 `pClassId`  
 [out] Указатель на возвращенный `ClassID`.  
  
## <a name="remarks"></a>Примечания  
 Значение null `pClassId` указывает, что `objectId` имеет тип, который выгружается.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
