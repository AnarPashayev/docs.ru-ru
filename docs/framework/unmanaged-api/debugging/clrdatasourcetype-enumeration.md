---
title: Перечисление CLRDataSourceType
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c8b3f338659e2784db8deca3e1776e7926c30c32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609694"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="94cd3-102">Перечисление CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="94cd3-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="94cd3-103">Предоставляет значения, которые используются в структуре CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="94cd3-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="94cd3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94cd3-104">Syntax</span></span>

```
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="94cd3-105">Участники</span><span class="sxs-lookup"><span data-stu-id="94cd3-105">Members</span></span>

| <span data-ttu-id="94cd3-106">Член</span><span class="sxs-lookup"><span data-stu-id="94cd3-106">Member</span></span>                        | <span data-ttu-id="94cd3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="94cd3-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="94cd3-108">Чтобы указать, что ничего применяется</span><span class="sxs-lookup"><span data-stu-id="94cd3-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="94cd3-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="94cd3-109">Remarks</span></span>

<span data-ttu-id="94cd3-110">Это перечисление находится внутри среды выполнения и не предоставляется через любой заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="94cd3-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="94cd3-111">Чтобы использовать его, определите перечисление, как указано выше, в коде.</span><span class="sxs-lookup"><span data-stu-id="94cd3-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="94cd3-112">Это также псевдонимом `CLRDATA_ENUM` как уже упоминалось в [общие типы данных](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="94cd3-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="94cd3-113">Требования</span><span class="sxs-lookup"><span data-stu-id="94cd3-113">Requirements</span></span>

<span data-ttu-id="94cd3-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94cd3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="94cd3-115">**Заголовок.** Нет</span><span class="sxs-lookup"><span data-stu-id="94cd3-115">**Header:** None</span></span>  
<span data-ttu-id="94cd3-116">**Библиотека:** Нет</span><span class="sxs-lookup"><span data-stu-id="94cd3-116">**Library:** None</span></span>  
<span data-ttu-id="94cd3-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94cd3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="94cd3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="94cd3-118">See also</span></span>

- [<span data-ttu-id="94cd3-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="94cd3-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="94cd3-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="94cd3-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
