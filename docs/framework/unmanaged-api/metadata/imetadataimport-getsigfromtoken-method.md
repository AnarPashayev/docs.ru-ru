---
title: Метод IMetaDataImport::GetSigFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 823a172c05d2ce76fef790966f54d7216f579fde
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152988"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="235d7-102">Метод IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="235d7-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="235d7-103">Возвращает двоичную подпись метаданных, связанную с указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="235d7-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="235d7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="235d7-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="235d7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="235d7-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="235d7-106">[in] Токен для двоичную подпись метаданных для возврата.</span><span class="sxs-lookup"><span data-stu-id="235d7-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="235d7-107">[out] Указатель на подпись возвращенные метаданные.</span><span class="sxs-lookup"><span data-stu-id="235d7-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="235d7-108">[out] Размер в байтах двоичную подпись метаданных.</span><span class="sxs-lookup"><span data-stu-id="235d7-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="235d7-109">Требования</span><span class="sxs-lookup"><span data-stu-id="235d7-109">Requirements</span></span>  
 <span data-ttu-id="235d7-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="235d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="235d7-111">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="235d7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="235d7-112">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="235d7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="235d7-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="235d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235d7-114">См. также</span><span class="sxs-lookup"><span data-stu-id="235d7-114">See also</span></span>

- [<span data-ttu-id="235d7-115">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="235d7-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="235d7-116">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="235d7-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
