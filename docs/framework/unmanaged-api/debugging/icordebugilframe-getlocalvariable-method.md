---
title: Метод ICorDebugILFrame::GetLocalVariable
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 54ecce830b928ded115233eb99932cc15a471033
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703139"
---
# <a name="icordebugilframegetlocalvariable-method"></a>Метод ICorDebugILFrame::GetLocalVariable

Возвращает значение указанной локальной переменной в кадре стека MSIL.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `dwIndex`  
 окне Индекс локальной переменной в этом кадре стека MSIL.  
  
 `ppValue`  
 [из] Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение.  
  
## <a name="remarks"></a>Комментарии  

 `GetLocalVariable`Метод можно использовать либо в кадре стека MSIL, либо в кадре JIT-компиляции.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
