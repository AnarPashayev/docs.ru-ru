---
title: Метод ICorDebugInstanceFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: c4b193b45e30b0eba3367f18cb1e4c2b4e108fa8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724914"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a>Метод ICorDebugInstanceFieldSymbol::GetSize

Получает размер поля экземпляра в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `pcbSize`  
 [out] Указатель на длину этого поля.  
  
## <a name="remarks"></a>Комментарии  
  
> [!NOTE]
> Этот метод доступен только в машинном коде .NET.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)
- [Интерфейсы отладки](debugging-interfaces.md)
