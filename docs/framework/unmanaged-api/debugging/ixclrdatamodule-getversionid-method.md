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
ms.openlocfilehash: e863f14676acc84f4d9f59d0898dee5b291bd30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775444"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="3c4f7-102">Метод IXCLRDataModule::GetVersionId</span><span class="sxs-lookup"><span data-stu-id="3c4f7-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="3c4f7-103">Получает идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="3c4f7-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3c4f7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c4f7-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="3c4f7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3c4f7-105">Parameters</span></span>

`vid`\
<span data-ttu-id="3c4f7-106">[out] Идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="3c4f7-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c4f7-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="3c4f7-107">Remarks</span></span>

<span data-ttu-id="3c4f7-108">Указанный метод является частью `IXCLRDataModule` интерфейса и соответствует 40-ой слот в таблице виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="3c4f7-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c4f7-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3c4f7-109">Requirements</span></span>

<span data-ttu-id="3c4f7-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c4f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3c4f7-111">**Заголовок.** Нет</span><span class="sxs-lookup"><span data-stu-id="3c4f7-111">**Header:** None</span></span>  
<span data-ttu-id="3c4f7-112">**Библиотека:** Нет</span><span class="sxs-lookup"><span data-stu-id="3c4f7-112">**Library:** None</span></span>  
<span data-ttu-id="3c4f7-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3c4f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3c4f7-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3c4f7-114">See also</span></span>

- [<span data-ttu-id="3c4f7-115">Отладка</span><span class="sxs-lookup"><span data-stu-id="3c4f7-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="3c4f7-116">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="3c4f7-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)