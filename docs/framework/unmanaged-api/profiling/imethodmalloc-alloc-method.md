---
title: Метод IMethodMalloc::Alloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636701"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="7615a-102">Метод IMethodMalloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="7615a-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="7615a-103">Пытается выделить указанный объем памяти для нового тела функции промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="7615a-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="7615a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7615a-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="7615a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7615a-105">Parameters</span></span>

`cb`\
<span data-ttu-id="7615a-106">[in] Число байтов, выделенных для тела метода.</span><span class="sxs-lookup"><span data-stu-id="7615a-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="7615a-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="7615a-107">Remarks</span></span>

 <span data-ttu-id="7615a-108">Выделенная память начинается по адресу больше, чем базовый адрес модуля, связанного с данным распределителем.</span><span class="sxs-lookup"><span data-stu-id="7615a-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="7615a-109">Другими словами каждый распределитель создается для определенного модуля и предпринимает попытку выделения памяти с положительным смещением от базового адреса.</span><span class="sxs-lookup"><span data-stu-id="7615a-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="7615a-110">Если `Alloc` не удается выделить запрошенное число байт по адресу больше, чем базовый адрес модуля, он возвращает значение E_OUTOFMEMORY, независимо от фактического объема доступной памяти.</span><span class="sxs-lookup"><span data-stu-id="7615a-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="7615a-111">`Alloc` Метод должен использоваться в сочетании с [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="7615a-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7615a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7615a-112">Requirements</span></span>
 <span data-ttu-id="7615a-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7615a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="7615a-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7615a-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="7615a-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7615a-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="7615a-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7615a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7615a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7615a-117">See also</span></span>

- [<span data-ttu-id="7615a-118">Интерфейс IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="7615a-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
