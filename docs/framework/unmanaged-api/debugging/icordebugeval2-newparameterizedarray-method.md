---
title: Метод ICorDebugEval2::NewParameterizedArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988999"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>Метод ICorDebugEval2::NewParameterizedArray
Выделяет новый массив элементов указанного типа и измерений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pElementType`  
 [in] Указатель на интерфейс ICorDebugType объект, представляющий тип элементов, которые хранятся в массиве.  
  
 `rank`  
 [in] Число измерений массива. В платформе .NET Framework версии 2.0 это значение должно быть 1.  
  
 `dims`  
 [in] Размер в байтах каждого измерения массива.  
  
 `lowBounds`  
 [в] Необязательно. Нижняя граница каждого измерения массива. Если это значение указано, для каждого измерения предполагается нижнюю границу, равную нулю.  
  
## <a name="remarks"></a>Примечания  
 Элементы массива могут быть экземпляры универсального типа. Массив всегда создается в домене приложения, в котором поток выполняется в данный момент. В .NET Framework 2.0, значение `rank` должно быть равно 1.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
