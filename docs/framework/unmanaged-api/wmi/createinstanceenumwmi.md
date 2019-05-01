---
title: Функция CreateInstanceEnumWmi (Справочник по неуправляемым API)
description: Функция CreateInstanceEnumWmi Возвращает перечислитель, содержащий экземпляры указанного класса, которые соответствуют критериям выбора.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a1d082cae19bd83c90e063d841a0c9e4602bc40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040707"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="0d3dc-103">CreateInstanceEnumWmi function</span><span class="sxs-lookup"><span data-stu-id="0d3dc-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="0d3dc-104">Возвращает перечислитель, возвращающий экземпляры указанного класса в соответствии с заданными критериями выбора.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0d3dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d3dc-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="0d3dc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d3dc-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="0d3dc-107">[in] Имя класса, для которого требуются экземпляры.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="0d3dc-108">Этот параметр не может быть `null`.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="0d3dc-109">[in] Сочетание флагов, влияющих на поведение этой функции.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="0d3dc-110">Следующие значения определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="0d3dc-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0d3dc-111">Константа</span><span class="sxs-lookup"><span data-stu-id="0d3dc-111">Constant</span></span>  |<span data-ttu-id="0d3dc-112">Значение</span><span class="sxs-lookup"><span data-stu-id="0d3dc-112">Value</span></span>  |<span data-ttu-id="0d3dc-113">Описание</span><span class="sxs-lookup"><span data-stu-id="0d3dc-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="0d3dc-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="0d3dc-114">0x20000</span></span> | <span data-ttu-id="0d3dc-115">Если набор, функция извлекает измененные квалификаторы, хранящиеся в локализованных имен языкового стандарта текущего соединения.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="0d3dc-116">В противном случае набор, функция получает только квалификаторы, хранящихся в пространство имен немедленно.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="0d3dc-117">0</span><span class="sxs-lookup"><span data-stu-id="0d3dc-117">0</span></span> | <span data-ttu-id="0d3dc-118">Перечисление включает в себя это и всех подклассов в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="0d3dc-119">1</span><span class="sxs-lookup"><span data-stu-id="0d3dc-119">1</span></span> | <span data-ttu-id="0d3dc-120">Перечисление содержит только чистые экземпляры этого класса и исключает все экземпляры из подклассов, которые предоставляют свойства, не найден в этом классе.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="0d3dc-121">0x10</span><span class="sxs-lookup"><span data-stu-id="0d3dc-121">0x10</span></span> | <span data-ttu-id="0d3dc-122">Этот флаг приводит к Полусинхронный вызов.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="0d3dc-123">0x20</span><span class="sxs-lookup"><span data-stu-id="0d3dc-123">0x20</span></span> | <span data-ttu-id="0d3dc-124">Функция возвращает только вперед перечислителя.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="0d3dc-125">Обычно перечислители только вперед, выполняются быстрее и использовать меньше памяти, чем обычные перечислители, но они не допускают вызовы [клона](clone.md).</span><span class="sxs-lookup"><span data-stu-id="0d3dc-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="0d3dc-126">0</span><span class="sxs-lookup"><span data-stu-id="0d3dc-126">0</span></span> | <span data-ttu-id="0d3dc-127">WMI сохраняет указатели на объекты в перечислении, до их появления.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="0d3dc-128">Рекомендуемые флаги `WBEM_FLAG_RETURN_IMMEDIATELY` и `WBEM_FLAG_FORWARD_ONLY` для достижения оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="0d3dc-129">[in] Как правило, это значение равно `null`.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="0d3dc-130">В противном случае он является указателем на [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) экземпляр, который может использоваться поставщиком, предоставляющего запрошенного экземпляров.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="0d3dc-131">[out] Получает указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="0d3dc-132">[in] Уровень авторизации.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="0d3dc-133">[in] Уровень олицетворения.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="0d3dc-134">[in] Указатель на [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) объект, представляющий текущее пространство имен.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="0d3dc-135">[in] Имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-135">[in] The user name.</span></span> <span data-ttu-id="0d3dc-136">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="0d3dc-137">[in] Пароль.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-137">[in] The password.</span></span> <span data-ttu-id="0d3dc-138">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="0d3dc-139">[in] Имя домена пользователя.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-139">[in] The domain name of the user.</span></span> <span data-ttu-id="0d3dc-140">См. в разделе [ConnectServerWmi](connectserverwmi.md) функции подробнее.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d3dc-141">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0d3dc-141">Return value</span></span>

<span data-ttu-id="0d3dc-142">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="0d3dc-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0d3dc-143">Константа</span><span class="sxs-lookup"><span data-stu-id="0d3dc-143">Constant</span></span>  |<span data-ttu-id="0d3dc-144">Значение</span><span class="sxs-lookup"><span data-stu-id="0d3dc-144">Value</span></span>  |<span data-ttu-id="0d3dc-145">Описание</span><span class="sxs-lookup"><span data-stu-id="0d3dc-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="0d3dc-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="0d3dc-146">0x80041003</span></span> | <span data-ttu-id="0d3dc-147">Пользователь не имеет разрешения на просмотр экземпляры указанного класса.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="0d3dc-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0d3dc-148">0x80041001</span></span> | <span data-ttu-id="0d3dc-149">Произошла неизвестная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="0d3dc-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="0d3dc-150">0x80041010</span></span> | <span data-ttu-id="0d3dc-151">`strFilter` — не существует.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0d3dc-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0d3dc-152">0x80041008</span></span> | <span data-ttu-id="0d3dc-153">Параметр не является допустимым.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0d3dc-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0d3dc-154">0x80041006</span></span> | <span data-ttu-id="0d3dc-155">Недостаточно памяти для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="0d3dc-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="0d3dc-156">0x80041033</span></span> | <span data-ttu-id="0d3dc-157">WMI был, вероятно, остановлена или перезапустить.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="0d3dc-158">Вызовите [ConnectServerWmi](connectserverwmi.md) еще раз.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="0d3dc-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="0d3dc-159">0x80041015</span></span> | <span data-ttu-id="0d3dc-160">Сбой удаленной процедуры вызова (RPC) связь между текущим процессом и WMI.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0d3dc-161">0</span><span class="sxs-lookup"><span data-stu-id="0d3dc-161">0</span></span> | <span data-ttu-id="0d3dc-162">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0d3dc-163">Примечания</span><span class="sxs-lookup"><span data-stu-id="0d3dc-163">Remarks</span></span>

<span data-ttu-id="0d3dc-164">Эта функция создает оболочку для вызова [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) метод.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="0d3dc-165">Обратите внимание, что возвращенный перечислитель может иметь ноль элементов.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="0d3dc-166">Если происходит сбой вызова функции, можно получить дополнительные сведения об ошибке, вызвав [GetErrorInfo](geterrorinfo.md) функции.</span><span class="sxs-lookup"><span data-stu-id="0d3dc-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d3dc-167">Требования</span><span class="sxs-lookup"><span data-stu-id="0d3dc-167">Requirements</span></span>

<span data-ttu-id="0d3dc-168">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d3dc-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="0d3dc-169">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0d3dc-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="0d3dc-170">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0d3dc-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0d3dc-171">См. также</span><span class="sxs-lookup"><span data-stu-id="0d3dc-171">See also</span></span>

- [<span data-ttu-id="0d3dc-172">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="0d3dc-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)