---
title: Метод ICorProfilerInfo2::GetGenerationBounds
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791694"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>Метод ICorProfilerInfo2::GetGenerationBounds
Получает области памяти, которые являются сегментами кучи, составляющими разные поколения сборки мусора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Параметры  
 `cObjectRanges`  
 [in] Количество элементов, выделенных вызывающим объектом для массива `ranges`.  
  
 `pcObjectRanges`  
 [out] Указатель на целое число, задающее общее число диапазонов, некоторые или все из которых будут возвращены в массиве `ranges`.  
  
 `ranges`  
 [out] Массив [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) структуры, каждый из которых описывает диапазон (блок) памяти в поколении, для которого выполняется сборка мусора.  
  
## <a name="remarks"></a>Примечания  
 Метод `GetGenerationBounds` может быть вызван из любого обратного вызова профилировщика при условии, что в этот момент не выполняется сборка мусора. То есть он может вызываться из любого обратного вызова, за исключением тех, которые происходят между [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) и [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Большинство смещений поколений происходит во время сборки мусора. Поколения могут увеличиваться между сборками мусора, но обычно не перемещаются. Таким образом, наиболее интересные места вызова метода `GetGenerationBounds` — `ICorProfilerCallback2::GarbageCollectionStarted` и `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 При запуске программы некоторые объекты выделяются самой средой (CLR), обычно в поколениях 3 и 0. Таким образом, к моменту начала выполнения управляемого кода эти поколения уже будут содержать объекты. Поколения 1 и 2 обычно оказываются пустыми, разве что кроме фиктивных объектов, созданных сборщиком мусора. (Размер фиктивных объектов составляет 12 байт в 32-разрядных реализациях среды CLR; в 64-разрядных реализациях размер больше). Вы также можете видеть диапазоны поколения 2, которые находятся внутри модулей, созданных генератором образов в машинном коде (NGen.exe). В этом случае объекты в поколении 2 являются *замороженными объектами*, которые выделяются при выполнении NGen.exe, а не сборщиком мусора.  
  
 Эта функция использует буферы, выделенные вызывающим объектом.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Интерфейс ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Интерфейсы профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Профилирование](../../../../docs/framework/unmanaged-api/profiling/index.md)
