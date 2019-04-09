---
title: Метод IMetaDataAssemblyEmit::DefineAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b95a583aec87e3ba3e247d1ef800302b62657837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176011"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>Метод IMetaDataAssemblyEmit::DefineAssembly
Создает `Assembly` структуры содержащие метаданные для указанной сборки и возвращает связанный токен метаданных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pbPublicKey`  
 [in] Открытый ключ, который идентифицирует издателя сборки, или значение NULL, если сборка не имеет строгого имени.  
  
 `cbPublicKey`  
 [in] Размер в байтах `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Идентификатор алгоритма хэширования, используемый для шифрования файлов в сборке, или значение NULL для задания алгоритма SHA-1.  
  
 `szName`  
 [in] Понятное текстовое имя сборки. Это значение не должна превышать 1024 символа.  
  
 `pMetaData`  
 [in] Указатель на экземпляр ASSEMBLYMETADATA, содержащий сведения о версии, платформы и языковой стандарт для сборки.  
  
 `dwAssemblyFlags`  
 [in] Сочетание [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) значения, описывающие возможности сборки.  
  
 `pmda`  
 [out] Указатель на токен метаданных.  
  
## <a name="remarks"></a>Примечания  
 Только один `Assembly` структуру метаданных можно определить в манифесте.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** Cor.h  
  
 **Библиотека:** Включена как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
