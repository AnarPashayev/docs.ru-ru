---
title: Метод IMetaDataImport::GetParamForMethodIndex
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c6f06ff4fc7d855ea07f1f572a2b7ea948efc51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207062"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="564a9-102">Метод IMetaDataImport::GetParamForMethodIndex</span><span class="sxs-lookup"><span data-stu-id="564a9-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="564a9-103">Возвращает токен, представляющий указанный параметр метода, представленного указанным токеном MethodDef.</span><span class="sxs-lookup"><span data-stu-id="564a9-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="564a9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="564a9-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="564a9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="564a9-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="564a9-106">[in] Токен, который представляет метод для возврата токена для параметра.</span><span class="sxs-lookup"><span data-stu-id="564a9-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="564a9-107">[in] Порядковая позиция в списке параметров, где происходит запрошенного параметра.</span><span class="sxs-lookup"><span data-stu-id="564a9-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="564a9-108">Параметры нумеруются, начиная с 1, возвращаемое значение метода в нулевой позиции.</span><span class="sxs-lookup"><span data-stu-id="564a9-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="564a9-109">[out] Указатель на токен ParamDef, представляющий запрашиваемый параметр.</span><span class="sxs-lookup"><span data-stu-id="564a9-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="564a9-110">Требования</span><span class="sxs-lookup"><span data-stu-id="564a9-110">Requirements</span></span>  
 <span data-ttu-id="564a9-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="564a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="564a9-112">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="564a9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="564a9-113">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="564a9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="564a9-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="564a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="564a9-115">См. также</span><span class="sxs-lookup"><span data-stu-id="564a9-115">See also</span></span>

- [<span data-ttu-id="564a9-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="564a9-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="564a9-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="564a9-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
