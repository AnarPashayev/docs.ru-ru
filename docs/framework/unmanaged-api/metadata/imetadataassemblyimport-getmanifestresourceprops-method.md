---
title: Метод IMetaDataAssemblyImport::GetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081668"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>Метод IMetaDataAssemblyImport::GetManifestResourceProps
Получает набор свойств ресурса манифеста с заданной подписью метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `mdmr`  
 [in] `mdManifestResource` Токен, представляющий ресурс, для которого нужно получить свойства.  
  
 `szName`  
 [out] Имя ресурса.  
  
 `cchName`  
 [in] Размер, в расширенных символах из `szName`.  
  
 `pchName`  
 [out] Указатель на число расширенных символов, фактически возвращенных в `szName`.  
  
 `ptkImplementation`  
 [out] Указатель на `mdFile` маркеров или `mdAssemblyRef` токен, который представляет файл или сборку, соответственно, содержащего ресурс.  
  
 `pdwOffset`  
 [out] Указатель на значение, указывающее смещение в начало ресурса в файле.  
  
 `pdwResourceFlags`  
 [out] Указатель на флаги, описывающие метаданные, применяемые к ресурсу. Значение флагов представляет собой сочетание одного или нескольких [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) значения.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Cor.h  
  
 **Библиотека:** Используется как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
