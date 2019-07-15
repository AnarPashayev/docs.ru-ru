---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858982"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="e4d15-101">Улучшенные специальные возможности для некоторых средств пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="e4d15-101">Improved accessibility for some .NET SDK tools</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4d15-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="e4d15-102">Details</span></span>|<span data-ttu-id="e4d15-103">В пакете SDK .NET Framework 4.7.1 в средствах SvcConfigEditor.exe и SvcTraceViewer.exe были устранены различные проблемы со специальными возможностями.</span><span class="sxs-lookup"><span data-stu-id="e4d15-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="e4d15-104">В основном это были незначительные проблемы, например не определялось имя или некорректно реализовывались шаблоны автоматизации пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e4d15-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="e4d15-105">Многие пользователи могли не замечать неверные значения, но пользователям, использующим вспомогательные технологии, такие как средства чтения с экрана, будет проще использовать эти средства пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="e4d15-105">While many users wouldn’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="e4d15-106">Безусловно, эти исправления влияют на предыдущее поведение, например порядок фокуса клавиатуры. Чтобы получить все исправления специальных возможностей в этих средствах, выполните следующее в файле app.config:</span><span class="sxs-lookup"><span data-stu-id="e4d15-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e4d15-107">Область</span><span class="sxs-lookup"><span data-stu-id="e4d15-107">Scope</span></span>|<span data-ttu-id="e4d15-108">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="e4d15-108">Edge</span></span>|
|<span data-ttu-id="e4d15-109">Версия</span><span class="sxs-lookup"><span data-stu-id="e4d15-109">Version</span></span>|<span data-ttu-id="e4d15-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e4d15-110">4.7.1</span></span>|
|<span data-ttu-id="e4d15-111">Тип</span><span class="sxs-lookup"><span data-stu-id="e4d15-111">Type</span></span>|<span data-ttu-id="e4d15-112">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="e4d15-112">Retargeting</span></span>|

