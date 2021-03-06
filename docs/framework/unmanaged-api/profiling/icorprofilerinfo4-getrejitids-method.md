---
title: Метод ICorProfilerInfo4::GetReJITIDs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: 2ac645cbaaa45554568874653be016e4691bbd2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707481"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>Метод ICorProfilerInfo4::GetReJITIDs

Возвращает массив идентификаторов, которые определяют все все повторно скомпилированные версии указанной функции, которые все еще выделены. Сюда входят JIT-повторно скомпилированные версии функций, которые впоследствии были отменены, но еще не освобождены (например, если домен приложения, содержащий функцию, которая содержит возвращенные функции, все еще используется).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Параметры  

 `functionId`  
 окне Объект `FunctionID` экземпляра функции, для которого требуется перечислить версии.  
  
 `cReJitIds`  
 окне Число идентификаторов, перекомпилированных с помощью JIT-компилятора, выделенных в `reJitIds` массиве.  
  
 `pcReJitIds`  
 заполняет Фактическое число повторно скомпилированных идентификаторов с JIT-рекомпиляцией.  
  
 `reJitIds`  
 заполняет Выделенный вызывающим объектом массив, который будет содержать JIT-перекомпилированные идентификаторы для указанной функции.  
  
## <a name="remarks"></a>Комментарии  

 `GetReJITIDs` Перечисляет активные JIT-повторно скомпилированные идентификаторы для заданного экземпляра функции. Он следует той же схеме использования, что и другие `ICorProfilerInfo` функции, принимающие буферы, выделенные вызывающим объектом.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo4](icorprofilerinfo4-interface.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Профилирование](index.md)
