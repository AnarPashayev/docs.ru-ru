---
title: Контейнеры, образы и реестры Docker
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Контейнеры, образы и реестры Docker
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639906"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="9224c-103">Контейнеры, образы и реестры Docker</span><span class="sxs-lookup"><span data-stu-id="9224c-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="9224c-104">При использовании Docker разработчик создает приложение или службу и упаковывает приложение или службу и их зависимости в образ контейнера.</span><span class="sxs-lookup"><span data-stu-id="9224c-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="9224c-105">Образ — это статическое представление приложения или службы, а также их конфигурации и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="9224c-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="9224c-106">Для запуска приложения или службы создается экземпляр образа приложения, чтобы создать контейнер, который будет запущен на узле Docker.</span><span class="sxs-lookup"><span data-stu-id="9224c-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="9224c-107">Контейнеры изначально проверяются в среде разработки или на ПК.</span><span class="sxs-lookup"><span data-stu-id="9224c-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="9224c-108">Разработчикам следует хранить образы в реестре, который выступает в качестве библиотеки образов и необходим при развертывании на оркестраторы в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="9224c-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="9224c-109">Docker поддерживает общедоступный реестр с помощью [Docker Hub](https://hub.docker.com/). Другие поставщики предлагают реестры для различных коллекций образов, включая [Реестр контейнеров Azure](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="9224c-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="9224c-110">Кроме того, организации могут развернуть локальные частные реестры для своих образов Docker.</span><span class="sxs-lookup"><span data-stu-id="9224c-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="9224c-111">На рисунке 2-4 показано, как образы и реестры в Docker связаны с другими компонентами.</span><span class="sxs-lookup"><span data-stu-id="9224c-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="9224c-112">На нем также показано несколько вариантов реестра от поставщиков.</span><span class="sxs-lookup"><span data-stu-id="9224c-112">It also shows the multiple registry offerings from vendors.</span></span>

![Базовая таксономия в Docker. Реестр напоминает книжную полку. В нем хранятся образы, которые можно извлекать для создания контейнеров, необходимых для запуска служб или веб-приложений.](./media/image5.PNG)

<span data-ttu-id="9224c-117">**Рис. 2-4**.</span><span class="sxs-lookup"><span data-stu-id="9224c-117">**Figure 2-4**.</span></span> <span data-ttu-id="9224c-118">Классификация основных понятий и терминов Docker</span><span class="sxs-lookup"><span data-stu-id="9224c-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="9224c-119">Размещение образов в реестре позволяет хранить статические и неизменяемые фрагменты приложений, включая всех их зависимости на уровне платформы.</span><span class="sxs-lookup"><span data-stu-id="9224c-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="9224c-120">Эти образы можно добавить в систему управления версиями и развернуть в нескольких средах, таким образом, каждый образ представляет согласованную единицу развертывания.</span><span class="sxs-lookup"><span data-stu-id="9224c-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="9224c-121">Частные реестры образов, размещенные локально или в облаке, рекомендуется использовать, если:</span><span class="sxs-lookup"><span data-stu-id="9224c-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="9224c-122">Ваши образы не могут быть открыты для общего доступа по соображениям конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="9224c-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="9224c-123">Вам необходимо обеспечить минимальную сетевую задержку между образами и выбранной средой развертывания.</span><span class="sxs-lookup"><span data-stu-id="9224c-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="9224c-124">Например, если рабочая среда представляет собой облако Azure, вы, вероятно, захотите разместить образы в [Реестре контейнеров Azure](https://azure.microsoft.com/services/container-registry/), чтобы сетевая задержка была минимальной.</span><span class="sxs-lookup"><span data-stu-id="9224c-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="9224c-125">Точно так же, если рабочая среда является локальной, вы можете развернуть локальный доверенный реестр Docker в той же локальной сети.</span><span class="sxs-lookup"><span data-stu-id="9224c-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9224c-126">[Назад](docker-terminology.md)
>[Вперед](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="9224c-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
