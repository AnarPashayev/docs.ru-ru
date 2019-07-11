---
title: Метод ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31fad9e82d0b93360f92676f6357c136ae60634a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771132"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>Метод ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
Получает `FunctionID` функции с помощью заданным токеном метаданных, содержащий класс, и `ClassID` значения любого типа аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>Параметры  
 `moduleID`  
 [in] Идентификатор модуля, в которой находится функция.  
  
 `funcDef`  
 [in] `mdMethodDef` Токен метаданных, который ссылается на функцию.  
  
 `classId`  
 [in] Идентификатор содержащего класса функции.  
  
 `cTypeArgs`  
 [in] Число параметров типа для заданной функции. Это значение должно быть ноль для неуниверсальных функциях.  
  
 `typeArgs`  
 [in] Массив `ClassID` значений, каждое из которых является аргументом функции. Значение `typeArgs` может иметь значение NULL, если `cTypeArgs` присваивается нулевое значение.  
  
 `pFunctionID`  
 [out] Указатель на `FunctionID` указанной функции.  
  
## <a name="remarks"></a>Примечания  
 Вызов `GetFunctionFromTokenAndTypeArgs` метод с `mdMethodRef` метаданных, а не `mdMethodDef` токен метаданных может привести к непредсказуемым результатам. Вызывающие объекты должны устранить `mdMethodRef` для `mdMethodDef` при передаче.  
  
 Если функция еще не загружено, вызов метода `GetFunctionFromTokenAndTypeArgs` вызовет загрузки возникает, который является опасной операцией во многих контекстах. Например вызов этого метода во время загрузки модулей или типов может привести к бесконечный цикл, как среда выполнения пытается циклически загружать объекты.  
  
 Как правило, использование `GetFunctionFromTokenAndTypeArgs` не рекомендуется. Если профилировщик интересуют события для определенной функции, их следует хранить `ModuleID` и `mdMethodDef` этой функции, а также использовать [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) проверяемый ли заданный `FunctionID` — для нужной функции.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Интерфейс ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
