---
title: Метод IXCLRDataProcess::EndEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 378095aa2b363f4003a5372b4158df27412655e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757854"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="4a3ee-102">Метод IXCLRDataProcess::EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="4a3ee-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="4a3ee-103">Освобождает ресурсы, используемые внутренней итераторы, используется в процессе экземпляра перечисления.</span><span class="sxs-lookup"><span data-stu-id="4a3ee-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4a3ee-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a3ee-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="4a3ee-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a3ee-105">Parameters</span></span>

`handle`\
<span data-ttu-id="4a3ee-106">[out] Дескриптор для перечисления экземпляров метода.</span><span class="sxs-lookup"><span data-stu-id="4a3ee-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a3ee-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="4a3ee-107">Remarks</span></span>

<span data-ttu-id="4a3ee-108">Указанный метод является частью `IXCLRDataProcess` интерфейса и соответствует 29 слот в таблице виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="4a3ee-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a3ee-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4a3ee-109">Requirements</span></span>

<span data-ttu-id="4a3ee-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4a3ee-111">**Заголовок.** None</span><span class="sxs-lookup"><span data-stu-id="4a3ee-111">**Header:** None</span></span>  
<span data-ttu-id="4a3ee-112">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="4a3ee-112">**Library:** None</span></span>  
<span data-ttu-id="4a3ee-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4a3ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4a3ee-114">См. также</span><span class="sxs-lookup"><span data-stu-id="4a3ee-114">See also</span></span>

- [<span data-ttu-id="4a3ee-115">Перечисление CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="4a3ee-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4a3ee-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="4a3ee-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="4a3ee-117">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="4a3ee-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
