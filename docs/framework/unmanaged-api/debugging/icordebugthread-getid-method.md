---
title: Метод ICorDebugThread::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8eef616d51febd1b919e0a1936406551f441b98c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987107"
---
# <a name="icordebugthreadgetid-method"></a>Метод ICorDebugThread::GetID
Возвращает идентификатор текущей операционной системы, активной части ICorDebugThread.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pdwThreadId`  
 [out] Идентификатор потока.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор операционной системы может измениться во время выполнения процесса и может быть другое значение для разных частей потока.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
