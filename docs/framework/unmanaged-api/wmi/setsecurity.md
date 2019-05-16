---
title: Функция SetSecurity (Справочник по неуправляемым API)
description: Функция SetSecurity получает маркер олицетворения текущего потока.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cecd8538b8f2b5d04cb9f1822751661ce9f8728
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636221"
---
# <a name="setsecurity-function"></a><span data-ttu-id="b8c80-103">Функция SetSecurity</span><span class="sxs-lookup"><span data-stu-id="b8c80-103">SetSecurity function</span></span>

<span data-ttu-id="b8c80-104">Получает маркер олицетворения, связанный с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="b8c80-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b8c80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8c80-105">Syntax</span></span>

```
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="b8c80-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b8c80-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="b8c80-107">[out] При возврате функции, содержит указатель на `boolean` , указывающее, следует ли сбросить маркер путем вызова [ResetSecurity](resetsecurity.md) функции.</span><span class="sxs-lookup"><span data-stu-id="b8c80-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="b8c80-108">[out] При возврате функции, содержит указатель на дескриптор токена олицетворения, связанный с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="b8c80-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="b8c80-109">Его значение может быть `null` имеется ли токен, не связанный с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="b8c80-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b8c80-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b8c80-110">Return value</span></span>

<span data-ttu-id="b8c80-111">Если функция выполняется успешно, возвращаемое значение равно `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="b8c80-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="b8c80-112">Если функция завершается с ошибкой, возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="b8c80-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="b8c80-113">Чтобы получить расширенные сведения об ошибке, вызовите [GetErrorInfo](geterrorinfo.md) функции.</span><span class="sxs-lookup"><span data-stu-id="b8c80-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8c80-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b8c80-114">Requirements</span></span>

 <span data-ttu-id="b8c80-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c80-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b8c80-116">**Заголовок.** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8c80-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="b8c80-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8c80-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b8c80-118">See also</span></span>

- [<span data-ttu-id="b8c80-119">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="b8c80-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
