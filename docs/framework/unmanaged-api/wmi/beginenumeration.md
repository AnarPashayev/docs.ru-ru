---
title: Функция BeginEnumeration (Справочник по неуправляемым API)
description: Функция BeginEnumeration устанавливает перечислитель в начало перечисления
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4221dbea2b5ad98f889e04eb8a9b6d992b59066e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212301"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="92846-103">Функция BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="92846-103">BeginEnumeration function</span></span>
<span data-ttu-id="92846-104">Сбрасывает перечислитель на начало перечисления.</span><span class="sxs-lookup"><span data-stu-id="92846-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="92846-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92846-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="92846-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92846-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="92846-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="92846-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="92846-108">[in] Указатель на [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="92846-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="92846-109">[in] Побитовое сочетание флагов или значения, описанные в ["Примечания"](#remarks) раздел, который управляет свойствами включена в перечисление.</span><span class="sxs-lookup"><span data-stu-id="92846-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="92846-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="92846-110">Return value</span></span>

<span data-ttu-id="92846-111">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="92846-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="92846-112">Константа</span><span class="sxs-lookup"><span data-stu-id="92846-112">Constant</span></span>  |<span data-ttu-id="92846-113">Значение</span><span class="sxs-lookup"><span data-stu-id="92846-113">Value</span></span>  |<span data-ttu-id="92846-114">Описание</span><span class="sxs-lookup"><span data-stu-id="92846-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="92846-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="92846-115">0x80041008</span></span> | <span data-ttu-id="92846-116">Комбинация флагов в `lEnumFlags` недопустим или указан недопустимый аргумент был указан.</span><span class="sxs-lookup"><span data-stu-id="92846-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="92846-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="92846-117">0x8004101d</span></span> | <span data-ttu-id="92846-118">Второй вызов `BeginEnumeration` была сделана без промежуточных вызовов к [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="92846-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="92846-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="92846-119">0x80041006</span></span> | <span data-ttu-id="92846-120">Не хватает памяти, позволяющих начать новое перечисление.</span><span class="sxs-lookup"><span data-stu-id="92846-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="92846-121">0</span><span class="sxs-lookup"><span data-stu-id="92846-121">0</span></span> | <span data-ttu-id="92846-122">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="92846-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="92846-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="92846-123">Remarks</span></span>

<span data-ttu-id="92846-124">Эта функция создает оболочку для вызова [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) метод.</span><span class="sxs-lookup"><span data-stu-id="92846-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="92846-125">Флаги, которые могут передаваться как `lEnumFlags` аргумент определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде.</span><span class="sxs-lookup"><span data-stu-id="92846-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="92846-126">Вы можете объединить один флаг из каждой группы с любой флаг из другой группы.</span><span class="sxs-lookup"><span data-stu-id="92846-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="92846-127">Однако флаги из одной группы являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="92846-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="92846-128">**Группа 1**</span><span class="sxs-lookup"><span data-stu-id="92846-128">**Group 1**</span></span>

|<span data-ttu-id="92846-129">Константа</span><span class="sxs-lookup"><span data-stu-id="92846-129">Constant</span></span>  |<span data-ttu-id="92846-130">Значение</span><span class="sxs-lookup"><span data-stu-id="92846-130">Value</span></span>  |<span data-ttu-id="92846-131">Описание</span><span class="sxs-lookup"><span data-stu-id="92846-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="92846-132">0x4</span><span class="sxs-lookup"><span data-stu-id="92846-132">0x4</span></span> | <span data-ttu-id="92846-133">Включают свойства, которые составляют только ключ.</span><span class="sxs-lookup"><span data-stu-id="92846-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="92846-134">0x8</span><span class="sxs-lookup"><span data-stu-id="92846-134">0x8</span></span> | <span data-ttu-id="92846-135">Включают свойства, которые являются только ссылки на объекты.</span><span class="sxs-lookup"><span data-stu-id="92846-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="92846-136">**Группа 2**</span><span class="sxs-lookup"><span data-stu-id="92846-136">**Group 2**</span></span>

<span data-ttu-id="92846-137">Константа</span><span class="sxs-lookup"><span data-stu-id="92846-137">Constant</span></span>  |<span data-ttu-id="92846-138">Значение</span><span class="sxs-lookup"><span data-stu-id="92846-138">Value</span></span>  |<span data-ttu-id="92846-139">Описание</span><span class="sxs-lookup"><span data-stu-id="92846-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="92846-140">0x30</span><span class="sxs-lookup"><span data-stu-id="92846-140">0x30</span></span> | <span data-ttu-id="92846-141">Ограничения перечисления только системные свойства.</span><span class="sxs-lookup"><span data-stu-id="92846-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="92846-142">0x40</span><span class="sxs-lookup"><span data-stu-id="92846-142">0x40</span></span> | <span data-ttu-id="92846-143">Включает локальные и распространенных свойств, но исключает системные свойства из перечисления.</span><span class="sxs-lookup"><span data-stu-id="92846-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="92846-144">Для классов:</span><span class="sxs-lookup"><span data-stu-id="92846-144">For classes:</span></span>

<span data-ttu-id="92846-145">Константа</span><span class="sxs-lookup"><span data-stu-id="92846-145">Constant</span></span>  |<span data-ttu-id="92846-146">Значение</span><span class="sxs-lookup"><span data-stu-id="92846-146">Value</span></span>  |<span data-ttu-id="92846-147">Описание</span><span class="sxs-lookup"><span data-stu-id="92846-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="92846-148">0x100</span><span class="sxs-lookup"><span data-stu-id="92846-148">0x100</span></span> | <span data-ttu-id="92846-149">Ограничения перечисления для свойства при переопределении в определении класса.</span><span class="sxs-lookup"><span data-stu-id="92846-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="92846-150">0x100</span><span class="sxs-lookup"><span data-stu-id="92846-150">0x100</span></span> | <span data-ttu-id="92846-151">Ограничения перечисления для свойства, переопределить в определении текущего класса и новые свойства, определенные в классе.</span><span class="sxs-lookup"><span data-stu-id="92846-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="92846-152">0x300</span><span class="sxs-lookup"><span data-stu-id="92846-152">0x300</span></span> | <span data-ttu-id="92846-153">Объект маскировать (а не флаг) для применения к `lEnumFlags` значение для проверки, если параметр `WBEM_FLAG_CLASS_OVERRIDES_ONLY` или `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` имеет значение.</span><span class="sxs-lookup"><span data-stu-id="92846-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="92846-154">0x10</span><span class="sxs-lookup"><span data-stu-id="92846-154">0x10</span></span> | <span data-ttu-id="92846-155">Ограничения перечисления для свойства, которые определены или являются изменения в самом классе.</span><span class="sxs-lookup"><span data-stu-id="92846-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="92846-156">0x20</span><span class="sxs-lookup"><span data-stu-id="92846-156">0x20</span></span> | <span data-ttu-id="92846-157">Ограничения перечисления для свойства, наследуемые от базовых классов.</span><span class="sxs-lookup"><span data-stu-id="92846-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="92846-158">Для экземпляров:</span><span class="sxs-lookup"><span data-stu-id="92846-158">For instances:</span></span>

<span data-ttu-id="92846-159">Константа</span><span class="sxs-lookup"><span data-stu-id="92846-159">Constant</span></span>  |<span data-ttu-id="92846-160">Значение</span><span class="sxs-lookup"><span data-stu-id="92846-160">Value</span></span>  |<span data-ttu-id="92846-161">Описание</span><span class="sxs-lookup"><span data-stu-id="92846-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="92846-162">0x10</span><span class="sxs-lookup"><span data-stu-id="92846-162">0x10</span></span> | <span data-ttu-id="92846-163">Ограничения перечисления для свойства, которые определены или являются изменения в самом классе.</span><span class="sxs-lookup"><span data-stu-id="92846-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="92846-164">0x20</span><span class="sxs-lookup"><span data-stu-id="92846-164">0x20</span></span> | <span data-ttu-id="92846-165">Ограничения перечисления для свойства, наследуемые от базовых классов.</span><span class="sxs-lookup"><span data-stu-id="92846-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="92846-166">Требования</span><span class="sxs-lookup"><span data-stu-id="92846-166">Requirements</span></span>  
 <span data-ttu-id="92846-167">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92846-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92846-168">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="92846-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="92846-169">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92846-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92846-170">См. также</span><span class="sxs-lookup"><span data-stu-id="92846-170">See also</span></span>

- [<span data-ttu-id="92846-171">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="92846-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)