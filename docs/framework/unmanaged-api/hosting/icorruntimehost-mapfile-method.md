---
title: Метод ICorRuntimeHost::MapFile
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: 60e1d5d49f6f8c6fec060d8751e94410986aa3fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671386"
---
# <a name="icorruntimehostmapfile-method"></a>Метод ICorRuntimeHost::MapFile

Сопоставляет указанный файл с памятью. Этот метод устарел.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `hFile`  
 окне Описатель файла для сопоставления.  
  
 `hMapAddress`  
 заполняет Начальный адрес памяти, с которого начинается сопоставление файла.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE. h  
  
 **Библиотека:** Включается в качестве ресурса в MSCorEE.dll  
  
 **Версия .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorRuntimeHost](icorruntimehost-interface.md)
