---
title: Функция CompareTo (Справочник по неуправляемым API)
description: Функция CompareTo сравнивает объект с другим объектом WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3566b9b8a3b4183f936c82c39c38dc5daa3aeae1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636680"
---
# <a name="compareto-function"></a><span data-ttu-id="59b40-103">Функция CompareTo</span><span class="sxs-lookup"><span data-stu-id="59b40-103">CompareTo function</span></span>

<span data-ttu-id="59b40-104">Сравнивает объект с другим объектом управления Windows.</span><span class="sxs-lookup"><span data-stu-id="59b40-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="59b40-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59b40-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="59b40-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="59b40-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="59b40-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="59b40-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="59b40-108">[in] Указатель на [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="59b40-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="59b40-109">[in] Побитовое сочетание флагов, определяющих характеристики объектов, которые следует учитывать для сравнения.</span><span class="sxs-lookup"><span data-stu-id="59b40-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="59b40-110">См. в разделе ["Примечания"](#remarks) Дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="59b40-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="59b40-111">[in] Объект для сравнения.</span><span class="sxs-lookup"><span data-stu-id="59b40-111">[in] The object for comparison.</span></span> <span data-ttu-id="59b40-112">`pCompareTo` должен быть допустимым [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра; не может быть `null`.</span><span class="sxs-lookup"><span data-stu-id="59b40-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="59b40-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="59b40-113">Return value</span></span>

<span data-ttu-id="59b40-114">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="59b40-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="59b40-115">Константа</span><span class="sxs-lookup"><span data-stu-id="59b40-115">Constant</span></span>  |<span data-ttu-id="59b40-116">Значение</span><span class="sxs-lookup"><span data-stu-id="59b40-116">Value</span></span>  |<span data-ttu-id="59b40-117">Описание</span><span class="sxs-lookup"><span data-stu-id="59b40-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="59b40-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="59b40-118">0x80041001</span></span> | <span data-ttu-id="59b40-119">Произошла неизвестная ошибка.</span><span class="sxs-lookup"><span data-stu-id="59b40-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="59b40-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="59b40-120">0x80041008</span></span> | <span data-ttu-id="59b40-121">Недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="59b40-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="59b40-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="59b40-122">0x8004101d</span></span> | <span data-ttu-id="59b40-123">Второй вызов `BeginEnumeration` была сделана без промежуточных вызовов к [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="59b40-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="59b40-124">0</span><span class="sxs-lookup"><span data-stu-id="59b40-124">0</span></span> | <span data-ttu-id="59b40-125">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="59b40-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="59b40-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="59b40-126">0x40003</span></span> | <span data-ttu-id="59b40-127">Объекты различаются.</span><span class="sxs-lookup"><span data-stu-id="59b40-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="59b40-128">0</span><span class="sxs-lookup"><span data-stu-id="59b40-128">0</span></span> | <span data-ttu-id="59b40-129">Объекты одинаковы основании флаги сравнения.</span><span class="sxs-lookup"><span data-stu-id="59b40-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="59b40-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="59b40-130">Remarks</span></span>

<span data-ttu-id="59b40-131">Эта функция создает оболочку для вызова [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) метод.</span><span class="sxs-lookup"><span data-stu-id="59b40-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="59b40-132">Флаги, которые могут передаваться как `lEnumFlags` аргумент определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде.</span><span class="sxs-lookup"><span data-stu-id="59b40-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="59b40-133">Можно указать отдельные характеристики, участвующих в сравнении, указав побитовое сочетание флагов:</span><span class="sxs-lookup"><span data-stu-id="59b40-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="59b40-134">Константа</span><span class="sxs-lookup"><span data-stu-id="59b40-134">Constant</span></span>  |<span data-ttu-id="59b40-135">Значение</span><span class="sxs-lookup"><span data-stu-id="59b40-135">Value</span></span>  |<span data-ttu-id="59b40-136">Описание</span><span class="sxs-lookup"><span data-stu-id="59b40-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="59b40-137">2</span><span class="sxs-lookup"><span data-stu-id="59b40-137">2</span></span> | <span data-ttu-id="59b40-138">Не учитывать источник (сервер и пространство имен, которое они поступили).</span><span class="sxs-lookup"><span data-stu-id="59b40-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="59b40-139">1</span><span class="sxs-lookup"><span data-stu-id="59b40-139">1</span></span> | <span data-ttu-id="59b40-140">Игнорировать все квалификаторы (включая **ключ** и **динамическое**)</span><span class="sxs-lookup"><span data-stu-id="59b40-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="59b40-141">4</span><span class="sxs-lookup"><span data-stu-id="59b40-141">4</span></span> | <span data-ttu-id="59b40-142">Игнорировать значения свойств по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="59b40-142">Ignore default values of properties.</span></span> <span data-ttu-id="59b40-143">Этот флаг применяется только к сравнения классов.</span><span class="sxs-lookup"><span data-stu-id="59b40-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="59b40-144">0x20</span><span class="sxs-lookup"><span data-stu-id="59b40-144">0x20</span></span> | <span data-ttu-id="59b40-145">Игнорируйте квалификаторов.</span><span class="sxs-lookup"><span data-stu-id="59b40-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="59b40-146">Этот флаг по-прежнему учитывает квалификаторы, но игнорирует такие правила распространения и ограничения.</span><span class="sxs-lookup"><span data-stu-id="59b40-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="59b40-147">0x10</span><span class="sxs-lookup"><span data-stu-id="59b40-147">0x10</span></span> | <span data-ttu-id="59b40-148">Не учитывать регистр при сравнении строковых значений.</span><span class="sxs-lookup"><span data-stu-id="59b40-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="59b40-149">Это относится как к строкам и значения квалификатора.</span><span class="sxs-lookup"><span data-stu-id="59b40-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="59b40-150">Сравнение имен свойств и квалификаторов всегда выполняется с учетом регистра, независимо от того, является ли этот флаг установлен.</span><span class="sxs-lookup"><span data-stu-id="59b40-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="59b40-151">0x8</span><span class="sxs-lookup"><span data-stu-id="59b40-151">0x8</span></span> | <span data-ttu-id="59b40-152">Предположим, что сравниваемые объекты являются экземплярами одного класса.</span><span class="sxs-lookup"><span data-stu-id="59b40-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="59b40-153">Следовательно этот флаг сравнивает только сведения, относящиеся к экземпляру.</span><span class="sxs-lookup"><span data-stu-id="59b40-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="59b40-154">Используйте это флаги для оптимизации производительности.</span><span class="sxs-lookup"><span data-stu-id="59b40-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="59b40-155">Если объекты не имеют одного класса, результаты будут неопределенными.</span><span class="sxs-lookup"><span data-stu-id="59b40-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="59b40-156">Или одного составного флага можно указать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="59b40-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="59b40-157">Константа</span><span class="sxs-lookup"><span data-stu-id="59b40-157">Constant</span></span>  |<span data-ttu-id="59b40-158">Значение</span><span class="sxs-lookup"><span data-stu-id="59b40-158">Value</span></span>  |<span data-ttu-id="59b40-159">Описание</span><span class="sxs-lookup"><span data-stu-id="59b40-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="59b40-160">0</span><span class="sxs-lookup"><span data-stu-id="59b40-160">0</span></span> | <span data-ttu-id="59b40-161">Учитывать все характеристики в сравнении.</span><span class="sxs-lookup"><span data-stu-id="59b40-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="59b40-162">Требования</span><span class="sxs-lookup"><span data-stu-id="59b40-162">Requirements</span></span>

<span data-ttu-id="59b40-163">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b40-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="59b40-164">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="59b40-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="59b40-165">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59b40-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="59b40-166">См. также</span><span class="sxs-lookup"><span data-stu-id="59b40-166">See also</span></span>

- [<span data-ttu-id="59b40-167">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="59b40-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
