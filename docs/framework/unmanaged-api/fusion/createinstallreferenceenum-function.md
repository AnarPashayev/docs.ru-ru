---
title: Функция CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da77d2eb848419c35e57ffacc8bf3d4580106fa5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764327"
---
# <a name="createinstallreferenceenum-function"></a>Функция CreateInstallReferenceEnum
Возвращает указатель на [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) экземпляр, который представляет список ссылок на приложения для указанной сборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Параметры  
 `ppRefEnum`  
 [out] Возвращенный `IInstallReferenceEnum` указатель.  
  
 `pName`  
 [in] [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) , определяющий сборку, для которого необходимо перечислить ссылки.  
  
 `dwFlags`  
 [in] Флаги, которые влияют на поведение перечислителя.  
  
 `pvReserved`  
 [in] Зарезервировано для будущего расширения. `pvReserved` должен быть пустой ссылкой.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Fusion.h  
  
 **Библиотека:** Fusion.dll и "Mscorwks.dll". Используйте Fusion.dll вместо "Mscorwks.dll", чтобы обеспечить целевых правильную версию платформы .NET Framework.  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [Интерфейс IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Глобальные статические функции Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
