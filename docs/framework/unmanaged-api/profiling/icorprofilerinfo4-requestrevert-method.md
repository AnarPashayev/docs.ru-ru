---
title: Метод ICorProfilerInfo4::RequestRevert
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92137e1a5b0923bc34745513715934c483616700
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179846"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>Метод ICorProfilerInfo4::RequestRevert
Восстанавливает исходные версии всех экземпляров указанных функций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Параметры  
 `cFunctions`  
 [in] Число функций для восстановления.  
  
 `moduleIds`  
 [in] Указывает часть `moduleId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.  
  
 `methodIds`  
 [in] Указывает часть `methodId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.  
  
 `status`  
 [out] Массив значений HRESULT, перечисленных в разделе «Значения HRESULT для состояния» далее в этом разделе. Каждое значение HRESULT указывает успех или сбой попытки восстановления исходного состояния каждой функции, указанной в параллельных массивах `moduleIds` и `methodIds`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|Была предпринята попытка восстановления исходного состояния всех запросов; однако необходимо проверить массив возвращенных состояний, чтобы определить, какие функции были успешно восстановлены.|  
|CORPROF_E_CALLBACK4_REQUIRED|Профилировщик должен реализовать [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) интерфейс для этого вызова, которые должны поддерживаться.|  
|CORPROF_E_REJIT_NOT_ENABLED|Перекомпиляция JIT не была включена. Необходимо включить перекомпиляцию JIT во время инициализации с помощью [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) метод, чтобы задать `COR_PRF_ENABLE_REJIT` флаг.|  
|E_INVALIDARG|`cFunctions` имеет значение 0, или `moduleIds` или `methodIds` является `NULL`.|  
|E_OUTOFMEMORY|Среде CLR не удалось выполнить запрос, поскольку не хватило памяти.|  
  
## <a name="status-hresults"></a>Значения HRESULT для состояния  
  
|Массив значений HRESULT для состояния|Описание|  
|--------------------------|-----------------|  
|S_OK|Соответствующая функция была успешно возвращена.|  
|E_INVALIDARG|Значение параметра `moduleID` или параметра `methodDef` — `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Модуль еще не полностью загружен или находится в процессе выгрузки.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Указанный модуль был создан динамически (например, с помощью `Reflection.Emit`). Поэтому он не поддерживается данным методом.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Среде CLR не удалось восстановить исходное состояние указанной функции, так как не найден соответствующий активный запрос перекомпиляции. Либо эта перекомпиляция никогда не запрашивалась, либо функция уже была восстановлена.|  
|Другое|Операционная система возвратила сбой за пределами среды CLR. Например, в случае сбоя системного вызова изменения защиты доступа к странице памяти будет отображаться ошибка операционной системы.|  
  
## <a name="remarks"></a>Примечания  
 При следующем вызове любой из восстановленных функций будет запускаться исходная версия этой функции. Если функция уже выполняется, то будет завершено выполнение запущенной версии.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Профилирующие интерфейсы](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Профилирование](../../../../docs/framework/unmanaged-api/profiling/index.md)
