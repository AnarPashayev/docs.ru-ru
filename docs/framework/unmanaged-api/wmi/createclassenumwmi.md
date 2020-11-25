---
title: Функция Креатеклассенумвми (Справочник по неуправляемым API)
description: Функция Креатеклассенумвми Возвращает перечислитель для всех классов, удовлетворяющих заданным условиям.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b80954e288f6720c75d0af0b8af083fa4856754
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719740"
---
# <a name="createclassenumwmi-function"></a>Функция CreateClassEnumWmi

Возвращает перечислитель для всех классов, которые удовлетворяют указанным критериям выбора.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Параметры

`strSuperclass`\
окне Если значение не `null` указано или пусто, указывает имя родительского класса; перечислитель возвращает только подклассы этого класса. Если значение равно `null` или пусто и `lFlags` WBEM_FLAG_SHALLOW, возвращает только классы верхнего уровня (классы без родительского класса). Если значение равно `null` или пусто и `lFlags` равно `WBEM_FLAG_DEEP` , возвращает все классы в пространстве имен.

`lFlags`\
окне Сочетание флагов, влияющих на поведение этой функции. Следующие значения определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:

|Константа  |Значение  |Описание  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Если параметр задан, функция получает измененные квалификаторы, хранящиеся в локализованном пространстве имен языкового стандарта текущего соединения. <br/> Если значение не задано, функция извлекает только квалификаторы, хранящиеся в пространстве имен immediate. |
| `WBEM_FLAG_DEEP` | 0 | Перечисление включает все подклассы в иерархии, но не этот класс. |
| `WBEM_FLAG_SHALLOW` | 1 | Перечисление включает только чистые экземпляры этого класса и исключает все экземпляры подклассов, которые предоставляют свойства, не найденные в этом классе. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Флаг вызывает вызов семисинчронаус. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Функция возвращает перечислитель только для перенаправления. Как правило, перечислители выполняются быстрее и используют меньше памяти, чем обычные перечислители, но не допускают вызовы для [клонирования](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Инструментарий WMI удерживает указатели на объекты в перечислении до их освобождения. |

`WBEM_FLAG_RETURN_IMMEDIATELY` `WBEM_FLAG_FORWARD_ONLY` Для наилучшей производительности рекомендуется использовать флаги.

`pCtx`\
окне Как правило, это значение равно `null` . В противном случае он является указателем на экземпляр [ивбемконтекст](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , который может использоваться поставщиком, который предоставляет запрошенные классы.

`ppEnum`\
заполняет Получает указатель на перечислитель.

`authLevel`\
окне Уровень авторизации.

`impLevel`\
окне Уровень олицетворения.

`pCurrentNamespace`\
окне Указатель на объект [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , представляющий текущее пространство имен.

`strUser`\
окне Имя пользователя. Дополнительные сведения см. в описании функции [коннектсервервми](connectserverwmi.md) .

`strPassword`\
окне Пароль. Дополнительные сведения см. в описании функции [коннектсервервми](connectserverwmi.md) .

`strAuthority`\
окне Доменное имя пользователя. Дополнительные сведения см. в описании функции [коннектсервервми](connectserverwmi.md) .

## <a name="return-value"></a>Возвращаемое значение

Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:

|Константа  |Значение  |Описание  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Пользователь не имеет разрешения на просмотр одного или нескольких классов, которые может возвращать функция. |
| `WBEM_E_FAILED` | 0x80041001 | Возникла неопределенная ошибка. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` — не существует. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Недействительный параметр. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Недостаточно памяти для выполнения операции. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Вероятно, Инструментарий WMI остановлен и перезапущен. Снова вызовите [коннектсервервми](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Не удалось создать ссылку на удаленный вызов процедур (RPC) между текущим процессом и WMI. |
|`WBEM_S_NO_ERROR` | 0 | Вызов функции выполнен успешно.  |

## <a name="remarks"></a>Комментарии

Эта функция заключает вызов метода [IWbemServices:: креатеклассенум](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .

Если вызов функции завершается неудачно, можно получить дополнительные сведения об ошибке, вызвав функцию [жетерроринфо](geterrorinfo.md) .

## <a name="requirements"></a>Требования

**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).

**Заголовок:** WMINet_Utils. idl

**.NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>См. также раздел

- [WMI и счетчики производительности (справочник по неуправляемым API)](index.md)
