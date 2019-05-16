---
title: Метод EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cd154ac90418dd0f6f476151686ff670c01c98c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632236"
---
# <a name="enumimporttypes-method"></a>Метод EnumImportTypes

Перечисляет каждый тип в каждой области.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Параметры

`hEnum`\
Дескриптор для перечислителя.

`dwMax`\
Максимальное число извлекаемых типов.

`aTypeDefs`\
Получает тип токенов, оно не должно превышать `dwMax`.

`pdwCount`\
Получает фактическое число типов в `aTypeDefs`.

## <a name="return-value"></a>Возвращаемое значение

Возвращает S_OK, если метод выполнен успешно.

## <a name="requirements"></a>Требования

Требуется alink.h

## <a name="see-also"></a>См. также

- [Интерфейс IALink](ialink-interface.md)
- [Интерфейс IALink2](ialink2-interface.md)
- [API ALink](index.md)
