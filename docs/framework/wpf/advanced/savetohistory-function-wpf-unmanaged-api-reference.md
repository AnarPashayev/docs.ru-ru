---
title: Функция SaveToHistory (WPF Справочник по неуправляемым API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 3f6413558ff1f259e497c6a1c31eb2664f70cc48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213720"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="56033-102">Функция SaveToHistory (WPF Справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="56033-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="56033-103">Этот API поддерживает инфраструктуру Windows Presentation Foundation (WPF) и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="56033-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="56033-104">Используется инфраструктурой Windows Presentation Foundation (WPF) для управления windows.</span><span class="sxs-lookup"><span data-stu-id="56033-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56033-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="56033-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="56033-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="56033-106">Parameters</span></span>  
 <span data-ttu-id="56033-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="56033-107">pHistoryStream</span></span>  
 <span data-ttu-id="56033-108">Указатель на поток журнала.</span><span class="sxs-lookup"><span data-stu-id="56033-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56033-109">Требования</span><span class="sxs-lookup"><span data-stu-id="56033-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56033-110">Требования</span><span class="sxs-lookup"><span data-stu-id="56033-110">Requirements</span></span>  
 <span data-ttu-id="56033-111">**Платформы:** См. в разделе [системные требования .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56033-111">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="56033-112">БИБЛИОТЕКА DLL:</span><span class="sxs-lookup"><span data-stu-id="56033-112">DLL:</span></span>**  
  
 <span data-ttu-id="56033-113">В .NET Framework 3.0 и 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="56033-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="56033-114">В .NET Framework 4 и более поздних версий: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="56033-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="56033-115">Версии платформы .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56033-115">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56033-116">См. также</span><span class="sxs-lookup"><span data-stu-id="56033-116">See also</span></span>

- [<span data-ttu-id="56033-117">Справочник по неуправляемым API WPF</span><span class="sxs-lookup"><span data-stu-id="56033-117">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
