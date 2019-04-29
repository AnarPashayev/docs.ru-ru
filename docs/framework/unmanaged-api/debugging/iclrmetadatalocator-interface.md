---
title: Интерфейс ICLRMetadataLocator
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddc0429a6fa921e8e6ba3c55f3efe5373bea9576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697853"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="72acf-102">Интерфейс ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="72acf-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="72acf-103">Используемый уровнем служб доступа к данным для определения местонахождения метаданных сборок в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="72acf-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72acf-104">Методы</span><span class="sxs-lookup"><span data-stu-id="72acf-104">Methods</span></span>  
  
|<span data-ttu-id="72acf-105">Метод</span><span class="sxs-lookup"><span data-stu-id="72acf-105">Method</span></span>|<span data-ttu-id="72acf-106">Описание</span><span class="sxs-lookup"><span data-stu-id="72acf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72acf-107">Метод GetMetadata</span><span class="sxs-lookup"><span data-stu-id="72acf-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="72acf-108">Извлекает метаданные изображения из целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="72acf-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72acf-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="72acf-109">Remarks</span></span>  
 <span data-ttu-id="72acf-110">Клиент API (то есть отладчик) должен реализовывать этот интерфейс для определенного целевого процесса по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="72acf-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="72acf-111">Например реализация активного процесса будет отличаться от дампа памяти.</span><span class="sxs-lookup"><span data-stu-id="72acf-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72acf-112">Требования</span><span class="sxs-lookup"><span data-stu-id="72acf-112">Requirements</span></span>  
 <span data-ttu-id="72acf-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72acf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72acf-114">**Заголовок.** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="72acf-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="72acf-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72acf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72acf-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72acf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72acf-117">См. также</span><span class="sxs-lookup"><span data-stu-id="72acf-117">See also</span></span>

- [<span data-ttu-id="72acf-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="72acf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
