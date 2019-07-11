---
title: Указатель функции PFN_CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81fcc99a739d5e673d1d01d5efb801ba4930bdee
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752557"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="5bef1-102">Указатель функции PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="5bef1-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="5bef1-103">Указывает на функцию, которая создает объект интерфейса для заданного целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="5bef1-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bef1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5bef1-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bef1-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5bef1-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="5bef1-106">[in] Идентификатор интерфейса для создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5bef1-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="5bef1-107">[in] Указатель на реализуется пользователем [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) , представляющий целевой элемент, для которого создается объект интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5bef1-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="5bef1-108">[out] Указатель на адрес объекта возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5bef1-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bef1-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="5bef1-109">Remarks</span></span>  
 <span data-ttu-id="5bef1-110">`ICLRDataTarget` Объект реализуется разработчиком отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="5bef1-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="5bef1-111">Реализация зависит от тип представляемого целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="5bef1-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="5bef1-112">Конечный элемент может быть процесс, дамп памяти, удаленный компьютер и т. д.</span><span class="sxs-lookup"><span data-stu-id="5bef1-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bef1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5bef1-113">Requirements</span></span>  
 <span data-ttu-id="5bef1-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bef1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bef1-115">**Заголовок.** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="5bef1-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="5bef1-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bef1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bef1-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bef1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bef1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="5bef1-118">See also</span></span>

- [<span data-ttu-id="5bef1-119">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="5bef1-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
