---
title: Каталог идентификаторов сред выполнения (RID) в .NET Core
description: Сведения об идентификаторах сред выполнения и их использовании в .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451737"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="3bb31-103">Каталог идентификаторов сред выполнения (RID) в .NET Core</span><span class="sxs-lookup"><span data-stu-id="3bb31-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="3bb31-104">RID — это сокращение от *Runtime IDentifier* (идентификатор среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="3bb31-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="3bb31-105">Идентификаторы RID служат для идентификации целевых платформ, на которых выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="3bb31-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="3bb31-106">Они используются пакетами .NET для представления ресурсов, специфичных для платформы, в пакетах NuGet.</span><span class="sxs-lookup"><span data-stu-id="3bb31-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="3bb31-107">Некоторые примеры идентификаторов RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` или `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="3bb31-108">Для пакетов с собственными зависимостями они указывают, на каких платформах можно восстановить пакет.</span><span class="sxs-lookup"><span data-stu-id="3bb31-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="3bb31-109">Один идентификатор RID можно задать в элементе `<RuntimeIdentifier>` вашего файла проекта.</span><span class="sxs-lookup"><span data-stu-id="3bb31-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="3bb31-110">Несколько идентификаторов RID можно определить в виде списка, разделенного точкой с запятой, в элементе `<RuntimeIdentifiers>` файла проекта.</span><span class="sxs-lookup"><span data-stu-id="3bb31-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="3bb31-111">Они также используются с помощью параметра `--runtime` со следующими [командами интерфейса командной строки .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="3bb31-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="3bb31-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3bb31-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="3bb31-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3bb31-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="3bb31-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3bb31-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="3bb31-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3bb31-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="3bb31-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3bb31-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="3bb31-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3bb31-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="3bb31-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3bb31-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="3bb31-119">Идентификаторы RID, представляющие отдельные операционные системы, обычно имеют следующий формат: `[os].[version]-[architecture]-[additional qualifiers]`, где:</span><span class="sxs-lookup"><span data-stu-id="3bb31-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="3bb31-120">`[os]` — это моникер платформы или операционной системы.</span><span class="sxs-lookup"><span data-stu-id="3bb31-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="3bb31-121">Например, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="3bb31-122">`[version]` — это версия операционной системы в виде номера, разделенного точкой (`.`).</span><span class="sxs-lookup"><span data-stu-id="3bb31-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="3bb31-123">Например, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="3bb31-124">Это **не должен быть** коммерческий номер версии, так как такой номер часто представляет отдельные версии операционной системы с различными контактными зонами API.</span><span class="sxs-lookup"><span data-stu-id="3bb31-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="3bb31-125">`[architecture]` — это архитектура процессора.</span><span class="sxs-lookup"><span data-stu-id="3bb31-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="3bb31-126">Например, `x86`, `x64`, `arm` или `arm64`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="3bb31-127">`[additional qualifiers]` дополнительно дифференцируют разные платформы.</span><span class="sxs-lookup"><span data-stu-id="3bb31-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="3bb31-128">Пример: `aot`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="3bb31-129">Схема RID</span><span class="sxs-lookup"><span data-stu-id="3bb31-129">RID graph</span></span>

<span data-ttu-id="3bb31-130">Схема RID или резервная схема среды выполнения — это список идентификаторов RID, которые совместимы друг с другом.</span><span class="sxs-lookup"><span data-stu-id="3bb31-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="3bb31-131">Идентификаторы RID определены в пакете [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="3bb31-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="3bb31-132">Список поддерживаемых идентификаторов RID и схема RID содержатся в файле [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json), который находится в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="3bb31-133">В этом файле можно увидеть, что все идентификаторы RID, кроме основного, содержат оператор `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="3bb31-134">Эти операторы указывают совместимые RID.</span><span class="sxs-lookup"><span data-stu-id="3bb31-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="3bb31-135">Когда NuGet восстанавливает пакеты, он пытается найти точное совпадение для указанной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3bb31-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="3bb31-136">Если его не удается найти, NuGet проходит схему до тех пор, пока не найдет ближайшую совместимую систему в соответствии со схемой RID.</span><span class="sxs-lookup"><span data-stu-id="3bb31-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="3bb31-137">Ниже приведена запись для идентификатора RID `osx.10.12-x64`:</span><span class="sxs-lookup"><span data-stu-id="3bb31-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="3bb31-138">Приведенный выше идентификатор RID указывает, что `osx.10.12-x64` импортирует `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="3bb31-139">Таким образом, когда NuGet восстанавливает пакеты, он пытается найти в пакете точное совпадение для `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="3bb31-140">Например, если NuGet не удается найти определенную среду выполнения, он может восстановить пакеты, которые определяют среды выполнения `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="3bb31-141">В следующем примере показана немного большая схема RID, которая также указана в файле *runtime.json*:</span><span class="sxs-lookup"><span data-stu-id="3bb31-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="3bb31-142">Все идентификаторы RID в конечном итоге сопоставляются с корневым идентификатором RID `any`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="3bb31-143">При работе с идентификаторами RID следует учитывать некоторые моменты:</span><span class="sxs-lookup"><span data-stu-id="3bb31-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="3bb31-144">RID являются **непрозрачными строками**, и их следует рассматривать как "черные ящики".</span><span class="sxs-lookup"><span data-stu-id="3bb31-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="3bb31-145">Не следует создавать идентификаторы RID программным способом.</span><span class="sxs-lookup"><span data-stu-id="3bb31-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="3bb31-146">Используйте только те идентификаторы RID, которые уже определены для платформы.</span><span class="sxs-lookup"><span data-stu-id="3bb31-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="3bb31-147">Идентификаторы RID должны указываться точно. Предположения недопустимы.</span><span class="sxs-lookup"><span data-stu-id="3bb31-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="3bb31-148">Использование идентификаторов RID</span><span class="sxs-lookup"><span data-stu-id="3bb31-148">Using RIDs</span></span>

<span data-ttu-id="3bb31-149">Для использования идентификаторов RID необходимо знать, какие идентификаторы RID существуют.</span><span class="sxs-lookup"><span data-stu-id="3bb31-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="3bb31-150">В платформу регулярно добавляются новые идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="3bb31-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="3bb31-151">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="3bb31-152">SDK для .NET Core 2.0 представляет концепцию переносных идентификаторов RID.</span><span class="sxs-lookup"><span data-stu-id="3bb31-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="3bb31-153">Это новые значения, добавленные в граф RID, которые не привязаны к конкретной версии или дистрибутиву ОС и рекомендуются для использования с .NET Core 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="3bb31-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="3bb31-154">Они особенно удобны во время работы с несколькими дистрибутивами Linux, так как большинство идентификаторов RID дистрибутивов сопоставлено с переносными идентификаторами RID.</span><span class="sxs-lookup"><span data-stu-id="3bb31-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="3bb31-155">Ниже представлена небольшая выборка наиболее распространенных RID, используемых для каждой ОС.</span><span class="sxs-lookup"><span data-stu-id="3bb31-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="3bb31-156">Идентификаторы RID для Windows</span><span class="sxs-lookup"><span data-stu-id="3bb31-156">Windows RIDs</span></span>

<span data-ttu-id="3bb31-157">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="3bb31-157">Only common values are listed.</span></span> <span data-ttu-id="3bb31-158">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="3bb31-159">Переносные (.NET Core 2.0 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="3bb31-160">Windows 7 или Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3bb31-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="3bb31-161">Windows 8.1 или Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3bb31-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="3bb31-162">Windows 10 или Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3bb31-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="3bb31-163">Дополнительные сведения см. в статье [Зависимости и требования для .NET Core](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="3bb31-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="3bb31-164">Идентификаторы RID для Linux</span><span class="sxs-lookup"><span data-stu-id="3bb31-164">Linux RIDs</span></span>

<span data-ttu-id="3bb31-165">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="3bb31-165">Only common values are listed.</span></span> <span data-ttu-id="3bb31-166">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="3bb31-167">Устройства с дистрибутивами, не перечисленными ниже, могут работать с одним из переносных идентификаторов RID.</span><span class="sxs-lookup"><span data-stu-id="3bb31-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="3bb31-168">Например, для устройств Raspberry Pi с дистрибутивом Linux, которого нет в списке, можно использовать `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="3bb31-169">Переносные (.NET Core 2.0 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="3bb31-170">`linux-x64` (большинство дистрибутивов для компьютеров, например CentOS, Debian, Fedora, Ubuntu и производные от них);</span><span class="sxs-lookup"><span data-stu-id="3bb31-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="3bb31-171">`linux-musl-x64` (упрощенные дистрибутивы, которые используют [musl](https://wiki.musl-libc.org/projects-using-musl.html), например Alpine Linux);</span><span class="sxs-lookup"><span data-stu-id="3bb31-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="3bb31-172">`linux-arm` (дистрибутивы Linux, которые работают на архитектуре ARM, например Raspberry Pi).</span><span class="sxs-lookup"><span data-stu-id="3bb31-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="3bb31-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3bb31-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="3bb31-174">`rhel-x64` (заменен на `linux-x64` для RHEL новее версии 6);</span><span class="sxs-lookup"><span data-stu-id="3bb31-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="3bb31-175">`rhel.6-x64` (.NET Core 2.0 или более поздние версии)</span><span class="sxs-lookup"><span data-stu-id="3bb31-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="3bb31-176">Tizen (.NET Core 2.0 или более поздние версии)</span><span class="sxs-lookup"><span data-stu-id="3bb31-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="3bb31-177">Дополнительные сведения см. в статье [Зависимости и требования для .NET Core](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="3bb31-177">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="3bb31-178">Относительные идентификаторы macOS</span><span class="sxs-lookup"><span data-stu-id="3bb31-178">macOS RIDs</span></span>

<span data-ttu-id="3bb31-179">Относительные идентификаторы macOS используют старую фирменную символику "OSX".</span><span class="sxs-lookup"><span data-stu-id="3bb31-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="3bb31-180">Перечислены только распространенные значения.</span><span class="sxs-lookup"><span data-stu-id="3bb31-180">Only common values are listed.</span></span> <span data-ttu-id="3bb31-181">Последнюю и полную версию см. в файле [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) в репозитории `dotnet/runtime`.</span><span class="sxs-lookup"><span data-stu-id="3bb31-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="3bb31-182">Переносные (.NET Core 2.0 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="3bb31-183">`osx-x64` (минимальная версия — macOS 10.12 Sierra).</span><span class="sxs-lookup"><span data-stu-id="3bb31-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="3bb31-184">macOS 10.10 Yosemite:</span><span class="sxs-lookup"><span data-stu-id="3bb31-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="3bb31-185">macOS 10.11 El Capitan:</span><span class="sxs-lookup"><span data-stu-id="3bb31-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="3bb31-186">macOS 10.12 Sierra (.NET Core 1.1 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="3bb31-187">macOS 10.13 High Sierra (.NET Core 1.1 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="3bb31-188">macOS 10.14 Mojave (.NET Core 1.1 или более поздние версии):</span><span class="sxs-lookup"><span data-stu-id="3bb31-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="3bb31-189">Дополнительные сведения см. в статье [Зависимости и требования для .NET Core](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="3bb31-189">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="3bb31-190">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3bb31-190">See also</span></span>

- [<span data-ttu-id="3bb31-191">Идентификаторы среды выполнения</span><span class="sxs-lookup"><span data-stu-id="3bb31-191">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
