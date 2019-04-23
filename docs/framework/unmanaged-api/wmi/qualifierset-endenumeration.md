---
title: Функция QualifierSet_EndEnumeration (Справочник по неуправляемым API)
description: Функция QualifierSet_EndEnumeration завершает перечисления.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2dfd6bb521dee14afd3728bdd9c446cb779e85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149231"
---
# <a name="qualifiersetendenumeration-function"></a>Функция QualifierSet_EndEnumeration
Завершается перечисление начался вызовом [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) функции.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Параметры

`vFunc`  
[in] Этот параметр не используется.

`ptr`   
[in] Указатель на [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) экземпляра.

## <a name="return-value"></a>Возвращаемое значение

Следующее значение, возвращаемое этой функцией, определенные в *WbemCli.h* файл заголовка, также можно определить его как константа в коде:

|Константа  |Значение  |Описание  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Вызов функции был успешным.  |
  
## <a name="remarks"></a>Примечания

Эта функция создает оболочку для вызова [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) метод.

Этот вызов рекомендуется, но не является обязательным. Она немедленно освобождает ресурсы, связанные с перечислением.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
**Заголовок.** WMINet_Utils.idl  
  
**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>См. также

- [WMI и счетчики производительности (Справочник по неуправляемым API)](index.md)
