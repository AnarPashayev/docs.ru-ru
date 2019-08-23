---
title: Интерфейс ICorDebugType2
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2f2c1e4c95c61eab4c9da6103d4ac479b4bbdb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936057"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="d97e4-102">Интерфейс ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="d97e4-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="d97e4-103">Расширяет интерфейс ICorDebugType для получения идентификатора типа базового типа или сложного (определяемого пользователем) типа.</span><span class="sxs-lookup"><span data-stu-id="d97e4-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d97e4-104">Методы</span><span class="sxs-lookup"><span data-stu-id="d97e4-104">Methods</span></span>  
  
|<span data-ttu-id="d97e4-105">Метод</span><span class="sxs-lookup"><span data-stu-id="d97e4-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="d97e4-106">Метод GetTypeID</span><span class="sxs-lookup"><span data-stu-id="d97e4-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="d97e4-107">Возвращает [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) для этого типа.</span><span class="sxs-lookup"><span data-stu-id="d97e4-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d97e4-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="d97e4-108">Remarks</span></span>  
 <span data-ttu-id="d97e4-109">Этот интерфейс является логическим расширением интерфейса ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="d97e4-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d97e4-110">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="d97e4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d97e4-111">Пример</span><span class="sxs-lookup"><span data-stu-id="d97e4-111">Example</span></span>  
 <span data-ttu-id="d97e4-112">В следующем фрагменте кода показано использование метода [ICorDebugType2:: typeid](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d97e4-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="d97e4-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d97e4-113">Requirements</span></span>  
 <span data-ttu-id="d97e4-114">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97e4-115">**Заголовок.** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d97e4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d97e4-116">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="d97e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d97e4-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d97e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97e4-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d97e4-118">See also</span></span>

- [<span data-ttu-id="d97e4-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d97e4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
