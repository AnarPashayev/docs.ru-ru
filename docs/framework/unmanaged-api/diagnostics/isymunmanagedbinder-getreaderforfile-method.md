---
title: Метод ISymUnmanagedBinder::GetReaderForFile
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441738"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>Метод ISymUnmanagedBinder::GetReaderForFile
При наличии интерфейса метаданных и имени файла возвращает правильный интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) , который будет считывать символы отладки, связанные с модулем.  
  
 Этот метод будет открывать файл базы данных программы (PDB) только в том случае, если он находится рядом с исполняемым файлом. Это изменение было внесено в целях безопасности. Если требуется более широкий поиск PDB-файла, используйте метод [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Параметры  
 `importer`  
 окне Указатель на интерфейс импорта метаданных.  
  
 `fileName`  
 окне Указатель на имя файла.  
  
 `searchPath`  
 окне Указатель на путь поиска.  
  
 `pRetVal`  
 заполняет Указатель, которому присваивается возвращаемый интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** Корсим. idl, Корсим. h  
  
## <a name="see-also"></a>Дополнительно

- [Интерфейс ISymUnmanagedBinder](isymunmanagedbinder-interface.md)
- [Метод GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md)
