---
title: Метод IMetaDataEmit::DefineField
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057bae1d702fa091ebc3d3178c9fba35d5dd3d90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777652"
---
# <a name="imetadataemitdefinefield-method"></a>Метод IMetaDataEmit::DefineField
Создает определение для поля с заданной подписью метаданных и получает маркер для этого определения поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Параметры  
 `td`  
 [in] `mdTypeDef` Маркеров для включающего класса или интерфейса.  
  
 `szName`  
 [in] Имя поля в формате Юникод.  
  
 `dwFieldFlags`  
 [in] Атрибуты поля. Это битовая маска `CorFieldAttr` значения.  
  
 `pvSigBlob`  
 [in] Подпись поля как большой двоичный объект.  
  
 `cbSigBlob`  
 [in] Число байт в `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** Для постоянного значения. Это `CorElementType` значение. Если не применяется частное определение постоянное значение для поля, используйте `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] Постоянное значение для поля.  
  
 `cchValue`  
 [in] Размер в символах (Юникод) `pValue`.  
  
 `pmd`  
 [out] `mdFieldDef` Маркер, назначенный.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Cor.h  
  
 **Библиотека:** Используется как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Интерфейс IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
