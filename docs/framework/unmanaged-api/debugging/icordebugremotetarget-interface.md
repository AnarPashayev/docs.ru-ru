---
title: Интерфейс ICorDebugRemoteTarget
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197325"
---
# <a name="icordebugremotetarget-interface"></a>Интерфейс ICorDebugRemoteTarget
Предоставляет методы, позволяющие разработчикам отлаживать приложения на основе Silverlight в среде CLR (CLR).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод ICorDebugRemoteTarget::GetHostName](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Возвращает имя узла или IP-адрес удаленного компьютера.|  
  
## <a name="remarks"></a>Примечания  
 Отладка в смешанном режиме (то есть управляемого и машинного кода) не поддерживается в Windows 95, Windows 98 или Windows ME или на платформах, отличных от — x86 (например, IA-64 и AMD64).  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl  
  
 **Библиотека:** : CorGuids.lib  
  
 **Версии платформы .NET framework:** 3.5 с пакетом обновления 1 (SP1)  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [Интерфейс ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
