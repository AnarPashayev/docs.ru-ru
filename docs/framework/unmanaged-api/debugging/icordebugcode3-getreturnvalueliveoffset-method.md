---
title: Метод ICorDebugCode3::GetReturnValueLiveOffset
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 6153ebf24ae939a50d71cad2d4323090aa905851
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720819"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>Метод ICorDebugCode3::GetReturnValueLiveOffset

Для указанного смещения IL получает машинные смещения, в которых должна быть помещена точка останова, чтобы отладчик мог получить возвращаемое значение из функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `ILoffset`  
 Смещение IL. Это должен быть сайт вызова функции, иначе вызов функции завершится ошибкой.  
  
 `bufferSize`  
 Число байтов, доступных для хранения `pOffsets` .  
  
 `pFetched`  
 Указатель на число фактически возвращенных смещений. Обычно его значение равно 1, но одна инструкция IL может сопоставляться с несколькими `CALL` инструкциями сборки.  
  
 `pOffsets`  
 Массив смещений машинного кода. Как правило, `pOffsets` содержит одно смещение, хотя одна инструкция il может сопоставляться с несколькими инструкциями сборки по нескольким схемам `CALL` .  
  
## <a name="remarks"></a>Комментарии  

 Этот метод используется вместе с методом [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) для получения возвращаемого значения метода, возвращающего ссылочный тип. Передача смещения IL на сайт вызова функции в этот метод возвращает одно или несколько исходных смещений. Затем отладчик может установить точки останова для этих собственных смещений в функции. Когда отладчик обращается к одной из точек останова, можно передать то же смещение IL, которое вы передали этому методу методу [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) , чтобы получить возвращаемое значение. Затем отладчик должен очистить все заданные точки останова.  
  
> [!WARNING]
> `ICorDebugCode3::GetReturnValueLiveOffset`Методы и [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) позволяют получать сведения о возвращаемых значениях только для ссылочных типов. Получение сведений о возвращаемых значениях из типов значений (то есть все типы, производные от <xref:System.ValueType> ) не поддерживаются.  
  
 Функция возвращает значения, `HRESULT` показанные в следующей таблице.  
  
|Значение `HRESULT`|Описание|  
|---------------------|-----------------|  
|`S_OK`|Успешно.|  
|`CORDBG_E_INVALID_OPCODE`|Указанный сайт смещения IL не является инструкцией вызова, или функция возвращает `void` .|  
|`CORDBG_E_UNSUPPORTED`|Данное смещение IL является правильным вызовом, но возвращаемый тип не поддерживается для получения возвращаемого значения.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset`Метод доступен только в системах на базе x86 и AMD64.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Метод GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [Интерфейс ICorDebugCode3](icordebugcode3-interface.md)
