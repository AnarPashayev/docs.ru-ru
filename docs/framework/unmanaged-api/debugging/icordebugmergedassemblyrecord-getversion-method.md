---
title: Метод ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb7861e33a02b994c4c29569a811f4e2f3c44cec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762307"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Метод ICorDebugMergedAssemblyRecord::GetVersion
Возвращает сведения о версии сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pMajor`  
 [out] Указатель на основной номер версии.  
  
 `pMinor`  
 [out] Указатель на дополнительный номер версии.  
  
 `pBuild`  
 [out] Указатель на номер сборки.  
  
 `pRevision`  
 [out] Указатель на номер редакции.  
  
## <a name="remarks"></a>Примечания  
 Сведения о версии сборки см в разделе, посвященном классу <xref:System.Version>.  
  
> [!NOTE]
>  Этот метод доступен только в машинном коде .NET.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
