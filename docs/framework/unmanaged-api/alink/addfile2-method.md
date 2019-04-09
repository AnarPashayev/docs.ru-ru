---
title: Метод AddFile2
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a651be40773607e0db215eadf884ed642e6e3b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126936"
---
# <a name="addfile2-method"></a>Метод AddFile2
Добавляет файлы в сборку. Может также использоваться для создания несвязанных модулей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Параметры  
 `AssemblyID`  
 Идентификатор сборки, к которому добавляется файл.  
  
 `pszFilename`  
 Имя файла для добавления.  
  
 `dwFlags`  
 COM + `FileDef` флаги, такие как `ffContainsNoMetaData` и `ffWriteable`. `dwFlags` передается [метод DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Интерфейс для [интерфейс IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) интерфейс.  
  
 `pFileToken`  
 Получает идентификатор для добавляемого файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает S_OK, если метод выполнен успешно.  
  
## <a name="requirements"></a>Требования  
 Требуется alink.h.  
  
## <a name="see-also"></a>См. также

- [Интерфейс IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Интерфейс IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
