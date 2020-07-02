---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620171"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="c5ecc-101">Свойству EnableViewStateMac больше невозможно задавать значение false</span><span class="sxs-lookup"><span data-stu-id="c5ecc-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="c5ecc-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="c5ecc-102">Details</span></span>

<span data-ttu-id="c5ecc-103">ASP.NET теперь не позволяет разработчикам указывать <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> или <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="c5ecc-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="c5ecc-104">Код проверки подлинности сообщения (MAC) состояния просмотра теперь принудительно применяется для всех запросов со встроенным состоянием просмотра.</span><span class="sxs-lookup"><span data-stu-id="c5ecc-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="c5ecc-105">Затрагиваются только те приложения, в которых для свойства EnableViewStateMac явно задано значение <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="c5ecc-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5ecc-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="c5ecc-106">Suggestion</span></span>

<span data-ttu-id="c5ecc-107">Следует считать, что свойство EnableViewStateMac имеет значение true, и возникающие ошибки MAC должны быть устранены (как описано в [этом](https://support.microsoft.com/kb/2915218) руководстве, содержащем несколько решений в зависимости от причины ошибки MAC).</span><span class="sxs-lookup"><span data-stu-id="c5ecc-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="c5ecc-108">name</span><span class="sxs-lookup"><span data-stu-id="c5ecc-108">Name</span></span>    | <span data-ttu-id="c5ecc-109">Значение</span><span class="sxs-lookup"><span data-stu-id="c5ecc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5ecc-110">Область</span><span class="sxs-lookup"><span data-stu-id="c5ecc-110">Scope</span></span>   |<span data-ttu-id="c5ecc-111">Значительно</span><span class="sxs-lookup"><span data-stu-id="c5ecc-111">Major</span></span>|
|<span data-ttu-id="c5ecc-112">Version</span><span class="sxs-lookup"><span data-stu-id="c5ecc-112">Version</span></span>|<span data-ttu-id="c5ecc-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c5ecc-113">4.5.2</span></span>|
|<span data-ttu-id="c5ecc-114">Type</span><span class="sxs-lookup"><span data-stu-id="c5ecc-114">Type</span></span>|<span data-ttu-id="c5ecc-115">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="c5ecc-115">Runtime</span></span>|
