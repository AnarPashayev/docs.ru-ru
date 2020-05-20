---
title: Интерфейс IXCLRDataMethodInstance
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420894"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="bf20b-102">Интерфейс IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="bf20b-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="bf20b-103">Предоставляет методы для запроса сведений об экземпляре метода.</span><span class="sxs-lookup"><span data-stu-id="bf20b-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="bf20b-104">Методы</span><span class="sxs-lookup"><span data-stu-id="bf20b-104">Methods</span></span>

| <span data-ttu-id="bf20b-105">Метод</span><span class="sxs-lookup"><span data-stu-id="bf20b-105">Method</span></span>                                                                                                                  | <span data-ttu-id="bf20b-106">Описание</span><span class="sxs-lookup"><span data-stu-id="bf20b-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="bf20b-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="bf20b-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="bf20b-108">Возвращает IL для сопоставления сведений о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="bf20b-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="bf20b-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="bf20b-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="bf20b-110">Возвращает наиболее репрезентативный адрес точки входа для собственной компиляции всех возможных точек входа для метода.</span><span class="sxs-lookup"><span data-stu-id="bf20b-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bf20b-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="bf20b-111">Remarks</span></span>

<span data-ttu-id="bf20b-112">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="bf20b-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bf20b-113">Однако это COM-интерфейс, производный от `IUnknown` GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="bf20b-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf20b-114">Требования</span><span class="sxs-lookup"><span data-stu-id="bf20b-114">Requirements</span></span>

<span data-ttu-id="bf20b-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf20b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bf20b-116">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="bf20b-116">**Header:** None</span></span>  
<span data-ttu-id="bf20b-117">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="bf20b-117">**Library:** None</span></span>  
<span data-ttu-id="bf20b-118">**.NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf20b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bf20b-119">См. также статью</span><span class="sxs-lookup"><span data-stu-id="bf20b-119">See also</span></span>

- [<span data-ttu-id="bf20b-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="bf20b-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="bf20b-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="bf20b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
