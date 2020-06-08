---
title: Метод IMetaDataTables::GetColumnInfo
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501200"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>Метод IMetaDataTables::GetColumnInfo
Получает данные о указанном столбце в указанной таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Параметры
=======

 `ixTbl`  
 окне Индекс требуемой таблицы.  
  
 `ixCol`  
 окне Индекс нужного столбца.  
  
 `poCol`  
 заполняет Указатель на смещение столбца в строке.  
  
 `pcbCol`  
 заполняет Указатель на размер столбца в байтах.  
  
 `pType`  
 заполняет Указатель на тип значений в столбце.  
  
 `ppName`  
 заполняет Указатель на указатель на имя столбца.  

## <a name="remarks"></a>Примечания

Возвращаемый тип столбца попадает в диапазон значений:

| птипе                    | Описание   | Вспомогательная функция                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Избежать           | **исридтипе**<br>**исридортокен** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | Закодированный маркер | **искодедтокентипе** <br>**исридортокен** |
| `iSHORT`(96)            | Int16         | **исфикседтипе**                   |
| `iUSHORT`(97)           | UInt16        | **исфикседтипе**                   |
| `iLONG`(98)             | Int32         | **исфикседтипе**                   |
| `iULONG`(99)            | UInt32        | **исфикседтипе**                   |
| `iBYTE`(100)            | Byte          | **исфикседтипе**                   |
| `iSTRING`(101)          | Строка        | **ишеаптипе**                    |
| `iGUID`(102)            | Guid          | **ишеаптипе**                    |
| `iBLOB`(103)            | BLOB-объект          | **ишеаптипе**                    |

Значения, хранящиеся в *куче* (т `IsHeapType == true` . е.), можно считывать с помощью:

- `iSTRING`: **IMetadataTables. GetString**
- `iGUID`: **IMetadataTables. с GUID**
- `iBLOB`: **IMetadataTables. BLOB**

> [!IMPORTANT]
> Чтобы использовать константы, определенные в приведенной выше таблице, включите директиву, `#define _DEFINE_META_DATA_META_CONSTANTS` предоставленную файлом заголовка *COR. h* .

## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** COR. h  
  
 **Библиотека:** Используется в качестве ресурса в MsCorEE. dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IMetaDataTables](imetadatatables-interface.md)
- [Интерфейс IMetaDataTables2](imetadatatables2-interface.md)
