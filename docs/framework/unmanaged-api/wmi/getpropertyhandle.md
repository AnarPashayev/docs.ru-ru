---
title: Функция GetPropertyHandle (Справочник по неуправляемым API)
description: Функция GetPropertyHandle возвращает уникальный дескриптор, который определяет свойство.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92d48caf7de873850135c7410a5e4b5861131212
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723242"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="28b8a-103">Функция GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="28b8a-103">GetPropertyHandle function</span></span>

<span data-ttu-id="28b8a-104">Возвращает уникальный маркер, определяющий свойство.</span><span class="sxs-lookup"><span data-stu-id="28b8a-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="28b8a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28b8a-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="28b8a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="28b8a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="28b8a-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="28b8a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="28b8a-108">[in] Указатель на [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="28b8a-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="28b8a-109">[in] Завершающаяся нулем строка символов в кодировке UTF16, содержащая имя свойства.</span><span class="sxs-lookup"><span data-stu-id="28b8a-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="28b8a-110">[out] Указатель на [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) член перечисления, представляющее тип CIM данного свойства.</span><span class="sxs-lookup"><span data-stu-id="28b8a-110">[out] A pointer to a [`CIMTYPE`](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="28b8a-111">[out] Указатель на целое число, которое содержит дескриптор свойства.</span><span class="sxs-lookup"><span data-stu-id="28b8a-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="28b8a-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="28b8a-112">Return value</span></span>

<span data-ttu-id="28b8a-113">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="28b8a-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="28b8a-114">Константа</span><span class="sxs-lookup"><span data-stu-id="28b8a-114">Constant</span></span>  |<span data-ttu-id="28b8a-115">Значение</span><span class="sxs-lookup"><span data-stu-id="28b8a-115">Value</span></span>  |<span data-ttu-id="28b8a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="28b8a-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="28b8a-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="28b8a-117">0x80041002</span></span> | <span data-ttu-id="28b8a-118">Свойство с указанным именем не найден.</span><span class="sxs-lookup"><span data-stu-id="28b8a-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="28b8a-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="28b8a-119">0x80041008</span></span> | <span data-ttu-id="28b8a-120">Параметр не является допустимым.</span><span class="sxs-lookup"><span data-stu-id="28b8a-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="28b8a-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="28b8a-121">0x8004100c</span></span> | <span data-ttu-id="28b8a-122">Запрошенное свойство имеет тип, `CIM_OBJECT` или `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="28b8a-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="28b8a-123">0</span><span class="sxs-lookup"><span data-stu-id="28b8a-123">0</span></span> | <span data-ttu-id="28b8a-124">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="28b8a-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="28b8a-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="28b8a-125">Remarks</span></span>

<span data-ttu-id="28b8a-126">Эта функция создает оболочку для вызова [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) метод.</span><span class="sxs-lookup"><span data-stu-id="28b8a-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="28b8a-127">Вы можете использовать этот дескриптор для идентификации свойств, при использовании [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) методы для чтения или записи значения свойств.</span><span class="sxs-lookup"><span data-stu-id="28b8a-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="28b8a-128">Дескрипторы может быть извлечен для свойства всех типов данных, отличных от `CIM_OBJECT` и `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="28b8a-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="28b8a-129">Возвращаемые дескрипторы работы для всех экземпляров класса.</span><span class="sxs-lookup"><span data-stu-id="28b8a-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="28b8a-130">Требования</span><span class="sxs-lookup"><span data-stu-id="28b8a-130">Requirements</span></span>

<span data-ttu-id="28b8a-131">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b8a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="28b8a-132">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="28b8a-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="28b8a-133">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28b8a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="28b8a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="28b8a-134">See also</span></span>

- [<span data-ttu-id="28b8a-135">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="28b8a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)