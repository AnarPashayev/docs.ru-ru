---
title: Удаление среды выполнения .NET Core и пакета SDK
description: В этой статье объясняется, как определить установленные в текущее время версии среды выполнения .NET Core и пакета SDK и как затем удалить их в Windows, Mac и Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970294"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="57f3e-103">Как удалить среду выполнения .NET Core и пакет SDK</span><span class="sxs-lookup"><span data-stu-id="57f3e-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="57f3e-104">По мере установки обновленных версий среды выполнения и пакета SDK .NET Core может потребоваться удалить устаревшие версии .NET Core с вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="57f3e-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="57f3e-105">При удалении более ранних версий среды выполнения может измениться среда выполнения, выбранная для запуска приложений общей платформы, как описано в статье [Выбор версии .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="57f3e-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="57f3e-106">Нужно ли удалять версию</span><span class="sxs-lookup"><span data-stu-id="57f3e-106">Should I remove a version?</span></span>

<span data-ttu-id="57f3e-107">[Выбор версии .NET Core](selection.md) и совместимость среды выполнения .NET Core для различных обновлений обеспечивает безопасное удаление предыдущих версий.</span><span class="sxs-lookup"><span data-stu-id="57f3e-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="57f3e-108">Обновления среды выполнения .NET Core совместимы в пределах основной версии, например 1.x или 2.x.</span><span class="sxs-lookup"><span data-stu-id="57f3e-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="57f3e-109">Кроме того, более поздние выпуски пакета SDK для .NET Core обычно позволяют создавать приложения, совместимые с предыдущими версиями среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="57f3e-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="57f3e-110">Как правило, требуется только последняя версия пакета SDK и последняя версия исправлений для сред выполнения, необходимых для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="57f3e-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="57f3e-111">К тем случаям, в которых сохраняются старые версии пакетов SDK или сред выполнения, относится поддержка приложений на основе **project.json**.</span><span class="sxs-lookup"><span data-stu-id="57f3e-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="57f3e-112">Если у приложения нет конкретных причин, по которым оно должно использовать ранние версии пакета SDK или среды выполнения, вы можете безопасно удалить старые версии.</span><span class="sxs-lookup"><span data-stu-id="57f3e-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="57f3e-113">Определите компоненты, которые нужно установить</span><span class="sxs-lookup"><span data-stu-id="57f3e-113">Determine what is installed</span></span>

<span data-ttu-id="57f3e-114">Начиная с .NET Core 2.1 можно определить версии пакета SDK и среды выполнения, установленных на вашем компьютере, с помощью команд в .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="57f3e-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="57f3e-115">Чтобы просмотреть список пакетов SDK, установленных на вашем компьютере, выполните команду [`dotnet --list-sdks`](../tools/dotnet.md#options).</span><span class="sxs-lookup"><span data-stu-id="57f3e-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="57f3e-116">Чтобы просмотреть список сред выполнения, установленных на вашем компьютере, выполните команду [`dotnet --list-runtimes`](../tools/dotnet.md#options).</span><span class="sxs-lookup"><span data-stu-id="57f3e-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="57f3e-117">Ниже приведены типичные выходные данные для Windows, macOS и Linux:</span><span class="sxs-lookup"><span data-stu-id="57f3e-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="57f3e-118">Windows</span><span class="sxs-lookup"><span data-stu-id="57f3e-118">Windows</span></span>](#tab/windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="57f3e-119">Linux</span><span class="sxs-lookup"><span data-stu-id="57f3e-119">Linux</span></span>](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[<span data-ttu-id="57f3e-120">macOS</span><span class="sxs-lookup"><span data-stu-id="57f3e-120">macOS</span></span>](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstalling-net-core"></a><span data-ttu-id="57f3e-121">Удаление .NET Core</span><span class="sxs-lookup"><span data-stu-id="57f3e-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="57f3e-122">Windows</span><span class="sxs-lookup"><span data-stu-id="57f3e-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="57f3e-123">Для удаления версий среды выполнения и пакета SDK .NET Core используется диалоговое окно **Установка и удаление программ** Windows.</span><span class="sxs-lookup"><span data-stu-id="57f3e-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="57f3e-124">На следующем рисунке показано диалоговое окно **Установка и удаление программ** с несколькими установленными версиями среды выполнения и пакета SDK .NET.</span><span class="sxs-lookup"><span data-stu-id="57f3e-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Диалоговое окно "Установка и удаление программ" для удаления .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="57f3e-126">Выберите все версии, которые необходимо удалить, и нажмите кнопку **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="57f3e-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="57f3e-127">Linux</span><span class="sxs-lookup"><span data-stu-id="57f3e-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="57f3e-128">В Linux есть несколько вариантов удаления .NET Core (пакета SDK или среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="57f3e-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="57f3e-129">Лучший способ удаления .NET Core — выполнить действие, противоположное тому, которое использовалось при установке .NET Core.</span><span class="sxs-lookup"><span data-stu-id="57f3e-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="57f3e-130">Конкретные действия зависят от выбранного дистрибутива и метода установки.</span><span class="sxs-lookup"><span data-stu-id="57f3e-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57f3e-131">Сведения об установке и удалении .NET Core для систем Red Hat см. в [Руководстве по началу работы с Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel).</span><span class="sxs-lookup"><span data-stu-id="57f3e-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="57f3e-132">Начиная с .NET Core 2.1 удалять пакет SDK для .NET Core при его обновлении с помощью диспетчера пакетов не нужно.</span><span class="sxs-lookup"><span data-stu-id="57f3e-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="57f3e-133">Диспетчер пакетов `update` или команды `refresh` автоматически удалят старую версию после успешной установки более новой версии.</span><span class="sxs-lookup"><span data-stu-id="57f3e-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="57f3e-134">Если вы установили .NET Core с помощью диспетчера пакетов, для удаления пакета SDK для .NET или среды выполнения используется тот же диспетчер пакетов.</span><span class="sxs-lookup"><span data-stu-id="57f3e-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="57f3e-135">.NET Core поддерживает большинство популярных менеджеров пакетов.</span><span class="sxs-lookup"><span data-stu-id="57f3e-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="57f3e-136">Точный синтаксис команды для вашей среды см. в документации по вашему дистрибутиву:</span><span class="sxs-lookup"><span data-stu-id="57f3e-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="57f3e-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) используется в системах на основе Debian, включая Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="57f3e-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="57f3e-138">[yum(8)](https://linux.die.net/man/8/yum) используется в Fedora, CentOS и Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="57f3e-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="57f3e-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) используется в openSUSE и SUSE Linux Enterprise System (SLES).</span><span class="sxs-lookup"><span data-stu-id="57f3e-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="57f3e-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) используется в Fedora.</span><span class="sxs-lookup"><span data-stu-id="57f3e-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="57f3e-141">Практически во всех случаях для удаления пакета используется команда `remove`.</span><span class="sxs-lookup"><span data-stu-id="57f3e-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="57f3e-142">Для установки пакета SDK для .NET Core в большинстве диспетчеров пакетов используется имя пакета `dotnet-sdk`, за которым следует номер версии.</span><span class="sxs-lookup"><span data-stu-id="57f3e-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="57f3e-143">Начиная с версии 2.1.300 пакета SDK для .NET Core и версии `2.1` среды выполнения необходимы только основной номер версии и дополнительный номер версии: например, для версии 2.1.300 пакета SDK для .NET Core можно указать пакет `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="57f3e-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="57f3e-144">В предыдущих версиях необходимо указать полную строку версии, например, для версии 2.1.200 пакета SDK для .NET Core потребовалось бы указать `dotnet-sdk-2.1.200`.</span><span class="sxs-lookup"><span data-stu-id="57f3e-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="57f3e-145">Для компьютеров, на которых установлена только среда выполнения без пакета SDK, используется имя пакета `dotnet-runtime-<version>` для среды выполнения .NET Core и `aspnetcore-runtime-<version>` для стека всей среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="57f3e-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="57f3e-146">Для .NET Core версий ниже 2.0 ведущее приложение не удалялось при удалении пакета SDK с помощью диспетчера пакетов.</span><span class="sxs-lookup"><span data-stu-id="57f3e-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="57f3e-147">При использовании `apt-get` применяется следующая команда:</span><span class="sxs-lookup"><span data-stu-id="57f3e-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="57f3e-148">Обратите внимание, что с `dotnet-host` не связана версия.</span><span class="sxs-lookup"><span data-stu-id="57f3e-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="57f3e-149">Если вы установили .NET Core из tar-архива, необходимо выполнить удаление вручную.</span><span class="sxs-lookup"><span data-stu-id="57f3e-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="57f3e-150">Необходимо отдельно удалить пакеты SDK и среды выполнения, удалив каталог, содержащий эту версию.</span><span class="sxs-lookup"><span data-stu-id="57f3e-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="57f3e-151">Например, чтобы удалить пакет SDK и среду выполнения версии 1.0.1, можно использовать следующие команды Bash:</span><span class="sxs-lookup"><span data-stu-id="57f3e-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="57f3e-152">Родительские каталоги для пакета SDK и среды выполнения указаны в выходных данных команд `dotnet --list-sdks` и `dotnet --list-runtimes`, как показано в приведенной выше таблице.</span><span class="sxs-lookup"><span data-stu-id="57f3e-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="57f3e-153">macOS</span><span class="sxs-lookup"><span data-stu-id="57f3e-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="57f3e-154">На компьютерах Mac необходимо отдельно удалить пакеты SDK и среды выполнения, удалив каталог, содержащий эту версию.</span><span class="sxs-lookup"><span data-stu-id="57f3e-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="57f3e-155">Например, чтобы удалить пакет SDK и среду выполнения версии 1.0.1, можно использовать следующие команды Bash:</span><span class="sxs-lookup"><span data-stu-id="57f3e-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="57f3e-156">Родительские каталоги для пакета SDK и среды выполнения указаны в выходных данных команд `dotnet --list-sdks` и `dotnet --list-runtimes`, как показано в приведенной выше таблице.</span><span class="sxs-lookup"><span data-stu-id="57f3e-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
