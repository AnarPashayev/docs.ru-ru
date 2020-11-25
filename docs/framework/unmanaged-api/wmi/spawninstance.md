---
title: Функция Спавнинстанце (Справочник по неуправляемым API)
description: Функция Спавнинстанце создает новый экземпляр класса.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 176bc83dd02381af8c2bc3995a37e7fee7c1bebf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732233"
---
# <a name="spawninstance-function"></a><span data-ttu-id="b2613-103">Функция SpawnInstance</span><span class="sxs-lookup"><span data-stu-id="b2613-103">SpawnInstance function</span></span>

<span data-ttu-id="b2613-104">Создает экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="b2613-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b2613-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2613-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="b2613-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b2613-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b2613-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="b2613-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b2613-108">окне Указатель на экземпляр [ивбемклассобжект](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="b2613-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="b2613-109">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="b2613-109">[in] Reserved.</span></span> <span data-ttu-id="b2613-110">Этот параметр должен иметь значение 0.</span><span class="sxs-lookup"><span data-stu-id="b2613-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="b2613-111">заполняет Получает указатель на новый экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="b2613-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="b2613-112">При возникновении ошибки новый объект не возвращается и остается `ppNewInstance` неизменным.</span><span class="sxs-lookup"><span data-stu-id="b2613-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2613-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b2613-113">Return value</span></span>

<span data-ttu-id="b2613-114">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="b2613-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b2613-115">Константа</span><span class="sxs-lookup"><span data-stu-id="b2613-115">Constant</span></span>  |<span data-ttu-id="b2613-116">Значение</span><span class="sxs-lookup"><span data-stu-id="b2613-116">Value</span></span>  |<span data-ttu-id="b2613-117">Описание</span><span class="sxs-lookup"><span data-stu-id="b2613-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="b2613-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="b2613-118">0x80041020</span></span> | <span data-ttu-id="b2613-119">`ptr` не является допустимым определением класса и не может порождать новые экземпляры.</span><span class="sxs-lookup"><span data-stu-id="b2613-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="b2613-120">Либо он неполон, либо не зарегистрирован в службе управления Windows путем вызова [путклассвми](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="b2613-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b2613-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b2613-121">0x80041006</span></span> | <span data-ttu-id="b2613-122">Недостаточно памяти для выполнения операции.</span><span class="sxs-lookup"><span data-stu-id="b2613-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b2613-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b2613-123">0x80041008</span></span> | <span data-ttu-id="b2613-124">`ppNewClass` имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b2613-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b2613-125">0</span><span class="sxs-lookup"><span data-stu-id="b2613-125">0</span></span> | <span data-ttu-id="b2613-126">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="b2613-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b2613-127">Комментарии</span><span class="sxs-lookup"><span data-stu-id="b2613-127">Remarks</span></span>

<span data-ttu-id="b2613-128">Эта функция заключает в оболочку вызов метода [ивбемклассобжект:: спавнинстанце](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) .</span><span class="sxs-lookup"><span data-stu-id="b2613-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="b2613-129">`ptr` должно быть определением класса, полученным из системы управления Windows.</span><span class="sxs-lookup"><span data-stu-id="b2613-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="b2613-130">(Обратите внимание, что порождение экземпляра из экземпляра поддерживается, но возвращаемый экземпляр пуст.) Затем это определение класса используется для создания новых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="b2613-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="b2613-131">Вызов функции [путинстанцевми](putinstancewmi.md) требуется, если вы планируете записать экземпляр в Windows Management.</span><span class="sxs-lookup"><span data-stu-id="b2613-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="b2613-132">Новый объект, возвращенный в `ppNewClass` , автоматически станет подклассом текущего объекта.</span><span class="sxs-lookup"><span data-stu-id="b2613-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="b2613-133">Это поведение не может быть переопределено.</span><span class="sxs-lookup"><span data-stu-id="b2613-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="b2613-134">Нет других методов, с помощью которых можно создать подклассы (производные классы).</span><span class="sxs-lookup"><span data-stu-id="b2613-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2613-135">Требования</span><span class="sxs-lookup"><span data-stu-id="b2613-135">Requirements</span></span>  

 <span data-ttu-id="b2613-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2613-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2613-137">**Заголовок:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="b2613-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b2613-138">**.NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2613-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2613-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b2613-139">See also</span></span>

- [<span data-ttu-id="b2613-140">WMI и счетчики производительности (справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="b2613-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
