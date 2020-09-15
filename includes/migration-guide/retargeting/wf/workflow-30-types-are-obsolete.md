---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617307"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="87d30-101">Типы WorkFlow 3.0 устарели</span><span class="sxs-lookup"><span data-stu-id="87d30-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="87d30-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="87d30-102">Details</span></span>

<span data-ttu-id="87d30-103">API-интерфейсы Windows Workflow Foundation (WWF) 3.0 (из пространства имен System.Workflow) теперь являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="87d30-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="87d30-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="87d30-104">Suggestion</span></span>

<span data-ttu-id="87d30-105">Вместо них следует использовать новые интерфейсы API WWF 4.0 (в System.Activities).</span><span class="sxs-lookup"><span data-stu-id="87d30-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="87d30-106">Пример использования новых интерфейсов API можно найти [здесь](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), а дальнейшие рекомендации доступны [здесь](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span><span class="sxs-lookup"><span data-stu-id="87d30-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="87d30-107">Кроме того, поскольку API-интерфейсы WWF 3.0 по-прежнему поддерживаются, их можно использовать, а чтобы избежать вывода предупреждения во время построения, его можно подавить или воспользоваться более старой версией компилятора.</span><span class="sxs-lookup"><span data-stu-id="87d30-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="87d30-108">name</span><span class="sxs-lookup"><span data-stu-id="87d30-108">Name</span></span>    | <span data-ttu-id="87d30-109">Значение</span><span class="sxs-lookup"><span data-stu-id="87d30-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="87d30-110">Область</span><span class="sxs-lookup"><span data-stu-id="87d30-110">Scope</span></span>   | <span data-ttu-id="87d30-111">Значительно</span><span class="sxs-lookup"><span data-stu-id="87d30-111">Major</span></span>       |
| <span data-ttu-id="87d30-112">Version</span><span class="sxs-lookup"><span data-stu-id="87d30-112">Version</span></span> | <span data-ttu-id="87d30-113">4.5</span><span class="sxs-lookup"><span data-stu-id="87d30-113">4.5</span></span>         |
| <span data-ttu-id="87d30-114">Type</span><span class="sxs-lookup"><span data-stu-id="87d30-114">Type</span></span>    | <span data-ttu-id="87d30-115">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="87d30-115">Retargeting</span></span> |
