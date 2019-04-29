---
title: Функция CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961178"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="4b4b3-102">Функция CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="4b4b3-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="4b4b3-103">Закрывает любой допустимый событий среды CLR (CLR) продолжения запуска находятся в массиве дескрипторов, возвращенном [функция EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)и освобождает память для массивов дескрипторов и строк пути.</span><span class="sxs-lookup"><span data-stu-id="4b4b3-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b4b3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b4b3-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b4b3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4b4b3-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="4b4b3-106">[in] Указатель на массив дескрипторов событий, возвращенных из [функция EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="4b4b3-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="4b4b3-107">[in] Указатель на массив путей строки среды CLR, возвращенный [функция EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="4b4b3-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="4b4b3-108">[in] Значение DWORD, содержащее размер (длину) массива `pHandleArray` или `pStringArray` (они одинаковые).</span><span class="sxs-lookup"><span data-stu-id="4b4b3-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b4b3-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4b4b3-109">Return Value</span></span>  
 <span data-ttu-id="4b4b3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b4b3-110">S_OK</span></span>  
 <span data-ttu-id="4b4b3-111">Дескрипторы, открытые [функция EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) будут закрыты, и освободить память, выделенная для массивов дескрипторов и строк.</span><span class="sxs-lookup"><span data-stu-id="4b4b3-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="4b4b3-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4b4b3-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="4b4b3-113">Длина массива `pHandleArray` не соответствует длине, переданной в `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="4b4b3-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="4b4b3-114">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="4b4b3-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4b4b3-115">Функции не удалось освободить память для массивов `pHandleArray` и `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="4b4b3-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b4b3-116">Требования</span><span class="sxs-lookup"><span data-stu-id="4b4b3-116">Requirements</span></span>  
 <span data-ttu-id="4b4b3-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b4b3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b4b3-118">**Заголовок:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="4b4b3-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="4b4b3-119">**Библиотека:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="4b4b3-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="4b4b3-120">**Версии платформы .NET framework:** 3.5 с пакетом обновления 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="4b4b3-120">**.NET Framework Versions:** 3.5 SP1</span></span>
