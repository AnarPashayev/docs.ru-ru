---
title: Функция Вритепропертивалуе (Справочник по неуправляемым API)
description: Функция Вритепропертивалуе записывает байты в свойство.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729412"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="1f4d6-103">Функция WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="1f4d6-103">WritePropertyValue function</span></span>

<span data-ttu-id="1f4d6-104">Записывает указанное число байт в свойство, заданное маркером свойства.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1f4d6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f4d6-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="1f4d6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1f4d6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1f4d6-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1f4d6-108">окне Указатель на экземпляр [ивбемобжектакцесс](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="1f4d6-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="1f4d6-109">окне Целое число, содержащее маркер, определяющий это свойство.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="1f4d6-110">Этот маркер можно получить, вызвав функцию [жетпропертихандле](getpropertyhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="1f4d6-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="1f4d6-111">окне Число байтов, записываемых в свойство.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="1f4d6-112">Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="1f4d6-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="1f4d6-113">`pHandle` заполняет Указатель на массив байтов, который содержит данные.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="1f4d6-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1f4d6-114">Return value</span></span>

<span data-ttu-id="1f4d6-115">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="1f4d6-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1f4d6-116">Константа</span><span class="sxs-lookup"><span data-stu-id="1f4d6-116">Constant</span></span>  |<span data-ttu-id="1f4d6-117">Значение</span><span class="sxs-lookup"><span data-stu-id="1f4d6-117">Value</span></span>  |<span data-ttu-id="1f4d6-118">Описание</span><span class="sxs-lookup"><span data-stu-id="1f4d6-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1f4d6-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1f4d6-119">0x80041008</span></span> | <span data-ttu-id="1f4d6-120">Недействительный параметр.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="1f4d6-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="1f4d6-121">0x80041005</span></span> | <span data-ttu-id="1f4d6-122">Обнаружено несоответствие типов.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1f4d6-123">0</span><span class="sxs-lookup"><span data-stu-id="1f4d6-123">0</span></span> | <span data-ttu-id="1f4d6-124">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1f4d6-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="1f4d6-125">Remarks</span></span>

<span data-ttu-id="1f4d6-126">Эта функция заключает в оболочку вызов метода [ивбемклассобжект:: вритепропертивалуе](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .</span><span class="sxs-lookup"><span data-stu-id="1f4d6-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="1f4d6-127">Эта функция используется для задания строки и всех остальных не являющихся `DWORD` `QWORD` данными.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="1f4d6-128">Для нестроковых значений свойств `lNumBytes` должен быть указан правильный размер данных указанного типа свойства.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="1f4d6-129">Для значений строковых свойств значение `lNumBytes` должно быть длиной указанной строки в байтах, а сама строка должна иметь допустимую длину в байтах и заканчиваться символом завершения null.</span><span class="sxs-lookup"><span data-stu-id="1f4d6-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f4d6-130">Требования</span><span class="sxs-lookup"><span data-stu-id="1f4d6-130">Requirements</span></span>  

<span data-ttu-id="1f4d6-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f4d6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4d6-132">**Заголовок:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="1f4d6-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1f4d6-133">**.NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4d6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4d6-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1f4d6-134">See also</span></span>

- [<span data-ttu-id="1f4d6-135">WMI и счетчики производительности (справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="1f4d6-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
