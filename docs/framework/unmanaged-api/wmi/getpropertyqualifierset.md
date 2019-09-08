---
title: Функция Жетпропертикуалифиерсет (Справочник по неуправляемым API)
description: Функция Жетпропертикуалифиерсет извлекает квалификатор, заданный для свойства.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7bce241d10051e4c6be94cdfa40de23773fb0bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798483"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="8e219-103">Функция Жетпропертикуалифиерсет</span><span class="sxs-lookup"><span data-stu-id="8e219-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="8e219-104">Получает набор квалификаторов для определенного свойства.</span><span class="sxs-lookup"><span data-stu-id="8e219-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8e219-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e219-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="8e219-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e219-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="8e219-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="8e219-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="8e219-108">окне Указатель на экземпляр [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="8e219-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="8e219-109">окне Имя свойства.</span><span class="sxs-lookup"><span data-stu-id="8e219-109">[in] The property  name.</span></span> <span data-ttu-id="8e219-110">`wszProperty`должен указывать на допустимое `LPCWSTR`значение.</span><span class="sxs-lookup"><span data-stu-id="8e219-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="8e219-111">заполняет Получает указатель интерфейса, который разрешает доступ к квалификаторам свойства.</span><span class="sxs-lookup"><span data-stu-id="8e219-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="8e219-112">Параметр `ppQualSet` не может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="8e219-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="8e219-113">При возникновении ошибки новый объект не возвращается, и указатель устанавливается на точку `null`.</span><span class="sxs-lookup"><span data-stu-id="8e219-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="8e219-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8e219-114">Return value</span></span>

<span data-ttu-id="8e219-115">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="8e219-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8e219-116">Константа</span><span class="sxs-lookup"><span data-stu-id="8e219-116">Constant</span></span>  |<span data-ttu-id="8e219-117">Значение</span><span class="sxs-lookup"><span data-stu-id="8e219-117">Value</span></span>  |<span data-ttu-id="8e219-118">Описание</span><span class="sxs-lookup"><span data-stu-id="8e219-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8e219-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8e219-119">0x80041001</span></span> | <span data-ttu-id="8e219-120">Общий сбой.</span><span class="sxs-lookup"><span data-stu-id="8e219-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="8e219-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8e219-121">0x80041002</span></span> | <span data-ttu-id="8e219-122">Указанный метод не существует.</span><span class="sxs-lookup"><span data-stu-id="8e219-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8e219-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8e219-123">0x80041006</span></span> | <span data-ttu-id="8e219-124">Недостаточно памяти для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="8e219-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8e219-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8e219-125">0x80041008</span></span> | <span data-ttu-id="8e219-126">Параметр имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="8e219-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="8e219-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="8e219-127">0x80041030</span></span> | <span data-ttu-id="8e219-128">Функция пытается получить квалификаторы системного свойства.</span><span class="sxs-lookup"><span data-stu-id="8e219-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8e219-129">0</span><span class="sxs-lookup"><span data-stu-id="8e219-129">0</span></span> | <span data-ttu-id="8e219-130">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="8e219-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8e219-131">Примечания</span><span class="sxs-lookup"><span data-stu-id="8e219-131">Remarks</span></span>

<span data-ttu-id="8e219-132">Эта функция заключает в оболочку вызов метода [ивбемклассобжект:: жетпропертикуалифиерсет](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="8e219-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="8e219-133">Вызов этой функции поддерживается только в том случае, если текущий объект является определением класса CIM.</span><span class="sxs-lookup"><span data-stu-id="8e219-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="8e219-134">Управление методами недоступно для [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) указателей, указывающих на экземпляры CIM.</span><span class="sxs-lookup"><span data-stu-id="8e219-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="8e219-135">Поскольку каждый метод может иметь собственные квалификаторы, [указатель ивбемкуалифиерсет](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) позволяет вызывающей стороне добавить, изменить или удалить эти квалификаторы.</span><span class="sxs-lookup"><span data-stu-id="8e219-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="8e219-136">Поскольку системные свойства не имеют квалификаторов, функция возвращает `WBEM_E_SYSTEM_PROPERTY` , если попытаться получить указатель [ивбемкуалифиерсет](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) для системного свойства.</span><span class="sxs-lookup"><span data-stu-id="8e219-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e219-137">Требования</span><span class="sxs-lookup"><span data-stu-id="8e219-137">Requirements</span></span>

<span data-ttu-id="8e219-138">**Платформ** См. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e219-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8e219-139">**Заголовок.** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="8e219-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="8e219-140">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8e219-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8e219-141">См. также</span><span class="sxs-lookup"><span data-stu-id="8e219-141">See also</span></span>

- [<span data-ttu-id="8e219-142">WMI и счетчики производительности (Справочник по неуправляемым интерфейсам API)</span><span class="sxs-lookup"><span data-stu-id="8e219-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
