---
title: Метод IXCLRDataModule::Request
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a02a60668ae6caaad1940395822758331b93f550
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119799"
---
# <a name="ixclrdatamodulerequest-method"></a>Метод IXCLRDataModule::Request

Запросы, чтобы заполнить буфер с данными модуля.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Синтаксис
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Параметры

`reqCode`\
[in] Тип отправляемого запроса.

`inBufferSize`\
[in] размер входного буфера, который передается в.

`inBuffer`\
[in, size_is(inBufferSize)] Указатель на буфер для необработанных данных, которые будут отправляться в запрос.

`outBufferSize`\
[in] Размер выходного буфера.

`outBuffer`\
[out, size_is(outBufferSize)] Указатель буфера, используемого для хранения запрос-ответ.

## <a name="remarks"></a>Примечания

Указанный метод является частью `IXCLRDataModule` интерфейса и соответствует 36-ая слот в таблице виртуального метода.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
**Заголовок.** Нет   
**Библиотека:** Нет  
**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>См. также

- [Отладка](index.md)
- [Интерфейс IXCLRDataModule](ixclrdatamodule-interface.md)