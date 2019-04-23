---
title: Устранение рисков. Проверки двоеточий в путях
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342c3ce59ad80c9a60f2a2b69b30f77ff0549415
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176765"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="39e87-102">Устранение рисков. Проверки двоеточий в путях</span><span class="sxs-lookup"><span data-stu-id="39e87-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="39e87-103">Начиная с приложений, ориентированных на [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], выполнен ряд изменений для поддержки ранее не поддерживаемых путей (с точки зрения и длины, и формата).</span><span class="sxs-lookup"><span data-stu-id="39e87-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="39e87-104">В частности, усовершенствованы проверки правильности синтаксиса разделителя диска (двоеточия).</span><span class="sxs-lookup"><span data-stu-id="39e87-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="39e87-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="39e87-105">Impact</span></span>  
 <span data-ttu-id="39e87-106">Эти изменения блокируют некоторые пути URI, которые ранее поддерживались методами <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> и <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39e87-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="39e87-107">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="39e87-107">Mitigation</span></span>  
 <span data-ttu-id="39e87-108">Чтобы обойти проблему с ранее допустимым путем, который больше не поддерживается методами <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> и <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="39e87-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="39e87-109">Вручную удалить схему из URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="39e87-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="39e87-110">Например, удалить `file://` из URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="39e87-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="39e87-111">передать код URI в конструктор <xref:System.Uri> и получить значение свойства <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="39e87-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="39e87-112">отказаться от новой нормализации путей, установив для параметра `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="39e87-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39e87-113">См. также</span><span class="sxs-lookup"><span data-stu-id="39e87-113">See also</span></span>

- [<span data-ttu-id="39e87-114">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="39e87-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
