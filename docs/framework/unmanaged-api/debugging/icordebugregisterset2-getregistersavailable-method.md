---
title: Метод ICorDebugRegisterSet2::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: cb56ea817d4045c19793a6290d68ae8b6236f14a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712325"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="a6bb0-102">Метод ICorDebugRegisterSet2::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="a6bb0-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>

<span data-ttu-id="a6bb0-103">Возвращает массив байтов, предоставляющий битовую карту доступных регистров.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6bb0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6bb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6bb0-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6bb0-105">Parameters</span></span>  

 `numChunks`  
 <span data-ttu-id="a6bb0-106">[in] Размер массива `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="a6bb0-107">заполняет Массив байтов, каждый бит которого соответствует регистру.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="a6bb0-108">Если регистр доступен, устанавливается соответствующий бит регистра.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6bb0-109">Комментарии</span><span class="sxs-lookup"><span data-stu-id="a6bb0-109">Remarks</span></span>  

 <span data-ttu-id="a6bb0-110">Значения перечисления CorDebugRegister указывают регистры различных микропроцессоров.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="a6bb0-111">Верхние пять битов каждого значения являются индексом в `availableRegChunks` массиве байтов.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="a6bb0-112">Младшие три бита каждого значения обозначают битовую точку в индексируемом байте.</span><span class="sxs-lookup"><span data-stu-id="a6bb0-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="a6bb0-113">Учитывая `CorDebugRegister` значение, указывающее конкретный регистр, расположение регистра в маске определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a6bb0-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="a6bb0-114">Извлеките индекс, необходимый для доступа к нужному байту в `availableRegChunks` массиве:</span><span class="sxs-lookup"><span data-stu-id="a6bb0-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="a6bb0-115">`CorDebugRegister` значение >> 3</span><span class="sxs-lookup"><span data-stu-id="a6bb0-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="a6bb0-116">Извлечение битовой позиции в индексируемом байте, где нулевой бит является наименее значимым битом:</span><span class="sxs-lookup"><span data-stu-id="a6bb0-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="a6bb0-117">`CorDebugRegister` значение & 7</span><span class="sxs-lookup"><span data-stu-id="a6bb0-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6bb0-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a6bb0-118">Requirements</span></span>  

 <span data-ttu-id="a6bb0-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6bb0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6bb0-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6bb0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6bb0-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6bb0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6bb0-122">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6bb0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bb0-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a6bb0-123">See also</span></span>

- [<span data-ttu-id="a6bb0-124">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="a6bb0-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="a6bb0-125">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="a6bb0-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
