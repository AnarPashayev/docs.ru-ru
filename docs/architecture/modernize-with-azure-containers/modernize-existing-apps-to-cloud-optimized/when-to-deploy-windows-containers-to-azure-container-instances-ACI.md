---
title: Когда следует развертывать контейнеры Windows в службе "экземпляры контейнеров Azure" (ACI)
description: Модернизировать существующих приложений .NET с помощью Azure Cloud and Windows Containers | Когда следует развертывать контейнеры Windows в службе "экземпляры контейнеров Azure" (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577937"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="40eb7-103">Когда следует развертывать контейнеры Windows в службе "экземпляры контейнеров Azure" (ACI)</span><span class="sxs-lookup"><span data-stu-id="40eb7-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="40eb7-104">Основное выгодное предложение для экземпляров контейнеров Azure заключается в том, что вы можете сразу же развернуть в нем контейнеры, и вам не нужно поддерживать эту среду, вам не нужно обновлять или исправлять базовую операционную систему или виртуальные машины, прозрачные и просто развертываемые контейнеры в готовую к использованию среду.</span><span class="sxs-lookup"><span data-stu-id="40eb7-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="40eb7-105">Причины и сценарии использования ACI похожи на основные сценарии при использовании виртуальных машин Azure с контейнерами, поэтому основные сценарии использования экземпляров контейнеров Azure:</span><span class="sxs-lookup"><span data-stu-id="40eb7-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="40eb7-106">**Сценарии разработки и тестирования**</span><span class="sxs-lookup"><span data-stu-id="40eb7-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="40eb7-107">**Автоматизация задач**</span><span class="sxs-lookup"><span data-stu-id="40eb7-107">**Task automation**</span></span>
- <span data-ttu-id="40eb7-108">**Агенты CI/CD**</span><span class="sxs-lookup"><span data-stu-id="40eb7-108">**CI/CD agents**</span></span>
- <span data-ttu-id="40eb7-109">**Малый или масштабируемый Пакетная обработка**</span><span class="sxs-lookup"><span data-stu-id="40eb7-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="40eb7-110">**Простые веб-приложения**</span><span class="sxs-lookup"><span data-stu-id="40eb7-110">**Simple web apps**</span></span>

<span data-ttu-id="40eb7-111">Простой сценарий веб-приложений является справедливым сценарием для ACI, но учитывается, что, поскольку в ACI вы можете иметь только один экземпляр контейнера для каждого образа контейнера, вы не сможете обеспечить высокий уровень доступности и ограничить масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="40eb7-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="40eb7-112">Тем не менее, даже если ACI считается инфраструктурой, так как он просто предоставляет отдельные экземпляры контейнеров, существует огромное преимущество по сравнению с обычными виртуальными машинами Azure с Windows Server.</span><span class="sxs-lookup"><span data-stu-id="40eb7-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="40eb7-113">С помощью ACI вы просто развертываете контейнеры в среде самообслуживания, и вы просто платите за эти контейнеры.</span><span class="sxs-lookup"><span data-stu-id="40eb7-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="40eb7-114">Вам не нужно поддерживать и обновлять виртуальные машины, поэтому это гораздо лучшая платформа для большинства сценариев, в которых могут использоваться виртуальные машины с контейнерами.</span><span class="sxs-lookup"><span data-stu-id="40eb7-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="40eb7-115">Используя ACI, вы просто развертываете контейнер, поэтому нет необходимости создавать среду виртуальной машины, в которой просто развертываются контейнеры.</span><span class="sxs-lookup"><span data-stu-id="40eb7-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="40eb7-116">Ниже приведены основные преимущества службы "экземпляры контейнеров Azure" (ACI).</span><span class="sxs-lookup"><span data-stu-id="40eb7-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="40eb7-117">Выполнение контейнеров без управления серверами</span><span class="sxs-lookup"><span data-stu-id="40eb7-117">Run containers without managing servers</span></span>
- <span data-ttu-id="40eb7-118">Повышение гибкости с помощью контейнеров по требованию</span><span class="sxs-lookup"><span data-stu-id="40eb7-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="40eb7-119">Развертывайте контейнеры в облаке с непревзойденной простотой и скоростью — с помощью одной команды.</span><span class="sxs-lookup"><span data-stu-id="40eb7-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="40eb7-120">Защита приложений с помощью изоляции гипервизора</span><span class="sxs-lookup"><span data-stu-id="40eb7-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="40eb7-121">Вкратце, с ACI вы можете быстро разрабатывать приложения без управления виртуальными машинами или изучать новые средства.</span><span class="sxs-lookup"><span data-stu-id="40eb7-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="40eb7-122">Это просто ваше приложение в контейнере, работающем в облаке.</span><span class="sxs-lookup"><span data-stu-id="40eb7-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="40eb7-123">[Назад](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Вперед](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="40eb7-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
