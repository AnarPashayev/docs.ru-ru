---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802648"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="1aafb-101">.NET COM успешно маршалирует параметры ByRef SafeArray в события</span><span class="sxs-lookup"><span data-stu-id="1aafb-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1aafb-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="1aafb-102">Details</span></span>|<span data-ttu-id="1aafb-103">В .NET Framework 4.7.2 и более ранних версиях параметр ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) события COM не позволял выполнить маршалинг обратно в машинный код.</span><span class="sxs-lookup"><span data-stu-id="1aafb-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="1aafb-104">Благодаря этому изменению [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) теперь успешно маршалируется.</span><span class="sxs-lookup"><span data-stu-id="1aafb-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="1aafb-105">[x] Режим совместимости</span><span class="sxs-lookup"><span data-stu-id="1aafb-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="1aafb-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="1aafb-106">Suggestion</span></span>|<span data-ttu-id="1aafb-107">Если правильный маршалинг параметров ByRef SafeArray в событиях COM нарушает выполнение, этот код можно отключить, добавив следующий параметр конфигурации в файл конфигурации приложения:</span><span class="sxs-lookup"><span data-stu-id="1aafb-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="1aafb-108">Область</span><span class="sxs-lookup"><span data-stu-id="1aafb-108">Scope</span></span>|<span data-ttu-id="1aafb-109">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="1aafb-109">Minor</span></span>|
|<span data-ttu-id="1aafb-110">Версия</span><span class="sxs-lookup"><span data-stu-id="1aafb-110">Version</span></span>|<span data-ttu-id="1aafb-111">4.8</span><span class="sxs-lookup"><span data-stu-id="1aafb-111">4.8</span></span>|
|<span data-ttu-id="1aafb-112">Тип</span><span class="sxs-lookup"><span data-stu-id="1aafb-112">Type</span></span>|<span data-ttu-id="1aafb-113">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="1aafb-113">Runtime</span></span>|

