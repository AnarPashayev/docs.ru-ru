---
title: Структура COR_PRF_FUNCTION_ARGUMENT_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dffefedf14d5f219736e429be191021b2de7ddd2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599329"
---
# <a name="corprffunctionargumentrange-structure"></a>Структура COR_PRF_FUNCTION_ARGUMENT_RANGE
Представляет блок аргументов функции, которые сохраняются в памяти последовательно слева направо.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a>Участники  
  
|Участники|Описание|  
|-------------|-----------------|  
|`startAddress`|Начальный адрес блока.|  
|`length`|Длина непрерывного блока.|  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Структуры профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
