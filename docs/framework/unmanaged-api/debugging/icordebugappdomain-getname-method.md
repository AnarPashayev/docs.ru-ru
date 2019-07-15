---
title: Метод ICorDebugAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 535d94688d02a7315529d17fae555fba457bbb86
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737872"
---
# <a name="icordebugappdomaingetname-method"></a>Метод ICorDebugAppDomain::GetName
Возвращает имя домена приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `cchName`  
 [in] Размер массива `szName`. Это значение равно нулю, чтобы поместить этот метод в режиме запроса.  
  
 `pcchName`  
 [out] Указатель на размер имени или количество символов, фактически возвращенных в `szName`. В режиме запроса, это значение позволяет вызывающему объекту знать размер буфера для выделения для имени.  
  
 `szName`  
 [out] Массив, в котором хранится имя домена приложения.  
  
## <a name="remarks"></a>Примечания  
 Отладчик вызывает `GetName` метод один раз, чтобы получить размер буфера, который необходим для имени. Отладчик выделяет буфер и затем вызывает метод во второй раз для заполнения буфера. Первый вызов, чтобы получить размер имени, называется *режим запроса*.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
