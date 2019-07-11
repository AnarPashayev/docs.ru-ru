---
title: Метод IXCLRDataModule::GetVersionId
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744701"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="d023c-102">Метод IXCLRDataModule::GetVersionId</span><span class="sxs-lookup"><span data-stu-id="d023c-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="d023c-103">Получает идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="d023c-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d023c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d023c-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="d023c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d023c-105">Parameters</span></span>

`vid`\
<span data-ttu-id="d023c-106">[out] Идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="d023c-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="d023c-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="d023c-107">Remarks</span></span>

<span data-ttu-id="d023c-108">Указанный метод является частью `IXCLRDataModule` интерфейса и соответствует 40-ой слот в таблице виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="d023c-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d023c-109">Требования</span><span class="sxs-lookup"><span data-stu-id="d023c-109">Requirements</span></span>

<span data-ttu-id="d023c-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d023c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d023c-111">**Заголовок.** None</span><span class="sxs-lookup"><span data-stu-id="d023c-111">**Header:** None</span></span>  
<span data-ttu-id="d023c-112">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="d023c-112">**Library:** None</span></span>  
<span data-ttu-id="d023c-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d023c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d023c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="d023c-114">See also</span></span>

- [<span data-ttu-id="d023c-115">Отладка</span><span class="sxs-lookup"><span data-stu-id="d023c-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="d023c-116">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="d023c-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
