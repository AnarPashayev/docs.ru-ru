---
title: Функция CloneEnumWbemClassObject (Справочник по неуправляемым API)
description: Функция CloneEnumWbemClassObject создается копия логического перечислитель.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab660769a49cf12b129cb7f44b8378053a231f8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761625"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="a475c-103">Функция CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="a475c-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="a475c-104">Создает логическую копию перечислителя, сохраняя текущую позицию в перечислении.</span><span class="sxs-lookup"><span data-stu-id="a475c-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a475c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a475c-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a><span data-ttu-id="a475c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a475c-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="a475c-107">[out] Получает указатель на новый [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="a475c-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="a475c-108">[in] Уровень авторизации.</span><span class="sxs-lookup"><span data-stu-id="a475c-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="a475c-109">[in] Уровень олицетворения.</span><span class="sxs-lookup"><span data-stu-id="a475c-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="a475c-110">[out] Указатель на [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) экземпляра для клонирования.</span><span class="sxs-lookup"><span data-stu-id="a475c-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="a475c-111">[in] Имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="a475c-111">[in] The user name.</span></span> <span data-ttu-id="a475c-112">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="a475c-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="a475c-113">[in] Пароль.</span><span class="sxs-lookup"><span data-stu-id="a475c-113">[in] The password.</span></span> <span data-ttu-id="a475c-114">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="a475c-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="a475c-115">`strAuthority`\ [in] имя домена пользователя.</span><span class="sxs-lookup"><span data-stu-id="a475c-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="a475c-116">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="a475c-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="a475c-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a475c-117">Return value</span></span>

<span data-ttu-id="a475c-118">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="a475c-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a475c-119">Константа</span><span class="sxs-lookup"><span data-stu-id="a475c-119">Constant</span></span>  |<span data-ttu-id="a475c-120">Значение</span><span class="sxs-lookup"><span data-stu-id="a475c-120">Value</span></span>  |<span data-ttu-id="a475c-121">Описание</span><span class="sxs-lookup"><span data-stu-id="a475c-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="a475c-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a475c-122">0x80041001</span></span> | <span data-ttu-id="a475c-123">Произошел общий сбой.</span><span class="sxs-lookup"><span data-stu-id="a475c-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a475c-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a475c-124">0x80041008</span></span> | <span data-ttu-id="a475c-125">Недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="a475c-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a475c-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a475c-126">0x80041006</span></span> | <span data-ttu-id="a475c-127">Не хватает памяти завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="a475c-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="a475c-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="a475c-128">0x80041015</span></span> | <span data-ttu-id="a475c-129">Сбой удаленной процедуры вызова (RPC) связь между текущим процессом и WMI.</span><span class="sxs-lookup"><span data-stu-id="a475c-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a475c-130">0</span><span class="sxs-lookup"><span data-stu-id="a475c-130">0</span></span> | <span data-ttu-id="a475c-131">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="a475c-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a475c-132">Примечания</span><span class="sxs-lookup"><span data-stu-id="a475c-132">Remarks</span></span>

<span data-ttu-id="a475c-133">Эта функция создает оболочку для вызова [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) метод.</span><span class="sxs-lookup"><span data-stu-id="a475c-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="a475c-134">Этот метод копирует только «оптимальных затрат».</span><span class="sxs-lookup"><span data-stu-id="a475c-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="a475c-135">Из-за динамической природы множество объектов CIM вполне возможно, что новый перечислитель не перечислить тот же набор объектов, что перечислитель источника.</span><span class="sxs-lookup"><span data-stu-id="a475c-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="a475c-136">Если происходит сбой вызова функции, можно получить дополнительные сведения об ошибке, вызвав [GetErrorInfo](geterrorinfo.md) функции.</span><span class="sxs-lookup"><span data-stu-id="a475c-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="a475c-137">Пример</span><span class="sxs-lookup"><span data-stu-id="a475c-137">Example</span></span>

<span data-ttu-id="a475c-138">Например, см. в разделе [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) метод.</span><span class="sxs-lookup"><span data-stu-id="a475c-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a475c-139">Требования</span><span class="sxs-lookup"><span data-stu-id="a475c-139">Requirements</span></span>
 <span data-ttu-id="a475c-140">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a475c-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a475c-141">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a475c-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="a475c-142">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a475c-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a475c-143">См. также</span><span class="sxs-lookup"><span data-stu-id="a475c-143">See also</span></span>

- [<span data-ttu-id="a475c-144">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="a475c-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
