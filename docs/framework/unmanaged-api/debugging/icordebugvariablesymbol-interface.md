---
title: Интерфейс ICorDebugVariableSymbol
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967982"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="fd183-102">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="fd183-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="fd183-103">Извлекает сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="fd183-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd183-104">Методы</span><span class="sxs-lookup"><span data-stu-id="fd183-104">Methods</span></span>  
  
|<span data-ttu-id="fd183-105">Метод</span><span class="sxs-lookup"><span data-stu-id="fd183-105">Method</span></span>|<span data-ttu-id="fd183-106">Описание</span><span class="sxs-lookup"><span data-stu-id="fd183-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd183-107">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="fd183-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="fd183-108">Получает имя переменной.</span><span class="sxs-lookup"><span data-stu-id="fd183-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="fd183-109">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="fd183-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="fd183-110">Получает размер переменной в байтах.</span><span class="sxs-lookup"><span data-stu-id="fd183-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="fd183-111">Метод GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="fd183-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="fd183-112">Возвращает управляемый индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="fd183-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="fd183-113">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="fd183-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="fd183-114">Возвращает значение переменной в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="fd183-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="fd183-115">Метод SetValue</span><span class="sxs-lookup"><span data-stu-id="fd183-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="fd183-116">Присваивает переменной значение массива байтов.</span><span class="sxs-lookup"><span data-stu-id="fd183-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd183-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="fd183-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd183-118">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd183-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fd183-119">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="fd183-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd183-120">Требования</span><span class="sxs-lookup"><span data-stu-id="fd183-120">Requirements</span></span>  
 <span data-ttu-id="fd183-121">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd183-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd183-122">**Заголовок.** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd183-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd183-123">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="fd183-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd183-124">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd183-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd183-125">См. также</span><span class="sxs-lookup"><span data-stu-id="fd183-125">See also</span></span>

- [<span data-ttu-id="fd183-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fd183-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fd183-127">Отладка</span><span class="sxs-lookup"><span data-stu-id="fd183-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
