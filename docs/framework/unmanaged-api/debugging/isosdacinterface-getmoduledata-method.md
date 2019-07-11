---
title: Метод ISOSDacInterface::GetModuleData
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 97b297def9fba329ff6d9573f7b2e7cc811273f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764720"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="46be1-102">Метод ISOSDacInterface::GetModuleData</span><span class="sxs-lookup"><span data-stu-id="46be1-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="46be1-103">Извлекает данные, соответствующие модуль загружен по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="46be1-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="46be1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46be1-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="46be1-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="46be1-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="46be1-106">[in] Адрес модуля для получения сведений для.</span><span class="sxs-lookup"><span data-stu-id="46be1-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="46be1-107">[out] [DacpModuleData структуры](dacpmoduledata-structure.md) для хранения информации о загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="46be1-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="46be1-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="46be1-108">Remarks</span></span>

<span data-ttu-id="46be1-109">Указанный метод является частью `ISOSDacInterface` интерфейса и соответствует 13-й слот в таблице виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="46be1-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="46be1-110">Требования</span><span class="sxs-lookup"><span data-stu-id="46be1-110">Requirements</span></span>

<span data-ttu-id="46be1-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46be1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="46be1-112">**Заголовок.** None</span><span class="sxs-lookup"><span data-stu-id="46be1-112">**Header:** None</span></span>  
<span data-ttu-id="46be1-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="46be1-113">**Library:** None</span></span>  
<span data-ttu-id="46be1-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="46be1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="46be1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="46be1-115">See also</span></span>

- [<span data-ttu-id="46be1-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="46be1-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="46be1-117">Интерфейс ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="46be1-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
