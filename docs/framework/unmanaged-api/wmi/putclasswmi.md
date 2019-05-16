---
title: Функция PutClassWmi (Справочник по неуправляемым API)
description: Функция PutClassWmi создает новый класс или обновляет существующий.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422de614d2e2ddb93cc1e932a8672e1e8269b2c0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636645"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="c7883-103">Функция PutClassWmi</span><span class="sxs-lookup"><span data-stu-id="c7883-103">PutClassWmi function</span></span>

<span data-ttu-id="c7883-104">Создает новый класс или обновляет существующий.</span><span class="sxs-lookup"><span data-stu-id="c7883-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c7883-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c7883-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="c7883-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c7883-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="c7883-107">[in] Указатель является допустимым определением класса.</span><span class="sxs-lookup"><span data-stu-id="c7883-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="c7883-108">Его необходимо правильно инициализировать со всеми значениями обязательное свойство.</span><span class="sxs-lookup"><span data-stu-id="c7883-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="c7883-109">[in] Сочетание флагов, влияющих на поведение этой функции.</span><span class="sxs-lookup"><span data-stu-id="c7883-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="c7883-110">Следующие значения определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="c7883-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7883-111">Константа</span><span class="sxs-lookup"><span data-stu-id="c7883-111">Constant</span></span>  |<span data-ttu-id="c7883-112">Значение</span><span class="sxs-lookup"><span data-stu-id="c7883-112">Value</span></span>  |<span data-ttu-id="c7883-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c7883-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="c7883-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="c7883-114">0x20000</span></span> | <span data-ttu-id="c7883-115">Если набор, WMI не сохраняет любые квалификаторы с измененная версия.</span><span class="sxs-lookup"><span data-stu-id="c7883-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="c7883-116">В противном случае набор, предполагается, что этот объект не локализован, а все квалификаторы хранятся с этим экземпляром.</span><span class="sxs-lookup"><span data-stu-id="c7883-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="c7883-117">0</span><span class="sxs-lookup"><span data-stu-id="c7883-117">0</span></span> | <span data-ttu-id="c7883-118">Создайте класс, если он не существует, или заменяет его, если он уже существует.</span><span class="sxs-lookup"><span data-stu-id="c7883-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="c7883-119">1</span><span class="sxs-lookup"><span data-stu-id="c7883-119">1</span></span> | <span data-ttu-id="c7883-120">Обновите класс.</span><span class="sxs-lookup"><span data-stu-id="c7883-120">Update the class.</span></span> <span data-ttu-id="c7883-121">Класс должен существовать для успешного вызова.</span><span class="sxs-lookup"><span data-stu-id="c7883-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="c7883-122">2</span><span class="sxs-lookup"><span data-stu-id="c7883-122">2</span></span> | <span data-ttu-id="c7883-123">Создайте класс.</span><span class="sxs-lookup"><span data-stu-id="c7883-123">Create the class.</span></span> <span data-ttu-id="c7883-124">Вызов завершается неудачей, если класс уже существует.</span><span class="sxs-lookup"><span data-stu-id="c7883-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="c7883-125">0x10</span><span class="sxs-lookup"><span data-stu-id="c7883-125">0x10</span></span> | <span data-ttu-id="c7883-126">Этот флаг приводит к Полусинхронный вызов.</span><span class="sxs-lookup"><span data-stu-id="c7883-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="c7883-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="c7883-127">0x10000</span></span> | <span data-ttu-id="c7883-128">Поставщики Push-уведомлений необходимо указать этот флаг, при вызове `PutClassWmi` для указания, что этот класс был изменен.</span><span class="sxs-lookup"><span data-stu-id="c7883-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="c7883-129">0</span><span class="sxs-lookup"><span data-stu-id="c7883-129">0</span></span> | <span data-ttu-id="c7883-130">Позволяет классу обновляться, если нет производных классов и экземпляры этого класса не существует.</span><span class="sxs-lookup"><span data-stu-id="c7883-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="c7883-131">Он также позволяет обновления во всех случаях при изменении просто незначительной квалификаторы, например квалификатор описания.</span><span class="sxs-lookup"><span data-stu-id="c7883-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="c7883-132">Если класс имеет экземпляры или изменяются важные квалификаторы, обновление завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c7883-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="c7883-133">0x20</span><span class="sxs-lookup"><span data-stu-id="c7883-133">0x20</span></span> | <span data-ttu-id="c7883-134">Обеспечивает обновление классов, даже при наличии дочерних классов, до тех пор, пока изменения не вызывает конфликтов с дочерними классами.</span><span class="sxs-lookup"><span data-stu-id="c7883-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="c7883-135">Например этот флаг позволяет новое свойство для добавления базового класса, который не упоминался ранее в любом из дочерних классов.</span><span class="sxs-lookup"><span data-stu-id="c7883-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="c7883-136">Если класс имеет экземпляры, обновление завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c7883-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="c7883-137">0x40</span><span class="sxs-lookup"><span data-stu-id="c7883-137">0x40</span></span> | <span data-ttu-id="c7883-138">Принудительное обновление классов, при наличии конфликтующих дочерних классов.</span><span class="sxs-lookup"><span data-stu-id="c7883-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="c7883-139">Например этот флаг вызывает принудительное обновление Если квалификатор определен в дочернем классе, и пытается добавить в базовый класс который конфликтует с существующей.</span><span class="sxs-lookup"><span data-stu-id="c7883-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="c7883-140">В принудительном режиме еще привлекательнее конфликт разрешается удалением квалификатора в дочернем классе.</span><span class="sxs-lookup"><span data-stu-id="c7883-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="c7883-141">[in] Как правило, это значение равно `null`.</span><span class="sxs-lookup"><span data-stu-id="c7883-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="c7883-142">В противном случае он является указателем на [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) экземпляр, который может использоваться поставщиком, предоставляющего запрошенного классы.</span><span class="sxs-lookup"><span data-stu-id="c7883-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="c7883-143">[out] Если `null`, этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="c7883-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="c7883-144">Если `lFlags` содержит `WBEM_FLAG_RETURN_IMMEDIATELY`, функция немедленно возвращает `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="c7883-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="c7883-145">`ppCallResult` Параметр получает указатель на новый [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) объекта.</span><span class="sxs-lookup"><span data-stu-id="c7883-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7883-146">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c7883-146">Return value</span></span>

<span data-ttu-id="c7883-147">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="c7883-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7883-148">Константа</span><span class="sxs-lookup"><span data-stu-id="c7883-148">Constant</span></span>  |<span data-ttu-id="c7883-149">Значение</span><span class="sxs-lookup"><span data-stu-id="c7883-149">Value</span></span>  |<span data-ttu-id="c7883-150">Описание</span><span class="sxs-lookup"><span data-stu-id="c7883-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="c7883-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="c7883-151">0x80041003</span></span> | <span data-ttu-id="c7883-152">Пользователь не имеет разрешения на создание или изменение классов.</span><span class="sxs-lookup"><span data-stu-id="c7883-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="c7883-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c7883-153">0x80041001</span></span> | <span data-ttu-id="c7883-154">Произошла неизвестная ошибка.</span><span class="sxs-lookup"><span data-stu-id="c7883-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="c7883-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="c7883-155">0x80041010</span></span> | <span data-ttu-id="c7883-156">Указанный класс не является допустимым.</span><span class="sxs-lookup"><span data-stu-id="c7883-156">The specified class is not valid.</span></span> <span data-ttu-id="c7883-157">Как правило, это означает, что `pObject` указывает объект экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c7883-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c7883-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c7883-158">0x80041008</span></span> | <span data-ttu-id="c7883-159">Параметр не является допустимым.</span><span class="sxs-lookup"><span data-stu-id="c7883-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="c7883-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c7883-160">0x80041016</span></span> | <span data-ttu-id="c7883-161">Недопустимое имя указанного класса.</span><span class="sxs-lookup"><span data-stu-id="c7883-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="c7883-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="c7883-162">0x80041025</span></span> | <span data-ttu-id="c7883-163">Выполнена попытка сделать изменение, которое аннулирует подкласс.</span><span class="sxs-lookup"><span data-stu-id="c7883-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="c7883-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="c7883-164">0x80041019</span></span> | <span data-ttu-id="c7883-165">`WBEM_FLAG_CREATE_ONLY` Указан флаг, но класс уже существует.</span><span class="sxs-lookup"><span data-stu-id="c7883-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="c7883-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c7883-166">0x80041002</span></span> | <span data-ttu-id="c7883-167">`WBEM_FLAG_UPDATE_ONLY` был указан в `lFlags`, и этот класс не найден.</span><span class="sxs-lookup"><span data-stu-id="c7883-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="c7883-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="c7883-168">0x80041020</span></span> | <span data-ttu-id="c7883-169">Обязательные свойства для классов не все установлены.</span><span class="sxs-lookup"><span data-stu-id="c7883-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c7883-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c7883-170">0x80041006</span></span> | <span data-ttu-id="c7883-171">Недостаточно памяти для завершения операции.</span><span class="sxs-lookup"><span data-stu-id="c7883-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="c7883-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="c7883-172">0x80041033</span></span> | <span data-ttu-id="c7883-173">WMI был, вероятно, остановлена или перезапустить.</span><span class="sxs-lookup"><span data-stu-id="c7883-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="c7883-174">Вызовите [ConnectServerWmi](connectserverwmi.md) еще раз.</span><span class="sxs-lookup"><span data-stu-id="c7883-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="c7883-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="c7883-175">0x80041015</span></span> | <span data-ttu-id="c7883-176">Сбой удаленной процедуры вызова (RPC) связь между текущим процессом и WMI.</span><span class="sxs-lookup"><span data-stu-id="c7883-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c7883-177">0</span><span class="sxs-lookup"><span data-stu-id="c7883-177">0</span></span> | <span data-ttu-id="c7883-178">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="c7883-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c7883-179">Примечания</span><span class="sxs-lookup"><span data-stu-id="c7883-179">Remarks</span></span>

<span data-ttu-id="c7883-180">Эта функция создает оболочку для вызова [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) метод.</span><span class="sxs-lookup"><span data-stu-id="c7883-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="c7883-181">Пользователь не может создать классы с именами, начинаться или заканчиваться символом подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="c7883-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="c7883-182">Если происходит сбой вызова функции, можно получить дополнительные сведения об ошибке, вызвав [GetErrorInfo](geterrorinfo.md) функции.</span><span class="sxs-lookup"><span data-stu-id="c7883-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7883-183">Требования</span><span class="sxs-lookup"><span data-stu-id="c7883-183">Requirements</span></span>

<span data-ttu-id="c7883-184">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7883-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c7883-185">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7883-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="c7883-186">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7883-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c7883-187">См. также</span><span class="sxs-lookup"><span data-stu-id="c7883-187">See also</span></span>

- [<span data-ttu-id="c7883-188">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="c7883-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
