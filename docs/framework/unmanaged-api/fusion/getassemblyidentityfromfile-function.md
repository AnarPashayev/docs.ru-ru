---
title: Функция GetAssemblyIdentityFromFile
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724485"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="89133-102">Функция GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="89133-102">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="89133-103">Возвращает указатель на `IUnknown` объект с указанным `IID` в сборке по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="89133-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89133-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89133-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="89133-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="89133-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="89133-106">окне Допустимый путь к запрошенной сборке.</span><span class="sxs-lookup"><span data-stu-id="89133-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="89133-107">окне `IID` Возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="89133-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="89133-108">заполняет Возвращаемый указатель интерфейса.</span><span class="sxs-lookup"><span data-stu-id="89133-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89133-109">Требования</span><span class="sxs-lookup"><span data-stu-id="89133-109">Requirements</span></span>  

 <span data-ttu-id="89133-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89133-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89133-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="89133-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89133-112">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89133-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89133-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="89133-113">See also</span></span>

- [<span data-ttu-id="89133-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="89133-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="89133-115">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="89133-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
