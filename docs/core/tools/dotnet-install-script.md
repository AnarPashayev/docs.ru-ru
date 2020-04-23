---
title: Скрипты dotnet-install
description: Сведения о скриптах dotnet-install, которые служат для установки пакета SDK для .NET Core и общей среды выполнения
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463679"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="a30c6-103">Справка по скриптам dotnet-install</span><span class="sxs-lookup"><span data-stu-id="a30c6-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="a30c6-104">name</span><span class="sxs-lookup"><span data-stu-id="a30c6-104">Name</span></span>

<span data-ttu-id="a30c6-105">`dotnet-install.ps1` | `dotnet-install.sh` — скрипт, используемый для установки общей среды выполнения и пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a30c6-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a30c6-106">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="a30c6-106">Synopsis</span></span>

<span data-ttu-id="a30c6-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="a30c6-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="a30c6-108">Linux или macOS</span><span class="sxs-lookup"><span data-stu-id="a30c6-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="a30c6-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a30c6-109">Description</span></span>

<span data-ttu-id="a30c6-110">Скрипты `dotnet-install` используются для установки пакета SDK для .NET Core без прав администратора. Этот пакет включает общую среду выполнения и .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="a30c6-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="a30c6-111">Мы рекомендуем использовать стабильную версию скриптов.</span><span class="sxs-lookup"><span data-stu-id="a30c6-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="a30c6-112">Bash (Linux или macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="a30c6-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="a30c6-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="a30c6-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="a30c6-114">Их основное назначение — помощь в сценариях автоматизации и при установках без прав администратора.</span><span class="sxs-lookup"><span data-stu-id="a30c6-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="a30c6-115">Имеются два скрипта: один для PowerShell (работает в Windows), а второй — bash-скрипт, который работает в Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="a30c6-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="a30c6-116">Оба скрипта выполняют одни и те же функции.</span><span class="sxs-lookup"><span data-stu-id="a30c6-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="a30c6-117">Так как bash-скрипт также считывает параметры PowerShell, их можно использовать с этим скриптом в системах Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="a30c6-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="a30c6-118">Скрипты установки скачивают файл ZIP или TAR из места сборки CLI, а затем осуществляют установку в расположении по умолчанию или расположении, заданном параметром `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="a30c6-119">По умолчанию скрипты установки скачивают и устанавливают пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="a30c6-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="a30c6-120">Если вы хотите получить только общую среду выполнения, укажите аргумент `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="a30c6-121">По умолчанию скрипт добавляет место установки в переменную $PATH для текущего сеанса.</span><span class="sxs-lookup"><span data-stu-id="a30c6-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="a30c6-122">Переопределите это поведение по умолчанию, указав аргумент `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="a30c6-123">Перед запуском скрипта установите все необходимые [зависимости](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="a30c6-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="a30c6-124">Вы можете установить конкретную версию с помощью аргумента `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="a30c6-125">Версию следует указывать в виде трехкомпонентного номера (например, `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="a30c6-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="a30c6-126">Если она не указана, используется версия `latest`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="a30c6-127">Параметры</span><span class="sxs-lookup"><span data-stu-id="a30c6-127">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="a30c6-128">Архитектура устанавливаемых двоичных файлов .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a30c6-128">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="a30c6-129">Допустимые значения: `<auto>`, `amd64`, `x64`, `x86`, `arm64` и `arm`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-129">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="a30c6-130">Значение по умолчанию — `<auto>`, представляющее текущую используемую архитектуру ОС.</span><span class="sxs-lookup"><span data-stu-id="a30c6-130">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="a30c6-131">Указывает URL-адрес для веб-канала Azure этого установщика.</span><span class="sxs-lookup"><span data-stu-id="a30c6-131">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="a30c6-132">Изменять это значение не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="a30c6-132">We recommended that you don't change this value.</span></span> <span data-ttu-id="a30c6-133">Значение по умолчанию — `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-133">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="a30c6-134">Указывает исходный канал для установки.</span><span class="sxs-lookup"><span data-stu-id="a30c6-134">Specifies the source channel for the installation.</span></span> <span data-ttu-id="a30c6-135">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="a30c6-135">The possible values are:</span></span>

  - <span data-ttu-id="a30c6-136">`Current` — самый последний выпуск.</span><span class="sxs-lookup"><span data-stu-id="a30c6-136">`Current` - Most current release.</span></span>
  - <span data-ttu-id="a30c6-137">`LTS` — канал долгосрочной поддержки (самый последний поддерживаемый выпуск).</span><span class="sxs-lookup"><span data-stu-id="a30c6-137">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="a30c6-138">Версия из двух частей в формате X.Y, который представляет конкретный выпуск (например, `2.1` или `3.0`).</span><span class="sxs-lookup"><span data-stu-id="a30c6-138">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="a30c6-139">Имя ветви, например `release/3.1.1xx` или `master` (для ночных выпусков).</span><span class="sxs-lookup"><span data-stu-id="a30c6-139">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="a30c6-140">Используйте этот параметр для установки версии из канала предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="a30c6-140">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="a30c6-141">Используйте имя канала, указанное в разделе [Установщики и двоичные файлы](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="a30c6-141">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="a30c6-142">Значение по умолчанию — `LTS`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-142">The default value is `LTS`.</span></span> <span data-ttu-id="a30c6-143">Дополнительные сведения о каналах поддержки .NET см. на странице о [политике поддержки .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="a30c6-143">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="a30c6-144">Если задано, скрипт не будет выполнять установку.</span><span class="sxs-lookup"><span data-stu-id="a30c6-144">If set, the script won't perform the installation.</span></span> <span data-ttu-id="a30c6-145">Вместо этого отобразится командная строка для согласованной установки запрошенной в настоящее время версии .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="a30c6-145">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="a30c6-146">Например, если указать версию `latest`, он отображает ссылку для определенной версии, чтобы эту команду можно было детерминировано использовать в скрипте сборки.</span><span class="sxs-lookup"><span data-stu-id="a30c6-146">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="a30c6-147">Кроме того, он отображает расположение двоичного файла, если вы хотите выполнить скачивание или установку самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a30c6-147">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="a30c6-148">Используется в качестве строки запроса для добавления в веб-канал Azure.</span><span class="sxs-lookup"><span data-stu-id="a30c6-148">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="a30c6-149">Позволяет изменять URL-адрес для использования учетных записей хранилища BLOB-объектов, не являющихся общедоступными.</span><span class="sxs-lookup"><span data-stu-id="a30c6-149">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="a30c6-150">Выводит справку для скрипта.</span><span class="sxs-lookup"><span data-stu-id="a30c6-150">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="a30c6-151">Указывает путь установки.</span><span class="sxs-lookup"><span data-stu-id="a30c6-151">Specifies the installation path.</span></span> <span data-ttu-id="a30c6-152">Если такого пути нет, создается каталог.</span><span class="sxs-lookup"><span data-stu-id="a30c6-152">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="a30c6-153">Значение по умолчанию — *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="a30c6-153">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="a30c6-154">Двоичные файлы помещаются непосредственно в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="a30c6-154">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="a30c6-155">Указывает путь к файлу [global.json](global-json.md), который будет использоваться для определения версии пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="a30c6-155">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="a30c6-156">В файле *global.json* должно быть значение для `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-156">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="a30c6-157">Отключает загрузку из [сети доставки содержимого Microsoft Azure (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) и напрямую использует некэшированный веб-канал.</span><span class="sxs-lookup"><span data-stu-id="a30c6-157">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="a30c6-158">Если значение задано, папка установки не экспортируется в путь текущего сеанса.</span><span class="sxs-lookup"><span data-stu-id="a30c6-158">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="a30c6-159">По умолчанию скрипт изменит значение PATH, благодаря чему .NET Core CLI становится доступным сразу после установки.</span><span class="sxs-lookup"><span data-stu-id="a30c6-159">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="a30c6-160">Если значение задано, установщик использует прокси-сервер для выполнения веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="a30c6-160">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="a30c6-161">(Допустимо только для Windows.)</span><span class="sxs-lookup"><span data-stu-id="a30c6-161">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="a30c6-162">Если задано, установщик использует учетные данные текущего пользователя при использовании адреса прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="a30c6-162">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="a30c6-163">(Допустимо только для Windows.)</span><span class="sxs-lookup"><span data-stu-id="a30c6-163">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="a30c6-164">Устанавливается только общая среда выполнения, а не весь пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="a30c6-164">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="a30c6-165">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="a30c6-165">The possible values are:</span></span>

  - <span data-ttu-id="a30c6-166">`dotnet` — общая среда выполнения `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-166">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a30c6-167">`aspnetcore` — общая среда выполнения `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-167">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a30c6-168">`windowsdesktop` — общая среда выполнения `Microsoft.WindowsDesktop.App`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-168">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="a30c6-169">Указывает [идентификатор среды выполнения](../rid-catalog.md), для которого устанавливаются средства.</span><span class="sxs-lookup"><span data-stu-id="a30c6-169">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="a30c6-170">Используйте значение `linux-x64` для переносимых файлов Linux.</span><span class="sxs-lookup"><span data-stu-id="a30c6-170">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="a30c6-171">(Допустимо только для Linux и macOS.)</span><span class="sxs-lookup"><span data-stu-id="a30c6-171">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="a30c6-172">Этот параметр является устаревшим и может быть удален в будущей версии скрипта.</span><span class="sxs-lookup"><span data-stu-id="a30c6-172">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="a30c6-173">Вместо этого рекомендуется использовать параметр `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-173">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="a30c6-174">Устанавливаются только двоичные файлы общей среды выполнения; в противном случае устанавливается весь пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="a30c6-174">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="a30c6-175">Этот параметр эквивалентен указанию `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-175">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="a30c6-176">Пропускает установку файлов без версии, таких как *dotnet.exe*, если они уже существуют.</span><span class="sxs-lookup"><span data-stu-id="a30c6-176">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="a30c6-177">Позволяет изменять URL-адрес некэшированного веб-канала, используемого этим установщиком.</span><span class="sxs-lookup"><span data-stu-id="a30c6-177">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="a30c6-178">Изменять это значение не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="a30c6-178">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="a30c6-179">Отображает сведения о диагностике.</span><span class="sxs-lookup"><span data-stu-id="a30c6-179">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="a30c6-180">Представляет определенную версию сборки.</span><span class="sxs-lookup"><span data-stu-id="a30c6-180">Represents a specific build version.</span></span> <span data-ttu-id="a30c6-181">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="a30c6-181">The possible values are:</span></span>

  - <span data-ttu-id="a30c6-182">`latest` — последняя сборка в канале (используется с параметром `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="a30c6-182">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="a30c6-183">`coherent` — последняя согласованная сборка в канале. Использует последние сочетания стабильных пакетов. (Используется с параметрами `-Channel` имени ветви.)</span><span class="sxs-lookup"><span data-stu-id="a30c6-183">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="a30c6-184">Версия из трех частей в формате X.Y.Z, который представляет определенную версию сборки. Заменяет параметр `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-184">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="a30c6-185">Например, `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-185">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="a30c6-186">Если не указано, `-Version` по умолчанию принимает значение `latest`.</span><span class="sxs-lookup"><span data-stu-id="a30c6-186">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="a30c6-187">Примеры</span><span class="sxs-lookup"><span data-stu-id="a30c6-187">Examples</span></span>

- <span data-ttu-id="a30c6-188">Установка последней версии с долгосрочной поддержкой (LTS) в расположение по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="a30c6-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="a30c6-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="a30c6-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="a30c6-190">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="a30c6-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="a30c6-191">Установка последней версии из канала версии 3.1 в указанное расположение</span><span class="sxs-lookup"><span data-stu-id="a30c6-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="a30c6-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="a30c6-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="a30c6-193">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="a30c6-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="a30c6-194">Установка общей среды выполнения версии 3.0.0</span><span class="sxs-lookup"><span data-stu-id="a30c6-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="a30c6-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="a30c6-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="a30c6-196">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="a30c6-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="a30c6-197">Получите и установите скрипт версии 2.1.2 за корпоративным прокси-сервером (только для Windows):</span><span class="sxs-lookup"><span data-stu-id="a30c6-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="a30c6-198">Получите скрипт и установите однострочные примеры для интерфейса командной строки .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a30c6-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="a30c6-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="a30c6-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="a30c6-200">Mac OS и Linux:</span><span class="sxs-lookup"><span data-stu-id="a30c6-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="a30c6-201">См. также</span><span class="sxs-lookup"><span data-stu-id="a30c6-201">See also</span></span>

- [<span data-ttu-id="a30c6-202">Выпуски .NET Core</span><span class="sxs-lookup"><span data-stu-id="a30c6-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="a30c6-203">Архив загрузки пакета SDK и среды выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="a30c6-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
