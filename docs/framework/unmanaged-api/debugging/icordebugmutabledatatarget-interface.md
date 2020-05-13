---
title: Интерфейс ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: fcf7521f8261c8f8f84c7a9a9deb4b7a7d739c6e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210011"
---
# <a name="icordebugmutabledatatarget-interface"></a>Интерфейс ICorDebugMutableDataTarget
Расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) для поддержки целевых объектов данных.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод ContinueStatusChanged](icordebugmutabledatatarget-continuestatuschanged-method.md)|Изменяет состояние продолжения для незавершенных событий отладки в указанном потоке.|  
|[Метод SetThreadContext](icordebugmutabledatatarget-setthreadcontext-method.md)|Задает контекст (значения регистра) для потока.|  
|[Метод WriteVirtual](icordebugmutabledatatarget-writevirtual-method.md)|Записывает память в адресное пространство целевого процесса.|  
  
## <a name="remarks"></a>Remarks  
 Это расширение интерфейса [ICorDebugDataTarget](icordebugdatatarget-interface.md) может быть реализовано средствами отладки, которые хотят изменить целевой процесс (например, для выполнения динамической отладки).  
  
 Все эти методы являются необязательными в том смысле, что никакая функциональность отладки на основе проверки ядра не будет потеряна, если этот интерфейс не будет реализован или если произойдет сбой вызова этих методов.  Любое свидетельствующее об ошибке значение `HRESULT` из этих методов будет исключаться, как и значение `HRESULT` из вызова метода ICorDebug.  
  
 Обратите внимание, что единственный вызов метода ICorDebug может привести к нескольким изменениям, и механизм гарантированного применения соответствующих изменений в транзакции (все или ничего) не предусмотрен.  Это означает, что в случае сбоя изменения после успешного применения других изменений (для того же вызова ICorDebug) целевой процесс может остаться в несогласованном состоянии, и отладка может оказаться ненадежной.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейсы отладки](debugging-interfaces.md)
- [Отладка](index.md)
