---
title: Функция _EFN_StackTrace
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0074584ee5baba358db5bf3b0f2cfdd9a3d8f1d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593541"
---
# <a name="efnstacktrace-function"></a>Функция _EFN_StackTrace
Предоставляет текстовое представление трассировки управляемого стека и массив записей `CONTEXT`, по одной для каждого перехода между неуправляемым и управляемым кодом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `Client`  
 [in] Клиент, для которого выполняется отладка.  
  
 `wszTextOut`  
 [out] Текстовое представление трассировки стека.  
  
 `puiTextLength`  
 [out] Указатель на число символов в `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Массив контекстов перехода.  
  
 `puiTransitionContextCount`  
 [out] Указатель на число контекстов перехода в массиве.  
  
 `uiSizeOfContext`  
 [in] Размер структуры контекста.  
  
 `Flags`  
 [in] Значение 0 или SOS_STACKTRACE_SHOWADDRESSES (0x01) для отображения регистр EBP и указатель стека ввод (ESP), перед каждым `module!functionname` строки.  
  
## <a name="remarks"></a>Примечания  
 `_EFN_StackTrace` Структуры, которые могут вызываться из WinDbg программный интерфейс. Параметры используются следующим образом:  
  
- Если `wszTextOut` имеет значение null и `puiTextLength` — не равно null, функция возвращает длину строки в `puiTextLength`.  
  
- Если `wszTextOut` — не равно null, функция сохраняет текст в `wszTextOut` до местоположения, указанного параметром `puiTextLength`. Успешно возвращается, если было достаточно места в буфере, или возвращает значение E_OUTOFMEMORY, если буфер недостаточно длинный.  
  
- Переход части функции учитывается, если `pTransitionContexts` и `puiTransitionContextCount` оба имеют значение null. В этом случае функция предоставляет вызывающим объектам с помощью текстовых выходных данных только имена функций.  
  
- Если `pTransitionContexts` имеет значение null и `puiTransitionContextCount` — не равно null, функция возвращает необходимое количество записей контекста в `puiTransitionContextCount`.  
  
- Если `pTransitionContexts` — не равно null, функция воспринимает его как массив структур длины `puiTransitionContextCount`. Задается размер структуры `uiSizeOfContext`, и должен быть размер [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) или `CONTEXT` для архитектуры.  
  
- `wszTextOut` записывается в следующем формате:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Если смещение в шестнадцатеричном формате 0x0, смещение не записывается.  
  
- Если отсутствует управляемый код в потоке в данный момент в контексте, функция возвращает значение SOS_E_NOMANAGEDCODE.  
  
- `Flags` Параметр имеет значение 0, или SOS_STACKTRACE_SHOWADDRESSES, чтобы увидеть EBP и ESP перед каждым `module!functionname` строки. По умолчанию — 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** SOS_Stacktrace.h  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Глобальные статические функции отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
