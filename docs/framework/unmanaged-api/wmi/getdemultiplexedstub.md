---
title: Функция GetDemultiplexedStub (Справочник по неуправляемым API)
description: Функция GetDemultiplexedStub создает приемник объект сервера пересылки для помощи в получении асинхронных вызовов из системы управления Windows клиента.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 872164e2f48f1ef234b729b28aa9b1af1589c0fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180950"
---
# <a name="getdemultiplexedstub-function"></a>Функция GetDemultiplexedStub
Создает приемник переадресации объекта, который помогает клиенту получать асинхронные вызовы из службы управления Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Параметры

`pObject`  
[in] Указатель на реализацию в процессе клиента [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[in] Флаг, указывающий, является ли событие локального (`true`); в противном случае `false`.

`ppObject`  
[out] Сервер пересылки приемника объектов, для помощи в получении асинхронных вызовов из системы управления Windows клиента.

## <a name="return-value"></a>Возвращаемое значение

Если функция выполняется успешно, возвращаемое значение равно `S_OK` (0).

Если функция завершается с ошибкой, возвращается код ошибки. Чтобы получить расширенные сведения об ошибке, вызовите [GetErrorInfo](geterrorinfo.md) функции.
    
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** WMINet_Utils.idl  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>См. также

- [WMI и счетчики производительности (Справочник по неуправляемым API)](index.md)
