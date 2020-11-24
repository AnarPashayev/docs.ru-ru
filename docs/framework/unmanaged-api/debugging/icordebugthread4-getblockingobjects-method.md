---
title: Метод ICorDebugThread4::GetBlockingObjects
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: eb8692aebe7b702b5778b3f13e496d81dcd45784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678551"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="d43b3-102">Метод ICorDebugThread4::GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="d43b3-102">ICorDebugThread4::GetBlockingObjects Method</span></span>

<span data-ttu-id="d43b3-103">Предоставляет упорядоченное перечисление структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) , которые предоставляют сведения о блокировке потока.</span><span class="sxs-lookup"><span data-stu-id="d43b3-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43b3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d43b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="d43b3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d43b3-105">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="d43b3-106">заполняет Указатель на упорядоченное перечисление структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d43b3-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d43b3-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="d43b3-107">Remarks</span></span>  

 <span data-ttu-id="d43b3-108">Первый элемент в возвращенном перечислении соответствует первой структуре, блокирующей поток.</span><span class="sxs-lookup"><span data-stu-id="d43b3-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="d43b3-109">Второй элемент соответствует блокирующему элементу, который обнаруживается при выполнении асинхронного вызова процедуры (APC) при блокировке в первом и т. д.</span><span class="sxs-lookup"><span data-stu-id="d43b3-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="d43b3-110">Перечисление допустимо только в течение текущего синхронизированного состояния.</span><span class="sxs-lookup"><span data-stu-id="d43b3-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="d43b3-111">Этот метод должен вызываться, когда отлаживаемый объект находится в синхронизированном состоянии.</span><span class="sxs-lookup"><span data-stu-id="d43b3-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="d43b3-112">Если не `ppBlockingObjectEnum` является допустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="d43b3-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="d43b3-113">Если поток заблокирован и ошибка не может быть определена, метод возвращает значение HRESULT, указывающее на ошибку; в противном случае возвращается S_OK.</span><span class="sxs-lookup"><span data-stu-id="d43b3-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43b3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="d43b3-114">Requirements</span></span>  

 <span data-ttu-id="d43b3-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d43b3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43b3-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d43b3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d43b3-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d43b3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d43b3-118">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43b3-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d43b3-119">See also</span></span>

- [<span data-ttu-id="d43b3-120">Интерфейс ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="d43b3-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="d43b3-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d43b3-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d43b3-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="d43b3-122">Debugging</span></span>](index.md)
