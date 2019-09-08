---
title: Функция Путмесод (Справочник по неуправляемым API)
description: Функция Путмесод создает метод.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798366"
---
# <a name="putmethod-function"></a><span data-ttu-id="6716c-103">Функция Путмесод</span><span class="sxs-lookup"><span data-stu-id="6716c-103">PutMethod function</span></span>
<span data-ttu-id="6716c-104">Создает метод.</span><span class="sxs-lookup"><span data-stu-id="6716c-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6716c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6716c-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="6716c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6716c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6716c-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="6716c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6716c-108">окне Указатель на экземпляр [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="6716c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="6716c-109">окне Имя создаваемого метода.</span><span class="sxs-lookup"><span data-stu-id="6716c-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="6716c-110">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="6716c-110">[in] Reserved.</span></span> <span data-ttu-id="6716c-111">Этот параметр должен иметь значение 0.</span><span class="sxs-lookup"><span data-stu-id="6716c-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="6716c-112">окне Указатель на копию [системного класса __Parameters](/windows/desktop/WmiSdk/--parameters) , которая содержит `in` параметры для метода.</span><span class="sxs-lookup"><span data-stu-id="6716c-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="6716c-113">Этот параметр игнорируется, если имеет `null`значение.</span><span class="sxs-lookup"><span data-stu-id="6716c-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="6716c-114">окне  Указатель на копию [системного класса __Parameters](/windows/desktop/WmiSdk/--parameters) , которая содержит `out` параметры для метода.</span><span class="sxs-lookup"><span data-stu-id="6716c-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="6716c-115">Этот параметр игнорируется, если имеет `null`значение.</span><span class="sxs-lookup"><span data-stu-id="6716c-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6716c-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6716c-116">Return value</span></span>

<span data-ttu-id="6716c-117">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="6716c-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6716c-118">Константа</span><span class="sxs-lookup"><span data-stu-id="6716c-118">Constant</span></span>  |<span data-ttu-id="6716c-119">Значение</span><span class="sxs-lookup"><span data-stu-id="6716c-119">Value</span></span>  |<span data-ttu-id="6716c-120">Описание</span><span class="sxs-lookup"><span data-stu-id="6716c-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6716c-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6716c-121">0x80041008</span></span> | <span data-ttu-id="6716c-122">Один или несколько параметров недопустимы.</span><span class="sxs-lookup"><span data-stu-id="6716c-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="6716c-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="6716c-123">0x80041043</span></span> | <span data-ttu-id="6716c-124">Параметр метода, указанный в объектах *пинсигнатуре* и паутсигнатуре, имеет разные квалификаторы. `[in, out]`</span><span class="sxs-lookup"><span data-stu-id="6716c-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="6716c-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="6716c-125">0x80041036</span></span> | <span data-ttu-id="6716c-126">В параметре метода отсутствует спецификация квалификатора **идентификатора** .</span><span class="sxs-lookup"><span data-stu-id="6716c-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="6716c-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="6716c-127">0x80041038</span></span> | <span data-ttu-id="6716c-128">Серия ИДЕНТИФИКАТОРов, назначенных параметрам метода, не является последовательным или не начинается с 0.</span><span class="sxs-lookup"><span data-stu-id="6716c-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="6716c-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="6716c-129">0x80041039</span></span> | <span data-ttu-id="6716c-130">Возвращаемое значение метода имеет квалификатор **идентификатора** .</span><span class="sxs-lookup"><span data-stu-id="6716c-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="6716c-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="6716c-131">0x80041034</span></span> | <span data-ttu-id="6716c-132">Предпринята попытка повторно использовать существующее имя метода из родительского класса, и подписи не совпали.</span><span class="sxs-lookup"><span data-stu-id="6716c-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6716c-133">0</span><span class="sxs-lookup"><span data-stu-id="6716c-133">0</span></span> | <span data-ttu-id="6716c-134">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="6716c-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6716c-135">Примечания</span><span class="sxs-lookup"><span data-stu-id="6716c-135">Remarks</span></span>

<span data-ttu-id="6716c-136">Эта функция создает оболочку для вызова метода [ивбемклассобжект::P утмесод](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="6716c-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="6716c-137">Этот вызов метода поддерживается, только если `ptr` является определением класса CIM.</span><span class="sxs-lookup"><span data-stu-id="6716c-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="6716c-138">Управление методами недоступно из [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) указателей, указывающих на экземпляры CIM.</span><span class="sxs-lookup"><span data-stu-id="6716c-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="6716c-139">Пользователи не могут создавать методы с именами, которые начинаются или заканчиваются символом подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="6716c-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="6716c-140">Он зарезервирован для системных классов и свойств.</span><span class="sxs-lookup"><span data-stu-id="6716c-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="6716c-141">Для метода `in` параметры и `out` описаны как свойства в объектах [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="6716c-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="6716c-142">Параметр можно определить, добавив одно и то же свойство в оба объекта, на `pInSignature` которые указывают `pOutSignature` параметры и. `[in/out]`</span><span class="sxs-lookup"><span data-stu-id="6716c-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="6716c-143">В этом случае свойства имеют одинаковое значение квалификатора **идентификатора** .</span><span class="sxs-lookup"><span data-stu-id="6716c-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="6716c-144">Каждое свойство в объекте класса [__Parameters](/windows/desktop/WmiSdk/--parameters) , отличном `ReturnValue` от, должно иметь квалификатор **ID** , числовое значение, начинающееся с нуля, определяющее порядок, в котором отображаются параметры.</span><span class="sxs-lookup"><span data-stu-id="6716c-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="6716c-145">Ни один из двух параметров не может иметь одинаковое значение **идентификатора** , и значение **идентификатора** не может быть пропущено.</span><span class="sxs-lookup"><span data-stu-id="6716c-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="6716c-146">При возникновении `PutMethod` любого из этих условий функция `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="6716c-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="6716c-147">Пример</span><span class="sxs-lookup"><span data-stu-id="6716c-147">Example</span></span>

<span data-ttu-id="6716c-148">Пример см. в описании метода [ивбемклассобжект::P утмесод](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="6716c-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6716c-149">Требования</span><span class="sxs-lookup"><span data-stu-id="6716c-149">Requirements</span></span>  
 <span data-ttu-id="6716c-150">**Платформ** См. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6716c-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6716c-151">**Заголовок.** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="6716c-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6716c-152">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6716c-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6716c-153">См. также</span><span class="sxs-lookup"><span data-stu-id="6716c-153">See also</span></span>

- [<span data-ttu-id="6716c-154">WMI и счетчики производительности (Справочник по неуправляемым интерфейсам API)</span><span class="sxs-lookup"><span data-stu-id="6716c-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
