---
title: Мониторинг служб контейнерных приложений
description: Сведения об основных аспектах, связанных с мониторингом контейнерных архитектур
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374446"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="55902-103">Мониторинг служб контейнерных приложений</span><span class="sxs-lookup"><span data-stu-id="55902-103">Monitor containerized application services</span></span>

<span data-ttu-id="55902-104">Для эффективного мониторинга и анализа поведения приложения в целом важно разбить его на несколько контейнеров и микрослужб.</span><span class="sxs-lookup"><span data-stu-id="55902-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="55902-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="55902-105">Azure Monitor</span></span>

<span data-ttu-id="55902-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) — это расширяемая служба аналитики, которая отслеживает работающие приложения.</span><span class="sxs-lookup"><span data-stu-id="55902-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="55902-107">С ее помощью можно обнаруживать и диагностировать проблемы производительности, а также понять, что пользователи в действительности делают с вашим приложением.</span><span class="sxs-lookup"><span data-stu-id="55902-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="55902-108">Эта служба ориентирована на разработчиков и предназначена для постоянного улучшения производительности и удобства ваших приложений и служб.</span><span class="sxs-lookup"><span data-stu-id="55902-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="55902-109">Azure Monitor работает с обычными или веб-службами и автономными приложениями на самых разных платформах, включая .NET, Java, Node.js и многие другие, которые могут размещаться как локально, так и в облаке.</span><span class="sxs-lookup"><span data-stu-id="55902-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="55902-110">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="55902-110">Additional resources</span></span>

- <span data-ttu-id="55902-111">**Обзор Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="55902-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="55902-112">**Что такое Azure Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="55902-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="55902-113">**Что такое метрики Azure Monitor?**</span><span class="sxs-lookup"><span data-stu-id="55902-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="55902-114">**Решение для мониторинга контейнеров в Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="55902-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="55902-115">Службы безопасности и резервного копирования</span><span class="sxs-lookup"><span data-stu-id="55902-115">Security and backup services</span></span>

<span data-ttu-id="55902-116">Чтобы обеспечить эффективную поддержку приложений и инфраструктуры в соответствии с постоянно изменяющимися бизнес-требованиями, необходимо выполнять множество самых разных рутинных операций и обрабатывать большие объемы сведений. В среде микрослужб ситуация становится еще сложнее, поскольку для выполнения любых действий вам требуется и высокоуровневое, и детализированное представление.</span><span class="sxs-lookup"><span data-stu-id="55902-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="55902-117">В Azure представлены средства управления, позволяющие получить унифицированное представление по четырем ключевым аспектам ваших облачных и локальных ресурсов:</span><span class="sxs-lookup"><span data-stu-id="55902-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="55902-118">**Безопасность**.</span><span class="sxs-lookup"><span data-stu-id="55902-118">**Security**.</span></span> <span data-ttu-id="55902-119">Используйте [Центр безопасности Azure](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="55902-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="55902-120">Полная прозрачность и эффективное управление безопасностью виртуальных машин, приложений и рабочих нагрузок.</span><span class="sxs-lookup"><span data-stu-id="55902-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="55902-121">Централизованное управление политиками безопасности и интеграция с существующими процессами и средствами.</span><span class="sxs-lookup"><span data-stu-id="55902-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="55902-122">Обнаружение реальных угроз благодаря расширенной аналитике.</span><span class="sxs-lookup"><span data-stu-id="55902-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="55902-123">**Резервное копирование**.</span><span class="sxs-lookup"><span data-stu-id="55902-123">**Backup**.</span></span> <span data-ttu-id="55902-124">Используйте [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="55902-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="55902-125">Исключение дорогостоящих перебоев в работе, обеспечение соответствия требованиям и защита данных от программ-шантажистов и человеческих ошибок.</span><span class="sxs-lookup"><span data-stu-id="55902-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="55902-126">Шифрование данных при передаче и во время хранения.</span><span class="sxs-lookup"><span data-stu-id="55902-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="55902-127">Защита от несанкционированного доступа на основе многофакторной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="55902-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="55902-128">**Локальные ресурсы**.</span><span class="sxs-lookup"><span data-stu-id="55902-128">**On-premises resources**.</span></span> <span data-ttu-id="55902-129">Используйте [гибридные облачные решения](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span><span class="sxs-lookup"><span data-stu-id="55902-129">With [hybrid cloud solutions](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="55902-130">[Назад](manage-production-docker-environments.md)
>[Вперед](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="55902-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
