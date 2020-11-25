---
title: Метод IBindingDisplay::InitializeForProcess
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: f9e65b49c9a3b506cba3493d81a40f2759dca781
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725155"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="77e36-102">Метод IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="77e36-102">IBindingDisplay::InitializeForProcess Method</span></span>

<span data-ttu-id="77e36-103">Инициализирует объект [ибиндингдисплай](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="77e36-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e36-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77e36-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e36-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="77e36-105">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="77e36-106">окне Идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="77e36-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77e36-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="77e36-107">Remarks</span></span>  

 <span data-ttu-id="77e36-108">Отладчик вызывает `InitializeForProcess` метод во время создания, чтобы инициализировать отображение привязки.</span><span class="sxs-lookup"><span data-stu-id="77e36-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="77e36-109">`InitializeForProcess` должен вызываться во время создания до вызова любого другого метода `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="77e36-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e36-110">Требования</span><span class="sxs-lookup"><span data-stu-id="77e36-110">Requirements</span></span>  

 <span data-ttu-id="77e36-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e36-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e36-112">**Заголовок:** Биндингдисплай. h</span><span class="sxs-lookup"><span data-stu-id="77e36-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="77e36-113">**Библиотека:** Биндингдисплай. idl</span><span class="sxs-lookup"><span data-stu-id="77e36-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="77e36-114">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e36-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="77e36-115">See also</span></span>

- [<span data-ttu-id="77e36-116">Интерфейс IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="77e36-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
