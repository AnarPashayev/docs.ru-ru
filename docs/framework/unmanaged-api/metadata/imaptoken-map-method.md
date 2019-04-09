---
title: Метод IMapToken::Map
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a85dc586b0c08fabdd34c018e82314c9003eeded
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171019"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="a2a81-102">Метод IMapToken::Map</span><span class="sxs-lookup"><span data-stu-id="a2a81-102">IMapToken::Map Method</span></span>
<span data-ttu-id="a2a81-103">Сопоставляет связь между сборками, используя подписи метаданных.</span><span class="sxs-lookup"><span data-stu-id="a2a81-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a81-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2a81-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a81-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a2a81-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="a2a81-106">[in] Токен метаданных, представляющий объект импортированном коде.</span><span class="sxs-lookup"><span data-stu-id="a2a81-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="a2a81-107">[in] Токен метаданных, представляющий объект порожденного кода.</span><span class="sxs-lookup"><span data-stu-id="a2a81-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2a81-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="a2a81-108">Remarks</span></span>  
 <span data-ttu-id="a2a81-109">При выполнении повторного сопоставления маркеров во время слияния, исходный маркер действует в области метаданных исходную и в области метаданных целевую относится новый токен.</span><span class="sxs-lookup"><span data-stu-id="a2a81-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a81-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a2a81-110">Requirements</span></span>  
 <span data-ttu-id="a2a81-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2a81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a81-112">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2a81-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2a81-113">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2a81-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a2a81-114">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a2a81-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2a81-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a2a81-115">See also</span></span>

- [<span data-ttu-id="a2a81-116">Интерфейс IMapToken</span><span class="sxs-lookup"><span data-stu-id="a2a81-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
