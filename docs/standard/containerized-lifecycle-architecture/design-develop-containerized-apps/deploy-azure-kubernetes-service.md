---
title: Управление микрослужбами и многоконтейнерными приложениями для обеспечения высокого уровня масштабируемости и доступности
description: Сведения о развертывании приложения с помощью службы Azure Kubernetes.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644665"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="c1f8e-103">Развертывание в службе Azure Kubernetes (AKS)</span><span class="sxs-lookup"><span data-stu-id="c1f8e-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="c1f8e-104">Вы можете взаимодействовать с AKS с помощью основной клиентской операционной системы, здесь мы покажем, как сделать это с помощью Microsoft Windows и встроенная версия Ubuntu Linux в Windows, с помощью команд Bash.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="c1f8e-105">Перечислены предварительные условия, чтобы перед использованием AKS.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="c1f8e-106">Компьютер разработки Mac или Linux</span><span class="sxs-lookup"><span data-stu-id="c1f8e-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="c1f8e-107">Компьютер разработки Windows</span><span class="sxs-lookup"><span data-stu-id="c1f8e-107">Windows development machine</span></span>
  - <span data-ttu-id="c1f8e-108">В Windows включен режим разработчика</span><span class="sxs-lookup"><span data-stu-id="c1f8e-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="c1f8e-109">Подсистема Windows для Linux</span><span class="sxs-lookup"><span data-stu-id="c1f8e-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="c1f8e-110">Установлен на Azure-CLI [Windows, Mac или Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="c1f8e-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="c1f8e-111">Чтобы найти подробные сведения о:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-111">To find complete information about:</span></span>
>
> <span data-ttu-id="c1f8e-112">Azure CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="c1f8e-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="c1f8e-113">Подсистема Windows для Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="c1f8e-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="c1f8e-114">Создание среды AKS в Azure</span><span class="sxs-lookup"><span data-stu-id="c1f8e-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="c1f8e-115">Чтобы создать среду для AKS несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="c1f8e-116">Это можно сделать с помощью команд интерфейса командной строки Azure или с помощью портала Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="c1f8e-117">Здесь вы можете изучить некоторые примеры использования Azure CLI для создания кластера и на портале Azure, чтобы ознакомиться с результатами.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="c1f8e-118">Необходимо также иметь Kubectl и Docker на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="c1f8e-119">Создание кластера AKS</span><span class="sxs-lookup"><span data-stu-id="c1f8e-119">Create the AKS cluster</span></span>

<span data-ttu-id="c1f8e-120">Создайте кластер AKS с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="c1f8e-121">После завершения создания задания, вы увидите AKS, созданные на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="c1f8e-122">Группа ресурсов:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-122">The resource group:</span></span>

![Представление группы ресурсов Azure AKS в браузере.](media/aks-resource-group-view.png)

<span data-ttu-id="c1f8e-124">**Рис. 4-17**.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-124">**Figure 4-17**.</span></span> <span data-ttu-id="c1f8e-125">Представление группы ресурсов AKS из Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="c1f8e-126">Кластер AKS:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-126">The AKS cluster:</span></span>

![Представление группы ресурсов AKS в браузере.](media/aks-cluster-view.png)

<span data-ttu-id="c1f8e-128">**Рис. 4-18**.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-128">**Figure 4-18**.</span></span> <span data-ttu-id="c1f8e-129">Представление AKS из Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-129">AKS view from Azure.</span></span>

<span data-ttu-id="c1f8e-130">Вы также можете просмотреть узел, созданных с помощью `Azure-CLI` и `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="c1f8e-131">Во-первых получение учетных данных:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Выходные данные этой команды консоли: Объединенный «MsSampleK8Cluster как текущий контекст в /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="c1f8e-133">**Рис. 4-19**.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-133">**Figure 4-19**.</span></span> <span data-ttu-id="c1f8e-134">`aks get-credentials` результат команды.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="c1f8e-135">Затем, эффективное использование Kubectl узлов:</span><span class="sxs-lookup"><span data-stu-id="c1f8e-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Выходные данные выше командной консоли: Список узлов с состоянием, возраст (времени выполнения) и версии](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="c1f8e-137">**Рис. 4-20**.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-137">**Figure 4-20**.</span></span> <span data-ttu-id="c1f8e-138">`kubectl get nodes` результат команды.</span><span class="sxs-lookup"><span data-stu-id="c1f8e-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c1f8e-139">[Назад](orchestrate-high-scalability-availability.md)
>[Вперед](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8e-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
