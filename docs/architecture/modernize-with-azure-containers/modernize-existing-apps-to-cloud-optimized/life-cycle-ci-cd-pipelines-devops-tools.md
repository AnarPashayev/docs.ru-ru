---
title: Модернизация жизненного цикла приложений с помощью конвейеров непрерывной интеграции и непрерывного развертывания и средств DevOps в облаке
description: Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows | Модернизация жизненного цикла приложений с помощью конвейеров непрерывной интеграции и непрерывного развертывания и средств DevOps в облаке
ms.date: 04/30/2018
ms.openlocfilehash: afb7bae7780a766329ca604d192b2d7353e32bf5
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739165"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="690c6-103">Модернизация жизненного цикла приложений с помощью конвейеров непрерывной интеграции и непрерывного развертывания и средств DevOps в облаке</span><span class="sxs-lookup"><span data-stu-id="690c6-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="690c6-104">Современные организации должны быстро внедрять инновации, чтобы быть конкурентоспособными на рынке.</span><span class="sxs-lookup"><span data-stu-id="690c6-104">Today's businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="690c6-105">Для предоставления высококачественных современных приложений требуются средства и процессы DevOps, которые важны для реализации этого постоянного цикла инноваций.</span><span class="sxs-lookup"><span data-stu-id="690c6-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="690c6-106">С помощью правильных средств DevOps разработчики могут упростить непрерывное развертывание и быстро предоставлять инновационные приложения пользователям.</span><span class="sxs-lookup"><span data-stu-id="690c6-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="690c6-107">Несмотря на наличие хорошо устоявшихся методов непрерывной интеграции и развертывания внедрение контейнеров требует учета новых аспектов, особенно при работе с многоконтейнерными приложениями.</span><span class="sxs-lookup"><span data-stu-id="690c6-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="690c6-108">Azure DevOps Services поддерживает непрерывную интеграцию и развертывание многоконтейнерных приложений в различных средах с помощью официальных задач развертывания:</span><span class="sxs-lookup"><span data-stu-id="690c6-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- <span data-ttu-id="690c6-109">[развертывание в решении "Веб-приложения Azure для контейнеров"](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core);</span><span class="sxs-lookup"><span data-stu-id="690c6-109">[Deploy to an Azure Web App for Containers](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)</span></span>

- <span data-ttu-id="690c6-110">[развертывание в Службе Azure Kubernetes](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="690c6-110">[Deploy to Azure Kubernetes Service](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)</span></span>

<span data-ttu-id="690c6-111">Но вы также можете выполнить развертывание в [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) или DC/OS с помощью задач Azure DevOps Services на основе скриптов.</span><span class="sxs-lookup"><span data-stu-id="690c6-111">But you can also deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="690c6-112">Чтобы улучшить гибкость развертывания, эти средства предоставляют отличные возможности развертывания рабочих нагрузок контейнеров в средах разработки, тестирования и, наконец, в рабочей, а также различные решения для разработки, непрерывной интеграции и доставки.</span><span class="sxs-lookup"><span data-stu-id="690c6-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="690c6-113">На рис. 4-12 показан конвейер непрерывного развертывания, который выполняет развертывание в кластере Kubernetes в Службе контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="690c6-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Снимок экрана, где показан конвейер Azure DevOps Services, осуществляющий развертывание в кластере Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="690c6-115">**Рис. 4-12**.</span><span class="sxs-lookup"><span data-stu-id="690c6-115">**Figure 4-12.**</span></span> <span data-ttu-id="690c6-116">Конвейер непрерывного развертывания Azure DevOps Services, осуществляющий развертывание в кластере Kubernetes</span><span class="sxs-lookup"><span data-stu-id="690c6-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="690c6-117">[Назад](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Вперед](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="690c6-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
