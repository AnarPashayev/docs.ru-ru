---
title: Метод ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350221ae205636cef82581f3fe11367006dd8b2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072176"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>Метод ICorProfilerInfo::IsArrayClass
Определяет, является ли указанный класс класса массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Параметры  
 `classId`  
 [in] Идентификатор класса, который необходимо проверить.  
  
 `pBaseElemType`  
 [out] Указатель на значение CorElementType перечисления, указывающее тип элементов массива.  
  
 `pBaseClassId`  
 [out] Указатель на идентификатор класса для элементов массива, если они доступны.  
  
 `pcRank`  
 [out] Указатель на целое число, указывающее ранг (то есть число измерений) массива.  
  
## <a name="remarks"></a>Примечания  
 Если класс является классом массива, `IsArrayClass` метод возвращает значение S_OK HRESULT и значения для всех ненулевых выходных параметров. В противном случае возвращается значение S_FALSE.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
