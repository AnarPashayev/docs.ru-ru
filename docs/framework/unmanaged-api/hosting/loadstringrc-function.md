---
title: Функция LoadStringRC
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 8bd0292ddf22453f8892ed8bddd10c2144877097
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008523"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="72cac-102">Функция LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="72cac-102">LoadStringRC Function</span></span>
<span data-ttu-id="72cac-103">Преобразует значение HRESULT в сообщение об ошибке с помощью языка и региональных параметров по умолчанию текущего потока.</span><span class="sxs-lookup"><span data-stu-id="72cac-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="72cac-104">Эта функция является устаревшей в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="72cac-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72cac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72cac-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72cac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="72cac-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="72cac-107">[in] Значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="72cac-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="72cac-108">заполняет Буфер, содержащий сообщение об ошибке после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="72cac-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="72cac-109">окне Размер буфера сообщений об ошибках.</span><span class="sxs-lookup"><span data-stu-id="72cac-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="72cac-110">окне Игнорируют.</span><span class="sxs-lookup"><span data-stu-id="72cac-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72cac-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="72cac-111">Return Value</span></span>  
 <span data-ttu-id="72cac-112">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="72cac-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="72cac-113">Код возврата</span><span class="sxs-lookup"><span data-stu-id="72cac-113">Return code</span></span>|<span data-ttu-id="72cac-114">Описание</span><span class="sxs-lookup"><span data-stu-id="72cac-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="72cac-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="72cac-115">S_OK</span></span>|<span data-ttu-id="72cac-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="72cac-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="72cac-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="72cac-117">E_INVALIDARG</span></span>|<span data-ttu-id="72cac-118">`szBuffer`имеет значение null или `iMax` равно нулю (0).</span><span class="sxs-lookup"><span data-stu-id="72cac-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72cac-119">Примечания</span><span class="sxs-lookup"><span data-stu-id="72cac-119">Remarks</span></span>  
 <span data-ttu-id="72cac-120">Если метод не завершается успешно, `szBuffer` содержит пустую строку.</span><span class="sxs-lookup"><span data-stu-id="72cac-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72cac-121">Требования</span><span class="sxs-lookup"><span data-stu-id="72cac-121">Requirements</span></span>  
 <span data-ttu-id="72cac-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72cac-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72cac-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72cac-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72cac-124">**Библиотека:** MSCorEE. dll и mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="72cac-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="72cac-125">Используйте библиотеку MSCorEE. dll вместо Mscorwks. dll, чтобы обеспечить правильную версию .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72cac-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="72cac-126">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72cac-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cac-127">См. также статью</span><span class="sxs-lookup"><span data-stu-id="72cac-127">See also</span></span>

- [<span data-ttu-id="72cac-128">Функция LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="72cac-128">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="72cac-129">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="72cac-129">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
