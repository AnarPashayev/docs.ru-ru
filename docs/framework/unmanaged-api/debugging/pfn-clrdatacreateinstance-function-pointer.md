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
ms.openlocfilehash: 34aae3cd913465bc3167d6c5eee9873d212fa4ac
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420697"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="d8028-102">Указатель функции PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="d8028-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="d8028-103">Указывает на функцию, которая создает объект интерфейса для указанного целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="d8028-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8028-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8028-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8028-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8028-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="d8028-106">окне Идентификатор интерфейса, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="d8028-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="d8028-107">окне Указатель на реализуемый пользователем объект [ICLRDataTarget](iclrdatatarget-interface.md) , представляющий целевой элемент, для которого создается объект интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d8028-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="d8028-108">заполняет Указатель на адрес возвращенного объекта интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d8028-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8028-109">Комментарии</span><span class="sxs-lookup"><span data-stu-id="d8028-109">Remarks</span></span>  
 <span data-ttu-id="d8028-110">`ICLRDataTarget`Объект реализуется модулем записи приложения отладки.</span><span class="sxs-lookup"><span data-stu-id="d8028-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="d8028-111">Реализация зависит от типа представляемого целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="d8028-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="d8028-112">Целевой элемент может быть процессом, дампом памяти, удаленным компьютером и т. д.</span><span class="sxs-lookup"><span data-stu-id="d8028-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8028-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d8028-113">Requirements</span></span>  
 <span data-ttu-id="d8028-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8028-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8028-115">**Заголовок:** Клрдата. idl</span><span class="sxs-lookup"><span data-stu-id="d8028-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="d8028-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8028-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8028-117">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8028-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8028-118">См. также статью</span><span class="sxs-lookup"><span data-stu-id="d8028-118">See also</span></span>

- [<span data-ttu-id="d8028-119">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="d8028-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
