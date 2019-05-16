---
title: Функция GetMethod (Справочник по неуправляемым API)
description: Функция GetMethod получает сведения о методе.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419fb33155cfa91199e52110da29efd44d606f4b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636610"
---
# <a name="getmethod-function"></a>Функция GetMethod

Получает сведения об указанном методе.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Параметры

`vFunc`\
[in] Этот параметр не используется.

`ptr`\
[in] Указатель на [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра.

`wszName`\
[in] Имя метода. Этот параметр не может быть `null` и должен указывать на допустимый `LPCWSTR`.

`lFlags`\
[in] Зарезервировано. Этот параметр должен быть 0.

`ppInSignature`\
[out] Указатель на адрес [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляр, описывающий входные параметры метода. Этот параметр учитывается, если он становится равным `null`.

`ppOutSignature`\
[out] Указатель на адрес [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляр, описывающий выходные параметры метода. Этот параметр учитывается, если он становится равным `null`.

## <a name="return-value"></a>Возвращаемое значение

Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:

|Константа  |Значение  |Описание  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Указанное свойство не найден. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Недостаточно памяти для завершения операции. |
|`WBEM_S_NO_ERROR` | 0 | Вызов функции был успешным.  |

## <a name="remarks"></a>Примечания

Эта функция создает оболочку для вызова [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) метод.

Можно установить Windows Management [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) указатель на `null` Если у метода нет входные параметры.

В `ppInSignature` и `ppOutSignature` описывают входным и выходным параметрами, соответственно, в виде свойств `IWbemClassObject` экземпляр системного класса [_Parameters](/windows/desktop/WmiSdk/--parameters). Свойства в `ppInSignature` именуются `Param` *n*, где *n* позиция параметра в сигнатуре метода (такие как `Param1`, `Param2`и т. д.). Свойства в `ppOutSignature` также называются `Param` *n*, и возвращаемое значение имеет имя `ReturnValue`. Дополнительные сведения и пример см. в разделе [IWbemClassObject::GetMethod метод](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).

**Заголовок.** WMINet_Utils.idl

**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>См. также

- [WMI и счетчики производительности (Справочник по неуправляемым API)](index.md)
