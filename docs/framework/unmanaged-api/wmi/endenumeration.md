---
title: Функция EndEnumeration (Справочник по неуправляемым API)
description: Функция EndEnumeration завершает перечисления.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65904da9efea90d31960d71ae0da8c81dffeccf1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000471"
---
# <a name="endenumeration-function"></a><span data-ttu-id="6d076-103">Функция EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="6d076-103">EndEnumeration function</span></span>

<span data-ttu-id="6d076-104">Завершает работу вызовом последовательности перечисления [функция BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6d076-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6d076-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d076-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="6d076-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6d076-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6d076-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="6d076-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6d076-108">[in] Указатель на [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6d076-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="6d076-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6d076-109">Return value</span></span>

<span data-ttu-id="6d076-110">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="6d076-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6d076-111">Константа</span><span class="sxs-lookup"><span data-stu-id="6d076-111">Constant</span></span>  |<span data-ttu-id="6d076-112">Значение</span><span class="sxs-lookup"><span data-stu-id="6d076-112">Value</span></span>  |<span data-ttu-id="6d076-113">Описание</span><span class="sxs-lookup"><span data-stu-id="6d076-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6d076-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6d076-114">0x80041001</span></span> | <span data-ttu-id="6d076-115">Произошел общий сбой.</span><span class="sxs-lookup"><span data-stu-id="6d076-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6d076-116">0</span><span class="sxs-lookup"><span data-stu-id="6d076-116">0</span></span> | <span data-ttu-id="6d076-117">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="6d076-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6d076-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="6d076-118">Remarks</span></span>

<span data-ttu-id="6d076-119">Эта функция создает оболочку для вызова [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) метод.</span><span class="sxs-lookup"><span data-stu-id="6d076-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="6d076-120">Вызов `EndEnumeration` функция не является обязательным, но рекомендуется, так как он освобождает ресурсы, связанные с перечислением.</span><span class="sxs-lookup"><span data-stu-id="6d076-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="6d076-121">Однако ресурсы освобождаются автоматически при запуске следующего перечисления или объект освобождается.</span><span class="sxs-lookup"><span data-stu-id="6d076-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="6d076-122">Требования</span><span class="sxs-lookup"><span data-stu-id="6d076-122">Requirements</span></span>

<span data-ttu-id="6d076-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d076-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6d076-124">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6d076-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6d076-125">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6d076-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6d076-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6d076-126">See also</span></span>

- [<span data-ttu-id="6d076-127">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="6d076-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)