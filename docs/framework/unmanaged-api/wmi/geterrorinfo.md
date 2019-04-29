---
title: Функция GetErrorInfo (Справочник по неуправляемым API)
description: Функция GetErrorInfo получает сведения об ошибке из предыдущего вызова функции.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2df4b87016394d1998ef90abe2e3eeb911886ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608974"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="ac442-103">GetErrorInfo-функция</span><span class="sxs-lookup"><span data-stu-id="ac442-103">GetErrorInfo function</span></span>
<span data-ttu-id="ac442-104">Получает сведения об ошибках из предыдущего вызова функции.</span><span class="sxs-lookup"><span data-stu-id="ac442-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ac442-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ac442-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="ac442-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ac442-106">Return value</span></span>

<span data-ttu-id="ac442-107">Указатель на [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) объекта, если вызов функции завершается успешно, или `null` при сбое.</span><span class="sxs-lookup"><span data-stu-id="ac442-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ac442-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="ac442-108">Remarks</span></span>

<span data-ttu-id="ac442-109">Эта функция создает оболочку для вызова [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) метод.</span><span class="sxs-lookup"><span data-stu-id="ac442-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac442-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ac442-110">Requirements</span></span>  
 <span data-ttu-id="ac442-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac442-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac442-112">**Заголовок.** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="ac442-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="ac442-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac442-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac442-114">См. также</span><span class="sxs-lookup"><span data-stu-id="ac442-114">See also</span></span>

- [<span data-ttu-id="ac442-115">WMI и счетчики производительности (Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="ac442-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
