---
title: Метод ICorProfilerInfo2::GetThreadStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8c18935069e4162236f99c411312087ce73bdc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782218"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>Метод ICorProfilerInfo2::GetThreadStaticAddress
Возвращает адрес указанного поля статического потока, который находится в области заданного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a>Параметры  
 `classId`  
 [in] Идентификатор класса, содержащего запрошенный статическое поле потока.  
  
 `fieldToken`  
 [in] Маркер метаданных для запрошенного статического поля потока.  
  
 `threadId`  
 [in] Идентификатор потока, который является областью для запрошенного статического поля.  
  
 `ppAddress`  
 [out] Указатель на адрес статического поля, которое находится в пределах указанного потока.  
  
## <a name="remarks"></a>Примечания  
 `GetThreadStaticAddress` Метод может возвращать одно из следующих:  
  
- HRESULT CORPROF_E_DATAINCOMPLETE, если заданного статические поля не был назначен адрес в заданном контексте.  
  
- Адреса объектов, которые могут быть в куче сбора мусора. Эти адреса могут стать недопустимыми после сборки мусора, поэтому после сборки мусора коллекции профилировщики не должны предполагать, что они являются допустимыми.  
  
 До завершения конструктора класса `GetThreadStaticAddress` возвращает CORPROF_E_DATAINCOMPLETE для всех статических полей, несмотря на то, что некоторые статические поля уже могут быть инициализированы и болея объекты сборки мусора.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Интерфейс ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
