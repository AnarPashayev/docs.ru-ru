---
title: Метод ICorProfilerInfo::GetModuleInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69db53c03d68e30507ff3ab2b11b663970d59af0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090814"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>Метод ICorProfilerInfo::GetModuleInfo
Возвращает имя файла модуля и идентификатор его родительской сборки для указанного идентификатора модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a>Параметры  
 `moduleId`  
 [in] Идентификатор модуля, для которого будут извлекаться сведения.  
  
 `ppBaseLoadAddress`  
 [out] Базовый адрес, по которому модуль был загружен.  
  
 `cchName`  
 [in] Длина буфера возврата `szName` в символах.  
  
 `pcchName`  
 [out] Указатель на общую длину возвращаемого имени файла модуля в символах.  
  
 `szName`  
 [out] Буфер расширенных символов, предоставленный вызывающим объектом. При возврате метода этот буфер содержит имя файла модуля.  
  
 `pAssemblyId`  
 [out] Указатель на идентификатор родительской сборки модуля.  
  
## <a name="remarks"></a>Примечания  
 Для динамических модулей параметр `szName` является пустой строкой, а базовый адрес равен 0 (нулю).  
  
 Несмотря на то что `GetModuleInfo` метод может вызываться сразу же существует идентификатор модуля, идентификатор родительской сборки будет недоступен до получения профилировщиком [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) обратного вызова.  
  
 После возврата метода `GetModuleInfo` необходимо убедиться, что буфер `szName` был достаточно велик, чтобы вместить в себя полное имя файла модуля. Для этого сравните значение, на которое указывает параметр `pcchName`, со значением параметра `cchName`. Если параметр `pcchName` указывает на значение, превышающее значение `cchName`, выделите буфер `szName` большего размера, обновите параметр `cchName`, задав новый, больший размер, и вызовите метод `GetModuleInfo` снова.  
  
 Кроме того, сначала можно вызвать метод `GetModuleInfo` с буфером `szName` нулевой длины для получения правильного размера буфера. Затем можно задать размер буфера равным значению, возвращенному в параметре `pcchName`, и вызвать метод `GetModuleInfo` снова.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Профилирующие интерфейсы](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Профилирование](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [Метод GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
