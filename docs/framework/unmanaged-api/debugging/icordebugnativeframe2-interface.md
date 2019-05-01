---
title: Интерфейс ICorDebugNativeFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc664d308d4db3e97597d785eda159e32255fa54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987848"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="c6f07-102">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="c6f07-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="c6f07-103">Предоставляет методы, проверяющие для кадров наличие взаимоотношений типа "дочерний-родительский".</span><span class="sxs-lookup"><span data-stu-id="c6f07-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6f07-104">Методы</span><span class="sxs-lookup"><span data-stu-id="c6f07-104">Methods</span></span>  
  
|<span data-ttu-id="c6f07-105">Метод</span><span class="sxs-lookup"><span data-stu-id="c6f07-105">Method</span></span>|<span data-ttu-id="c6f07-106">Описание</span><span class="sxs-lookup"><span data-stu-id="c6f07-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6f07-107">Метод IsChild</span><span class="sxs-lookup"><span data-stu-id="c6f07-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="c6f07-108">Определяет, является ли текущий кадр дочерним.</span><span class="sxs-lookup"><span data-stu-id="c6f07-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="c6f07-109">Метод IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="c6f07-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="c6f07-110">Определяет, является ли указанный кадр родительским для текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="c6f07-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="c6f07-111">Метод GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="c6f07-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="c6f07-112">Возвращает общий размер параметров в стеке в x86 операционных систем.</span><span class="sxs-lookup"><span data-stu-id="c6f07-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6f07-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="c6f07-113">Remarks</span></span>  
 <span data-ttu-id="c6f07-114">Этот интерфейс логически расширяет интерфейс «ICorDebugNativeFrame».</span><span class="sxs-lookup"><span data-stu-id="c6f07-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6f07-115">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="c6f07-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6f07-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c6f07-116">Requirements</span></span>  
 <span data-ttu-id="c6f07-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6f07-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6f07-118">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6f07-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6f07-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6f07-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6f07-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6f07-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f07-121">См. также</span><span class="sxs-lookup"><span data-stu-id="c6f07-121">See also</span></span>

- [<span data-ttu-id="c6f07-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c6f07-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c6f07-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="c6f07-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
