---
title: Установка .NET Core на Fedora 29 — диспетчер пакетов — .NET Core
description: Используйте диспетчер пакетов для установки пакета SDK для .NET Core и среды выполнения на Fedora 29.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1cbe38f4f104a8e178d8bcfd1fa1bd6d7645261
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645298"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="34301-103">Диспетчер пакетов Fedora 29 — установка .NET Core</span><span class="sxs-lookup"><span data-stu-id="34301-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="34301-104">Эта статья описывает, как использовать диспетчер пакетов для установки .NET Core на Fedora 29.</span><span class="sxs-lookup"><span data-stu-id="34301-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="34301-105">Добавление ключа и веб-канала репозитория Майкрософт</span><span class="sxs-lookup"><span data-stu-id="34301-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="34301-106">Перед установкой .NET нужно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="34301-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="34301-107">добавить ключ подписывания пакета Майкрософт в список доверенных ключей;</span><span class="sxs-lookup"><span data-stu-id="34301-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="34301-108">добавить репозиторий в диспетчер пакетов;</span><span class="sxs-lookup"><span data-stu-id="34301-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="34301-109">установить необходимые зависимости.</span><span class="sxs-lookup"><span data-stu-id="34301-109">Install required dependencies.</span></span>

<span data-ttu-id="34301-110">Данную операцию достаточно выполнить один раз для каждого компьютера.</span><span class="sxs-lookup"><span data-stu-id="34301-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="34301-111">Откройте терминал и выполните приведенные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="34301-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="34301-112">Установка пакета SDK для .NET Core</span><span class="sxs-lookup"><span data-stu-id="34301-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="34301-113">Обновите продукты, доступные для установки, а затем установите пакет SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34301-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="34301-114">В терминале выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="34301-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="34301-115">Установка среды выполнения ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34301-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="34301-116">Обновите продукты, доступные для установки, а затем установите среду выполнения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="34301-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="34301-117">В терминале выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="34301-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="34301-118">Установка среды выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="34301-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="34301-119">Обновите продукты, доступные для установки, а затем установите среду выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34301-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="34301-120">В терминале выполните приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="34301-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="34301-121">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="34301-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="34301-122">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="34301-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="34301-123">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34301-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="34301-124">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="34301-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
