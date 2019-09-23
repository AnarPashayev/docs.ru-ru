---
title: Определение многоконтейнерного приложения с помощью docker-compose.yml
description: Как указать композицию микрослужб для многоконтейнерного приложения с помощью docker-compose.yml.
ms.date: 10/02/2018
ms.openlocfilehash: 8c0f1a654d27b32e613b84d3862198ad96f32e1c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039746"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="eac17-103">Определение многоконтейнерного приложения с помощью docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="eac17-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="eac17-104">В данном руководстве файл [docker-compose.yml](https://docs.docker.com/compose/compose-file/) был представлен в разделе [Шаг 4. Определение служб в файле docker-compose.yml при сборке многоконтейнерного приложения Docker](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="eac17-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="eac17-105">Тем не менее существуют дополнительные способы использования файлов docker-compose, которые стоит изучить более подробно.</span><span class="sxs-lookup"><span data-stu-id="eac17-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="eac17-106">Например, в файле docker-compose.yml вы можете явно описать, как следует развертывать ваше многоконтейнерное приложение.</span><span class="sxs-lookup"><span data-stu-id="eac17-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="eac17-107">При необходимости также можно описать, как вы планируете собирать свои пользовательские образы Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="eac17-108">(Пользовательские образы Docker можно также собрать с помощью Docker CLI.)</span><span class="sxs-lookup"><span data-stu-id="eac17-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="eac17-109">В сущности, вы определяете каждый из контейнеров, которые планируете развернуть, и конкретные характеристики для каждого развертывания контейнера.</span><span class="sxs-lookup"><span data-stu-id="eac17-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="eac17-110">Создав файл описания многоконтейнерного развертывания, вы можете развернуть все решение в одном действии, управляемом командой CLI [docker-compose up](https://docs.docker.com/compose/overview/), или развернуть решение прозрачно из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eac17-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="eac17-111">В противном случае придется использовать Docker CLI, чтобы разворачивать контейнер за контейнером в несколько этапов с помощью команды `docker run` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="eac17-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="eac17-112">Таким образом, для каждой службы, определенной в файле docker-compose.yml, необходимо указать ровно один образ или сборку.</span><span class="sxs-lookup"><span data-stu-id="eac17-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="eac17-113">Остальные ключи являются необязательными и соответствуют своим аналогам в командной строке `docker run`.</span><span class="sxs-lookup"><span data-stu-id="eac17-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="eac17-114">В следующем примере кода YAML представлено определение возможно глобального, но единственного файла docker-compose.yml для примера eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eac17-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="eac17-115">Это ненастоящий файл docker-compose из eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eac17-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="eac17-116">Это упрощенная и объединенная в один файл версия, представляющая не лучший способ работы с файлами docker-compose, как будет показано ниже.</span><span class="sxs-lookup"><span data-stu-id="eac17-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="eac17-117">Корневой ключ в этом файле — services.</span><span class="sxs-lookup"><span data-stu-id="eac17-117">The root key in this file is services.</span></span> <span data-ttu-id="eac17-118">Под этим ключом определяются службы, которые требуется развернуть и запустить при выполнении команды `docker-compose up` или при развертывании из Visual Studio с помощью этого файла docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="eac17-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="eac17-119">В данном случае в файле docker-compose.yml определено несколько служб, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="eac17-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="eac17-120">Имя службы</span><span class="sxs-lookup"><span data-stu-id="eac17-120">Service name</span></span> | <span data-ttu-id="eac17-121">Описание</span><span class="sxs-lookup"><span data-stu-id="eac17-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="eac17-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="eac17-122">webmvc</span></span>       | <span data-ttu-id="eac17-123">Контейнер, включающий приложение MVC ASP.NET Core и использующий микрослужбы из C\# на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="eac17-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="eac17-124">catalog.api</span><span class="sxs-lookup"><span data-stu-id="eac17-124">catalog.api</span></span>  | <span data-ttu-id="eac17-125">Контейнер, включающий микрослужбу Catalog веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="eac17-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="eac17-126">ordering.api</span><span class="sxs-lookup"><span data-stu-id="eac17-126">ordering.api</span></span> | <span data-ttu-id="eac17-127">Контейнер, включающий микрослужбу Ordering веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="eac17-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="eac17-128">sql.data</span><span class="sxs-lookup"><span data-stu-id="eac17-128">sql.data</span></span>     | <span data-ttu-id="eac17-129">Контейнер, запускающий SQL Server для Linux, в котором содержатся базы данных микрослужб.</span><span class="sxs-lookup"><span data-stu-id="eac17-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="eac17-130">basket.api</span><span class="sxs-lookup"><span data-stu-id="eac17-130">basket.api</span></span>   | <span data-ttu-id="eac17-131">Контейнер с микрослужбой Basket веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eac17-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="eac17-132">basket.data</span><span class="sxs-lookup"><span data-stu-id="eac17-132">basket.data</span></span>  | <span data-ttu-id="eac17-133">Контейнер, запускающий службу кэша REDIS, с базой данных basket в качестве кэша REDIS.</span><span class="sxs-lookup"><span data-stu-id="eac17-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="eac17-134">Простой контейнер API веб-службы</span><span class="sxs-lookup"><span data-stu-id="eac17-134">A simple Web Service API container</span></span>

<span data-ttu-id="eac17-135">Рассмотрим один контейнер. Контейнер-микрослужба catalog.api имеет простое определение:</span><span class="sxs-lookup"><span data-stu-id="eac17-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="eac17-136">Эта контейнерная служба имеет следующую базовую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="eac17-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="eac17-137">Она основывается на пользовательском образе eshop/catalog.api.</span><span class="sxs-lookup"><span data-stu-id="eac17-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="eac17-138">Проще говоря, в файле не задан ключ build:.</span><span class="sxs-lookup"><span data-stu-id="eac17-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="eac17-139">Это означает, что образ должен быть предварительно создан (с помощью команды docker build) или скачан (с помощью команды docker pull) из любого реестра Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="eac17-140">Она определяет переменную среды с именем ConnectionString со строкой подключения, которая должна использоваться Entity Framework для доступа к экземпляру SQL Server, содержащему модель данных каталога.</span><span class="sxs-lookup"><span data-stu-id="eac17-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="eac17-141">В данном случае в одном контейнере SQL Server содержатся несколько баз данных.</span><span class="sxs-lookup"><span data-stu-id="eac17-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="eac17-142">Поэтому на компьютере разработки потребуется меньше памяти для Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="eac17-143">Однако можно было бы также развернуть по одному контейнеру SQL Server для каждой базы данных микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="eac17-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="eac17-144">Имя SQL Server — sql.data; это же имя используется для контейнера, в котором выполняется экземпляр SQL Server для Linux.</span><span class="sxs-lookup"><span data-stu-id="eac17-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="eac17-145">Это удобно; благодаря этой возможности служба разрешения имен (внутренняя для узла Docker) будет разрешать сетевой адрес, так что вам не нужно знать внутренний IP-адрес для контейнеров при доступе к ним из других контейнеров.</span><span class="sxs-lookup"><span data-stu-id="eac17-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="eac17-146">Так как строка подключения определяется переменной среды, можно задавать эту переменную посредством другого механизма и в другое время.</span><span class="sxs-lookup"><span data-stu-id="eac17-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="eac17-147">Например, можно задать другую строку подключения при развертывании в рабочей среде на финальных узлах или сделать это из конвейеров CI/CD в Azure DevOps Services или в другой предпочитаемой системе DevOps.</span><span class="sxs-lookup"><span data-stu-id="eac17-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="eac17-148">Она представляет порт 80 для внутреннего доступа к службе catalog.api в узле Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="eac17-149">В данном случае этот узел является виртуальной машиной Linux, так как он основан на образе Docker для Linux, но можно настроить контейнер для запуска в образе Windows.</span><span class="sxs-lookup"><span data-stu-id="eac17-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="eac17-150">Она переадресует предоставленный порт 80 в порт 5101 на хост-компьютере Docker (виртуальной машине Linux).</span><span class="sxs-lookup"><span data-stu-id="eac17-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="eac17-151">Она связывает веб-службу со службой sql.data (экземпляром SQL Server для базы данных Linux, запущенным в контейнере).</span><span class="sxs-lookup"><span data-stu-id="eac17-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="eac17-152">Если вы указываете эту зависимость, контейнер catalog.api не будет запускаться до запуска контейнера sql.data. Это важно, поскольку для catalog.api требуется уже запущенная база данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eac17-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="eac17-153">Тем не менее во многих случаях недостаточно использовать этот вид зависимости контейнера, так как Docker выполняет проверку только на уровне контейнера.</span><span class="sxs-lookup"><span data-stu-id="eac17-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="eac17-154">Иногда служба (в данном случае SQL Server) может быть еще не готова, поэтому рекомендуется реализовать в клиентских микрослужбах логику повторов с экспоненциальным отходом.</span><span class="sxs-lookup"><span data-stu-id="eac17-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="eac17-155">Таким образом, если контейнер зависимостей будет не готов в течение некоторого времени, приложение по-прежнему будет устойчивым.</span><span class="sxs-lookup"><span data-stu-id="eac17-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="eac17-156">Она настроена для разрешения доступа к внешним серверам: параметр extra\_hosts позволяет получать доступ к внешним серверам или компьютерам за пределами узла Docker (то есть за пределами виртуальной машины Linux по умолчанию, которая является узлом разработки Docker), таким как локальный экземпляр SQL Server на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="eac17-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="eac17-157">В файле docker-compose.yml также имеются другие, более сложные параметры, которые рассматриваются в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="eac17-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="eac17-158">Использование файлов docker-compose для нескольких сред</span><span class="sxs-lookup"><span data-stu-id="eac17-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="eac17-159">Файлы docker-compose.yml являются файлами определения и могут использоваться несколькими инфраструктурами, которые распознают этот формат.</span><span class="sxs-lookup"><span data-stu-id="eac17-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="eac17-160">Самым простым средством является команда docker-compose.</span><span class="sxs-lookup"><span data-stu-id="eac17-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="eac17-161">Таким образом, используя команду docker-compose, вы можете реализовать следующие основные сценарии.</span><span class="sxs-lookup"><span data-stu-id="eac17-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="eac17-162">Среды разработки</span><span class="sxs-lookup"><span data-stu-id="eac17-162">Development environments</span></span>

<span data-ttu-id="eac17-163">При разработке приложений важно иметь возможность запускать приложение в изолированной среде разработки.</span><span class="sxs-lookup"><span data-stu-id="eac17-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="eac17-164">Можно создать такую среду с помощью команды CLI docker-compose или использовать Visual Studio, в котором команда docker-compose применяется внутренним образом.</span><span class="sxs-lookup"><span data-stu-id="eac17-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="eac17-165">Файл docker-compose.yml позволяет настраивать и документировать все зависимости служб вашего приложения (другие службы, кэш, базы данных, очереди и т. п.).</span><span class="sxs-lookup"><span data-stu-id="eac17-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="eac17-166">С помощью команды CLI docker-compose вы можете создавать и запускать один или несколько контейнеров для каждой зависимости одной командой (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="eac17-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="eac17-167">Файлы docker-compose.yml — это файлы конфигурации, интерпретированные подсистемой Docker, но они также служат в качестве удобных файлов документирования сведений о составе вашего многоконтейнерного приложения.</span><span class="sxs-lookup"><span data-stu-id="eac17-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="eac17-168">Тестовые среды</span><span class="sxs-lookup"><span data-stu-id="eac17-168">Testing environments</span></span>

<span data-ttu-id="eac17-169">Важной частью любого процесса непрерывного развертывания (CD) или непрерывной интеграции (CI) являются модульные тесты и интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="eac17-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="eac17-170">Для этих автоматических тестов требуется изолированная среда, чтобы на них не влияли пользователи или какие-либо изменения данных в приложении.</span><span class="sxs-lookup"><span data-stu-id="eac17-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="eac17-171">Используя Docker Compose, можно очень просто создавать и уничтожать такую изолированную среду с помощью нескольких команд, выполненных в командной строке, или скриптов; например, с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="eac17-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="eac17-172">Рабочие развертывания</span><span class="sxs-lookup"><span data-stu-id="eac17-172">Production deployments</span></span>

<span data-ttu-id="eac17-173">Команду Compose можно также использовать для развертывания в удаленной подсистеме Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="eac17-174">Типичный случай — развертывание на один экземпляр узла Docker (такой как рабочая виртуальная машина или сервер с установленной [машиной Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="eac17-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="eac17-175">При использовании любых других оркестраторов (Azure Service Fabric, Kubernetes и т. п.) может потребоваться добавить параметры настройки и конфигурации метаданных, аналогичные имеющимся в файле docker-compose.yml, но в формате, необходимом для этого другого оркестратора.</span><span class="sxs-lookup"><span data-stu-id="eac17-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="eac17-176">В любом случае docker-compose является удобным инструментом и форматом метаданных для рабочих процессов развертывания, тестирования и работы, хотя рабочий процесс работы может отличаться в зависимости от используемого оркестратора.</span><span class="sxs-lookup"><span data-stu-id="eac17-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="eac17-177">Использование нескольких файлов docker-compose для обработки разных сред</span><span class="sxs-lookup"><span data-stu-id="eac17-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="eac17-178">Если планируются разные среды, необходимо использовать несколько файлов compose.</span><span class="sxs-lookup"><span data-stu-id="eac17-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="eac17-179">Это позволяет создать несколько вариантов конфигурации в зависимости от среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="eac17-180">Переопределение базового файла docker-compose</span><span class="sxs-lookup"><span data-stu-id="eac17-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="eac17-181">Вы можете использовать единственный файл docker-compose.yml, как показано в упрощенных примерах, приведенных в предыдущих разделах.</span><span class="sxs-lookup"><span data-stu-id="eac17-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="eac17-182">Однако для большинства приложений это не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="eac17-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="eac17-183">По умолчанию Compose читает два файла, docker-compose.yml и дополнительный файл docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="eac17-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="eac17-184">Как показано на рисунке 6-11, если вы работаете в Visual Studio и включаете поддержку Docker, Visual Studio при этом создает дополнительный файл docker-compose.vs.debug.g.yml для отладки приложения, вы можете просмотреть этот файл в папке obj\\Docker\\ в главной папке решения.</span><span class="sxs-lookup"><span data-stu-id="eac17-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Структура файла проекта docker-compose: .dockerignore — для пропуска файлов; docker-compose.yml — для создания микрослужб; docker-compose.override.yml — для настройки среды микрослужб.](./media/image12.png)

<span data-ttu-id="eac17-186">**Рис. 6-11**.</span><span class="sxs-lookup"><span data-stu-id="eac17-186">**Figure 6-11**.</span></span> <span data-ttu-id="eac17-187">Файлы docker-compose в Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="eac17-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="eac17-188">Файлы docker-compose можно изменить в любом редакторе, например в Visual Studio Code или Sublime, и запустить приложение с помощью команды docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="eac17-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="eac17-189">По определению файл docker-compose.yml содержит базовую конфигурацию и другие статические параметры.</span><span class="sxs-lookup"><span data-stu-id="eac17-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="eac17-190">Это означает, что конфигурация службы не должна изменяться в зависимости от целевой среды развертывания.</span><span class="sxs-lookup"><span data-stu-id="eac17-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="eac17-191">Файл docker-compose.override.yml, как следует из его имени, содержит параметры конфигурации, которые переопределяют базовую конфигурацию, например конфигурацию, зависящую от среды развертывания.</span><span class="sxs-lookup"><span data-stu-id="eac17-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="eac17-192">У вас может быть несколько файлов переопределения с разными именами.</span><span class="sxs-lookup"><span data-stu-id="eac17-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="eac17-193">Файлы переопределения обычно содержат дополнительные сведения, необходимые для приложения, но относящиеся к конкретной среде или развертыванию.</span><span class="sxs-lookup"><span data-stu-id="eac17-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="eac17-194">Планирование нескольких сред</span><span class="sxs-lookup"><span data-stu-id="eac17-194">Targeting multiple environments</span></span>

<span data-ttu-id="eac17-195">Распространенный вариант использования заключается в том, что определяется несколько файлов compose, чтобы можно было планировать несколько сред, таких как рабочая среда, промежуточная среда, среда CI или среда разработки.</span><span class="sxs-lookup"><span data-stu-id="eac17-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="eac17-196">Для поддержки этих разных сред можно разделить конфигурацию Compose на несколько файлов, как показано на рисунке 6-12.</span><span class="sxs-lookup"><span data-stu-id="eac17-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Вы можете сочетать несколько файлов docker-compose\*.fml для обработки разных сред.](./media/image13.png)

<span data-ttu-id="eac17-198">**Рис. 6-12**.</span><span class="sxs-lookup"><span data-stu-id="eac17-198">**Figure 6-12**.</span></span> <span data-ttu-id="eac17-199">Несколько файлов docker-compose, переопределяющих значения в базовом файле docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="eac17-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="eac17-200">Вы начинаете с базового файла docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="eac17-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="eac17-201">Этот базовый файл должен содержать базовые или статические параметры конфигурации, которые не изменяются в зависимости от среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="eac17-202">Например, eShopOnContainers имеет в качестве базового файла следующий файл docker-compose.yml (упрощен путем уменьшения числа служб).</span><span class="sxs-lookup"><span data-stu-id="eac17-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="eac17-203">Значения в базовом файле docker-compose.yml не должны изменяться из-за разных целевых сред развертывания.</span><span class="sxs-lookup"><span data-stu-id="eac17-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="eac17-204">Если рассмотреть, например, определение службы webmvc, то можно увидеть, что эта информация большей частью одинакова независимо от планируемой среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="eac17-205">В этом определении содержится следующая информация.</span><span class="sxs-lookup"><span data-stu-id="eac17-205">You have the following information:</span></span>

- <span data-ttu-id="eac17-206">Имя службы: webmvc.</span><span class="sxs-lookup"><span data-stu-id="eac17-206">The service name: webmvc.</span></span>

- <span data-ttu-id="eac17-207">Пользовательский образ контейнера: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="eac17-207">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="eac17-208">Команда для создания пользовательского образа Docker, указывающая, какой Dockerfile следует использовать.</span><span class="sxs-lookup"><span data-stu-id="eac17-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="eac17-209">Зависимости от других служб, чтобы данный контейнер не запускался до запуска других контейнеров зависимостей.</span><span class="sxs-lookup"><span data-stu-id="eac17-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="eac17-210">У вас могут быть дополнительные параметры конфигурации, но суть в том, что в базовом файле docker-compose.yml вы просто задаете ту информацию, которая является общей для всех сред.</span><span class="sxs-lookup"><span data-stu-id="eac17-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="eac17-211">Затем в файле docker-compose.override.yml или в аналогичных файлах для рабочей или промежуточной среды необходимо указать конфигурацию, характерную для каждой среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="eac17-212">Обычно файл docker-compose.override.yml используется для среды разработки, как в следующем примере из eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eac17-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity.api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="eac17-213">В этом примере конфигурация переопределения для среды разработки представляет некоторые порты для узла, задает переменные среды с URL-адресами перенаправления, а также указывает строки подключения для среды разработки.</span><span class="sxs-lookup"><span data-stu-id="eac17-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="eac17-214">Все эти параметры предназначены только для среды разработки.</span><span class="sxs-lookup"><span data-stu-id="eac17-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="eac17-215">При выполнении команды `docker-compose up` (или запуске ее из Visual Studio) эта команда считывает переопределения автоматически, как если бы оба файла были объединены.</span><span class="sxs-lookup"><span data-stu-id="eac17-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="eac17-216">Предположим, что требуется другой файл Compose для рабочей среды, с другими значениями конфигурации, портами или строками подключения.</span><span class="sxs-lookup"><span data-stu-id="eac17-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="eac17-217">Вы можете создать другой файл переопределения, например с именем `docker-compose.prod.yml`, содержащий другие параметры и переменные среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="eac17-218">Этот файл может храниться в другом репозитории Git или управляться и защищаться другой группой.</span><span class="sxs-lookup"><span data-stu-id="eac17-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="eac17-219">Развертывание с помощью конкретного файла переопределения</span><span class="sxs-lookup"><span data-stu-id="eac17-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="eac17-220">Чтобы использовать несколько файлов переопределения или файл переопределения с другим именем, можно указать эти файлы с помощью параметра -f в команде docker-compose.</span><span class="sxs-lookup"><span data-stu-id="eac17-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="eac17-221">Команда compose объединяет файлы в том порядке, в котором они указаны в командной строке.</span><span class="sxs-lookup"><span data-stu-id="eac17-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="eac17-222">В следующем примере показано, как выполняется развертывание с файлами переопределения.</span><span class="sxs-lookup"><span data-stu-id="eac17-222">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="eac17-223">Использование переменных среды в файлах docker-compose</span><span class="sxs-lookup"><span data-stu-id="eac17-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="eac17-224">Удобно, особенно в рабочих средах, иметь возможность получать сведения о конфигурации из переменных среды, как показано в предыдущих примерах.</span><span class="sxs-lookup"><span data-stu-id="eac17-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="eac17-225">Вы можете сослаться на переменную среды в файлах docker-compose делаются с помощью синтаксиса ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="eac17-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="eac17-226">Следующая строка из файла docker-compose.prod.yml показывает, как ссылаться на значение переменной среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="eac17-227">Переменные среды создаются и инициализируются разными способами в зависимости от среды узла (Linux, Windows, кластер Cloud и т. п.).</span><span class="sxs-lookup"><span data-stu-id="eac17-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="eac17-228">Однако рекомендуется использовать ENV-файл.</span><span class="sxs-lookup"><span data-stu-id="eac17-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="eac17-229">Файлы docker-compose поддерживает объявление переменных среды по умолчанию в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="eac17-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="eac17-230">Эти значения для переменных среды являются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="eac17-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="eac17-231">Однако они могут быть переопределены значениями, которые, возможно, заданы в каждой из сред (ОС узла или переменные среды из кластера).</span><span class="sxs-lookup"><span data-stu-id="eac17-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="eac17-232">Этот ENV-файл следует поместить в ту папку, из которой выполняется команда docker-compose.</span><span class="sxs-lookup"><span data-stu-id="eac17-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="eac17-233">В следующем примере показан ENV-файл, аналогичный [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env)-файлу для приложения eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eac17-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```env
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="eac17-234">Для команды docker-compose необходимо, чтобы каждая строка в ENV-файле была в формате \<переменная\>=\<значение\>.</span><span class="sxs-lookup"><span data-stu-id="eac17-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="eac17-235">Обратите внимание, что значения, установленные в среде выполнения, всегда переопределяют значения, определенные в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="eac17-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="eac17-236">Аналогичным образом значения, переданные с помощью аргументов командной строки, тоже переопределяют значения по умолчанию, заданные в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="eac17-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="eac17-237">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="eac17-237">Additional resources</span></span>

- <span data-ttu-id="eac17-238">**Общие сведения о Docker Compose** </span><span class="sxs-lookup"><span data-stu-id="eac17-238">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="eac17-239">**Несколько файлов Compose** </span><span class="sxs-lookup"><span data-stu-id="eac17-239">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="eac17-240">Создание оптимизированных образов Docker ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eac17-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="eac17-241">Если вы изучаете Docker и .NET Core по источникам в Интернете, вы обнаружите файлы Dockerfile, демонстрирующие простоту создания образа Docker путем копирования источника в контейнер.</span><span class="sxs-lookup"><span data-stu-id="eac17-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="eac17-242">Эти примеры показывают, что, используя простую конфигурацию, можно получить образ Docker со средой, упакованной с приложением.</span><span class="sxs-lookup"><span data-stu-id="eac17-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="eac17-243">В следующем примере показан такой простой Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="eac17-243">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="eac17-244">Такой Dockerfile будет работать.</span><span class="sxs-lookup"><span data-stu-id="eac17-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="eac17-245">Тем не менее вы можете существенно оптимизировать ваши образы, особенно образы рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="eac17-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="eac17-246">В модели контейнера и микрослужб вы постоянно запускаете контейнеры.</span><span class="sxs-lookup"><span data-stu-id="eac17-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="eac17-247">Обычно контейнеры используются таким образом, чтобы не перезапускать спящий контейнер, так как контейнер является одноразовым.</span><span class="sxs-lookup"><span data-stu-id="eac17-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="eac17-248">Оркестраторы (такие как Kubernetes и Azure Service Fabric) просто создают экземпляры образов.</span><span class="sxs-lookup"><span data-stu-id="eac17-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="eac17-249">Это означает, что вам нужно будет выполнить оптимизацию путем предварительной компиляции приложения во время его сборки, чтобы ускорить процесс создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="eac17-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="eac17-250">Когда контейнер запускается, он должен быть готов к выполнению.</span><span class="sxs-lookup"><span data-stu-id="eac17-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="eac17-251">Не следует выполнять восстановление и компиляцию во время выполнения с помощью команд `dotnet restore` и `dotnet build` из dotnet CLI, как показано в нескольких записях блога о .NET Core и Docker.</span><span class="sxs-lookup"><span data-stu-id="eac17-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="eac17-252">Команда .NET выполняет важнейшую работу, чтобы сделать .NET Core и ASP.NET Core платформой, оптимизированной для работы с контейнерами.</span><span class="sxs-lookup"><span data-stu-id="eac17-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="eac17-253">.NET Core является не только облегченной платформой с небольшим объемом памяти; команда разработчиков сконцентрировалась на оптимизированных образах Docker для трех основных сценариев и опубликовала их в реестре центра Docker по адресу *dotnet/core*, начиная с версии 2.1:</span><span class="sxs-lookup"><span data-stu-id="eac17-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="eac17-254">**Разработка**: здесь приоритетной является возможность быстрой интеграции и отладки изменений, а размер вторичен.</span><span class="sxs-lookup"><span data-stu-id="eac17-254">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="eac17-255">**Сборка**: здесь приоритетным направлением является компиляция приложения, включая двоичные файлы и другие зависимости для их оптимизации.</span><span class="sxs-lookup"><span data-stu-id="eac17-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="eac17-256">**Рабочая среда**: здесь основное внимание уделяется быстрому развертыванию и запуску контейнеров, поэтому эти образы ограничены двоичными файлами и содержимым, необходимым для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="eac17-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="eac17-257">Для этого команда .NET предоставляет в [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (в Docker Hub) четыре основных сборки:</span><span class="sxs-lookup"><span data-stu-id="eac17-257">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="eac17-258">**sdk**: для сценариев разработки и сборки;</span><span class="sxs-lookup"><span data-stu-id="eac17-258">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="eac17-259">**aspnet**: для производственных сценариев ASP.NET;</span><span class="sxs-lookup"><span data-stu-id="eac17-259">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="eac17-260">**runtime**: для производственных сценариев .NET;</span><span class="sxs-lookup"><span data-stu-id="eac17-260">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="eac17-261">**runtime-deps**: для сценария рабочей среды у [автономных приложений](../../../core/deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="eac17-261">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#self-contained-deployments-scd).</span></span>

<span data-ttu-id="eac17-262">Чтобы ускорить запуск, образы среды выполнения также автоматически настраивают aspnetcore\_urls на порт 80 и использование Ngen для создания собственного кэша образов для сборок.</span><span class="sxs-lookup"><span data-stu-id="eac17-262">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="eac17-263">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="eac17-263">Additional resources</span></span>

- <span data-ttu-id="eac17-264">**Создание оптимизированных образов Docker в ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="eac17-264">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- <span data-ttu-id="eac17-265">**Создание образов Docker для приложений .NET Core**</span><span class="sxs-lookup"><span data-stu-id="eac17-265">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

> [!div class="step-by-step"]
> <span data-ttu-id="eac17-266">[Назад](data-driven-crud-microservice.md)
> [Вперед](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="eac17-266">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
