---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235965"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="96c8e-101">Элементы управления Managed Browser в .NET Framework 1.1 и 2.0 заблокированы</span><span class="sxs-lookup"><span data-stu-id="96c8e-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

|   |   |
|---|---|
|<span data-ttu-id="96c8e-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="96c8e-102">Details</span></span>|<span data-ttu-id="96c8e-103">Размещение этих элементов управления в Internet Explorer блокируется.</span><span class="sxs-lookup"><span data-stu-id="96c8e-103">Hosting these controls is blocked in Internet Explorer.</span></span>|
|<span data-ttu-id="96c8e-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="96c8e-104">Suggestion</span></span>|<span data-ttu-id="96c8e-105">Internet Explorer не сможет запустить приложение, в котором используются управляемые элементы управления, размещенные в браузере.</span><span class="sxs-lookup"><span data-stu-id="96c8e-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="96c8e-106">Прежнее поведение можно восстановить путем установки параметру EnableIEHosting подраздела реестра <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> значения <code>1</code> для систем x86 и для 32-разрядных процессов в системах x64, а также путем установки параметру <code>EnableIEHosting</code> подраздела реестра <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> значения <code>1</code> для 64-разрядных процессов в системах x64.</span><span class="sxs-lookup"><span data-stu-id="96c8e-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>|
|<span data-ttu-id="96c8e-107">Область</span><span class="sxs-lookup"><span data-stu-id="96c8e-107">Scope</span></span>|<span data-ttu-id="96c8e-108">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="96c8e-108">Minor</span></span>|
|<span data-ttu-id="96c8e-109">Версия</span><span class="sxs-lookup"><span data-stu-id="96c8e-109">Version</span></span>|<span data-ttu-id="96c8e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="96c8e-110">4.5</span></span>|
|<span data-ttu-id="96c8e-111">Тип</span><span class="sxs-lookup"><span data-stu-id="96c8e-111">Type</span></span>|<span data-ttu-id="96c8e-112">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="96c8e-112">Runtime</span></span>|
