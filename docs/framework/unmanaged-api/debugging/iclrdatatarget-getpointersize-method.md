---
title: Метод ICLRDataTarget::GetPointerSize
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73645265821d5854776e412f8eb0f33b36db00d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130498"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="28930-102">Метод ICLRDataTarget::GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="28930-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="28930-103">Возвращает размер в байтах, типа указателя, использующего целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="28930-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="28930-104">Этот метод вызывается службами доступа к данным среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="28930-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28930-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28930-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28930-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="28930-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="28930-107">[out] Указатель на целочисленное значение, указывающее размер в байтах для указателя на целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="28930-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28930-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="28930-108">Remarks</span></span>  
 <span data-ttu-id="28930-109">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="28930-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28930-110">Требования</span><span class="sxs-lookup"><span data-stu-id="28930-110">Requirements</span></span>  
 <span data-ttu-id="28930-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28930-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28930-112">**Заголовок.** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="28930-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="28930-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28930-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28930-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28930-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28930-115">См. также</span><span class="sxs-lookup"><span data-stu-id="28930-115">See also</span></span>

- [<span data-ttu-id="28930-116">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="28930-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
