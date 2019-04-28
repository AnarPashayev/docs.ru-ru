---
title: Функция BeginMethodEnumeration (Справочник по неуправляемым API)
description: Функция BeginMethodEnumeration начинается перечисление методы объекта
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6de2a5ff4d2743c7aca2e46b3af848138c15fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917362"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="303b4-103">Функция BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="303b4-103">BeginEnumeration function</span></span>
<span data-ttu-id="303b4-104">Начинает перечисление методы, доступные для объекта.</span><span class="sxs-lookup"><span data-stu-id="303b4-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="303b4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="303b4-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="303b4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="303b4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="303b4-107">[in] Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="303b4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="303b4-108">[in] Указатель на [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="303b4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="303b4-109">[in] Ноль (0) для всех методов, или флаг, указывающий область видимости перечисления.</span><span class="sxs-lookup"><span data-stu-id="303b4-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="303b4-110">Далее перечислены флаги определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="303b4-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="303b4-111">Константа</span><span class="sxs-lookup"><span data-stu-id="303b4-111">Constant</span></span>  |<span data-ttu-id="303b4-112">Значение</span><span class="sxs-lookup"><span data-stu-id="303b4-112">Value</span></span>  |<span data-ttu-id="303b4-113">Описание</span><span class="sxs-lookup"><span data-stu-id="303b4-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="303b4-114">0x10</span><span class="sxs-lookup"><span data-stu-id="303b4-114">0x10</span></span> | <span data-ttu-id="303b4-115">Ограничения перечисления к методам, которые определены в самом классе.</span><span class="sxs-lookup"><span data-stu-id="303b4-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="303b4-116">0x20</span><span class="sxs-lookup"><span data-stu-id="303b4-116">0x20</span></span> | <span data-ttu-id="303b4-117">Ограничения перечисления для свойства, наследуемые от базовых классов.</span><span class="sxs-lookup"><span data-stu-id="303b4-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="303b4-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="303b4-118">Return value</span></span>

<span data-ttu-id="303b4-119">Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файл заголовка, или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="303b4-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="303b4-120">Константа</span><span class="sxs-lookup"><span data-stu-id="303b4-120">Constant</span></span>  |<span data-ttu-id="303b4-121">Значение</span><span class="sxs-lookup"><span data-stu-id="303b4-121">Value</span></span>  |<span data-ttu-id="303b4-122">Описание</span><span class="sxs-lookup"><span data-stu-id="303b4-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="303b4-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="303b4-123">0x80041008</span></span> | <span data-ttu-id="303b4-124">`lEnnumFlags` не равно нулю и не является одним из указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="303b4-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="303b4-125">0</span><span class="sxs-lookup"><span data-stu-id="303b4-125">0</span></span> | <span data-ttu-id="303b4-126">Вызов функции был успешным.</span><span class="sxs-lookup"><span data-stu-id="303b4-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="303b4-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="303b4-127">Remarks</span></span>

<span data-ttu-id="303b4-128">Эта функция создает оболочку для вызова [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) метод.</span><span class="sxs-lookup"><span data-stu-id="303b4-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="303b4-129">Вызов этого метода поддерживается только в том случае, если текущий объект является определение класса.</span><span class="sxs-lookup"><span data-stu-id="303b4-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="303b4-130">Метод манипуляции не доступен из [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) указатели, которые указывают на экземпляры.</span><span class="sxs-lookup"><span data-stu-id="303b4-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="303b4-131">Порядок, в котором перечисляются методы обязательно является инвариантным для заданного экземпляра [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="303b4-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="303b4-132">Требования</span><span class="sxs-lookup"><span data-stu-id="303b4-132">Requirements</span></span>  
 <span data-ttu-id="303b4-133">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="303b4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="303b4-134">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="303b4-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="303b4-135">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="303b4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303b4-136">См. также</span><span class="sxs-lookup"><span data-stu-id="303b4-136">See also</span></span>

- [<span data-ttu-id="303b4-137">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="303b4-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
