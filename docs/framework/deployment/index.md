---
title: Развертывание .NET Framework и приложений
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7380556e13e17e26ffb2f8c5fbbc7136a1fb5e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481331"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="e8a83-102">Развертывание .NET Framework и приложений</span><span class="sxs-lookup"><span data-stu-id="e8a83-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="e8a83-103">Эта статья поможет приступить к развертыванию платформы .NET Framework с приложением.</span><span class="sxs-lookup"><span data-stu-id="e8a83-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="e8a83-104">Большая часть информации предназначена для разработчиков, изготовителей оборудования и администраторов предприятия.</span><span class="sxs-lookup"><span data-stu-id="e8a83-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="e8a83-105">Пользователям, которые хотят установить .NET Framework на своих компьютерах, следует прочитать статью [Установка .NET Framework](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="e8a83-106">Основные ресурсы, посвященные развертыванию</span><span class="sxs-lookup"><span data-stu-id="e8a83-106">Key Deployment Resources</span></span>

<span data-ttu-id="e8a83-107">Для получения дополнительных сведений о развертывании и обслуживании .NET Framework воспользуйтесь приведенными ниже ссылками на другие разделы MSDN.</span><span class="sxs-lookup"><span data-stu-id="e8a83-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="e8a83-108">**Установка и развертывание**</span><span class="sxs-lookup"><span data-stu-id="e8a83-108">**Setup and deployment**</span></span>

- <span data-ttu-id="e8a83-109">Общие сведения об установщиках и развертывании:</span><span class="sxs-lookup"><span data-stu-id="e8a83-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="e8a83-110">Тип установщика:</span><span class="sxs-lookup"><span data-stu-id="e8a83-110">Installer options:</span></span>

    - <span data-ttu-id="e8a83-111">[веб-установщик](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable);</span><span class="sxs-lookup"><span data-stu-id="e8a83-111">[Web installer](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)</span></span>

    - <span data-ttu-id="e8a83-112">[автономный установщик](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable).</span><span class="sxs-lookup"><span data-stu-id="e8a83-112">[Offline installer](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)</span></span>

  - <span data-ttu-id="e8a83-113">Режимы установки:</span><span class="sxs-lookup"><span data-stu-id="e8a83-113">Installation modes:</span></span>

    - <span data-ttu-id="e8a83-114">[автоматическая установка](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom);</span><span class="sxs-lookup"><span data-stu-id="e8a83-114">[Silent installation](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)</span></span>

    - <span data-ttu-id="e8a83-115">[отображение пользовательского интерфейса](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default).</span><span class="sxs-lookup"><span data-stu-id="e8a83-115">[Displaying a UI](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)</span></span>

  - [<span data-ttu-id="e8a83-116">Уменьшение числа перезагрузок при установке платформы .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e8a83-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)

  - [<span data-ttu-id="e8a83-117">Устранение неполадок с заблокированными установками и удалениями .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e8a83-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="e8a83-118">Развертывание .NET Framework с клиентским приложением (для разработчиков):</span><span class="sxs-lookup"><span data-stu-id="e8a83-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="e8a83-119">[Использование InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) в проекте установки и развертывания.</span><span class="sxs-lookup"><span data-stu-id="e8a83-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - <span data-ttu-id="e8a83-120">[Использование приложения Visual Studio ClickOnce](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment).</span><span class="sxs-lookup"><span data-stu-id="e8a83-120">[Using a Visual Studio ClickOnce application](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)</span></span>

  - <span data-ttu-id="e8a83-121">[Создание пакета установки WiX](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix).</span><span class="sxs-lookup"><span data-stu-id="e8a83-121">[Creating a WiX installation package](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)</span></span>

  - <span data-ttu-id="e8a83-122">[Использование настраиваемого установщика](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining).</span><span class="sxs-lookup"><span data-stu-id="e8a83-122">[Using a custom installer](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)</span></span>

  - <span data-ttu-id="e8a83-123">[Дополнительные сведения](../../../docs/framework/deployment/deployment-guide-for-developers.md) для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="e8a83-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="e8a83-124">Развертывание .NET Framework (для изготовителей оборудования и администраторов):</span><span class="sxs-lookup"><span data-stu-id="e8a83-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - <span data-ttu-id="e8a83-125">[Комплект средств для развертывания и оценки Windows (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976).</span><span class="sxs-lookup"><span data-stu-id="e8a83-125">[Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)</span></span>

  - <span data-ttu-id="e8a83-126">[Руководство администратора](../../../docs/framework/deployment/guide-for-administrators.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-126">[Administrator's guide](../../../docs/framework/deployment/guide-for-administrators.md)</span></span>

<span data-ttu-id="e8a83-127">**Обслуживание**.</span><span class="sxs-lookup"><span data-stu-id="e8a83-127">**Servicing**</span></span>

- <span data-ttu-id="e8a83-128">Общие сведения см. в [блоге по .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977).</span><span class="sxs-lookup"><span data-stu-id="e8a83-128">For general information, see the [.NET Framework blog](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>

- <span data-ttu-id="e8a83-129">[Обнаружение версий](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-129">[Detecting versions](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)</span></span>

- <span data-ttu-id="e8a83-130">[Обнаружение обновлений и пакетов обновления](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-130">[Detecting service packs and updates](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)</span></span>

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="e8a83-131">Возможности, упрощающие развертывание</span><span class="sxs-lookup"><span data-stu-id="e8a83-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="e8a83-132">Платформа .NET Framework включает ряд функций, которые упрощают развертывание приложений.</span><span class="sxs-lookup"><span data-stu-id="e8a83-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="e8a83-133">Изолированные приложения.</span><span class="sxs-lookup"><span data-stu-id="e8a83-133">No-impact applications.</span></span>

     <span data-ttu-id="e8a83-134">Эта функция обеспечивает изоляцию приложений и исключает конфликты библиотек DLL.</span><span class="sxs-lookup"><span data-stu-id="e8a83-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="e8a83-135">По умолчанию компоненты не влияют на другие приложения.</span><span class="sxs-lookup"><span data-stu-id="e8a83-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="e8a83-136">Частные компоненты по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e8a83-136">Private components by default.</span></span>

     <span data-ttu-id="e8a83-137">По умолчанию компоненты развертываются в каталоге приложения и доступны только содержащему их приложению.</span><span class="sxs-lookup"><span data-stu-id="e8a83-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="e8a83-138">Контролируемое совместное использование кода.</span><span class="sxs-lookup"><span data-stu-id="e8a83-138">Controlled code sharing.</span></span>

     <span data-ttu-id="e8a83-139">Для совместного использования кода необходимо явным образом предоставить к нему общий доступ — по умолчанию он не предоставляется.</span><span class="sxs-lookup"><span data-stu-id="e8a83-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="e8a83-140">Управление параллельными версиями.</span><span class="sxs-lookup"><span data-stu-id="e8a83-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="e8a83-141">Одновременно могут сосуществовать несколько версий компонента или приложения. Вы можете выбрать используемые версии, а среда CLR применит политику управления версиями.</span><span class="sxs-lookup"><span data-stu-id="e8a83-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="e8a83-142">Развертывание и репликация XCOPY.</span><span class="sxs-lookup"><span data-stu-id="e8a83-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="e8a83-143">Самоописываемые и автономные компоненты и приложения можно развертывать без записей в реестре и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="e8a83-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="e8a83-144">Оперативные обновления.</span><span class="sxs-lookup"><span data-stu-id="e8a83-144">On-the-fly updates.</span></span>

     <span data-ttu-id="e8a83-145">Администраторы могут использовать узлы, например ASP.NET, для обновления библиотек DLL программы даже на удаленных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="e8a83-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="e8a83-146">Интеграция с установщиком Windows.</span><span class="sxs-lookup"><span data-stu-id="e8a83-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="e8a83-147">При развертывании приложения доступны объявление, публикация, восстановление и установка по требованию.</span><span class="sxs-lookup"><span data-stu-id="e8a83-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="e8a83-148">Корпоративное развертывание.</span><span class="sxs-lookup"><span data-stu-id="e8a83-148">Enterprise deployment.</span></span>

     <span data-ttu-id="e8a83-149">Эта функция упрощает распространение программного обеспечения, в том числе с помощью Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e8a83-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="e8a83-150">Скачивание и кэширование.</span><span class="sxs-lookup"><span data-stu-id="e8a83-150">Downloading and caching.</span></span>

     <span data-ttu-id="e8a83-151">Добавочное скачивание позволяет сократить объем скачиваемых файлов. Кроме того, можно изолировать компоненты для использования только приложением, что позволяет снизить влияние развертывания на среду.</span><span class="sxs-lookup"><span data-stu-id="e8a83-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="e8a83-152">Частично доверенный код.</span><span class="sxs-lookup"><span data-stu-id="e8a83-152">Partially trusted code.</span></span>

     <span data-ttu-id="e8a83-153">Идентификация производится на основе кода, а не на основе пользователя. Не выводятся диалоговые окна сертификата.</span><span class="sxs-lookup"><span data-stu-id="e8a83-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="e8a83-154">Упаковка и распространение приложений .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e8a83-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="e8a83-155">Некоторые сведения о создании пакетов и развертывании для платформы .NET Framework приводятся в других разделах документации.</span><span class="sxs-lookup"><span data-stu-id="e8a83-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="e8a83-156">В этих разделах содержатся сведения о самоописываемых блоках, называемых [сборками](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), для которых не требуются записи в реестре, [сборках со строгими именами](../../../docs/framework/app-domains/strong-named-assemblies.md), которые гарантируют уникальность имен и предотвращают их подмену, и об [управлении версиями сборок](../../../docs/framework/app-domains/assembly-versioning.md), которое решает многие проблемы, связанные с конфликтами библиотек DLL.</span><span class="sxs-lookup"><span data-stu-id="e8a83-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="e8a83-157">В разделах ниже содержатся сведения об упаковке и распространении приложений .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8a83-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="e8a83-158">Упаковка</span><span class="sxs-lookup"><span data-stu-id="e8a83-158">Packaging</span></span>

<span data-ttu-id="e8a83-159">Платформа .NET Framework предоставляет следующие способы упаковки приложений:</span><span class="sxs-lookup"><span data-stu-id="e8a83-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="e8a83-160">В виде отдельной сборки или коллекции сборок.</span><span class="sxs-lookup"><span data-stu-id="e8a83-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="e8a83-161">В этом варианте DLL- или EXE-файлы используются в том виде, в котором они были созданы.</span><span class="sxs-lookup"><span data-stu-id="e8a83-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="e8a83-162">В виде CAB-файлов.</span><span class="sxs-lookup"><span data-stu-id="e8a83-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="e8a83-163">В этом варианте файлы сжимаются в CAB-файлы, чтобы распространение или скачивание занимало меньше времени.</span><span class="sxs-lookup"><span data-stu-id="e8a83-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="e8a83-164">В виде пакета установщика Windows или в других форматах установщика.</span><span class="sxs-lookup"><span data-stu-id="e8a83-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="e8a83-165">В этом случае вы создаете MSI-файлы для использования с установщиком Windows или пакет приложения для использования с другими установщиками.</span><span class="sxs-lookup"><span data-stu-id="e8a83-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="e8a83-166">Распределение</span><span class="sxs-lookup"><span data-stu-id="e8a83-166">Distribution</span></span>

<span data-ttu-id="e8a83-167">Платформа .NET Framework предоставляет следующие варианты распространения приложений.</span><span class="sxs-lookup"><span data-stu-id="e8a83-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="e8a83-168">С помощью XCOPY или FTP.</span><span class="sxs-lookup"><span data-stu-id="e8a83-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="e8a83-169">Так как приложения среды CLR являются самоописываемыми и не требуют записей в реестре, вы можете использовать XCOPY или FTP, чтобы просто скопировать приложение в соответствующий каталог.</span><span class="sxs-lookup"><span data-stu-id="e8a83-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="e8a83-170">Затем приложение можно будет запустить из этого каталога.</span><span class="sxs-lookup"><span data-stu-id="e8a83-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="e8a83-171">С помощью скачивания кода.</span><span class="sxs-lookup"><span data-stu-id="e8a83-171">Use code download.</span></span>

     <span data-ttu-id="e8a83-172">Если приложение распространяется через Интернет или корпоративную интрасеть, можно просто скачать код на компьютер и запустить его.</span><span class="sxs-lookup"><span data-stu-id="e8a83-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="e8a83-173">С помощью программы установки, например установщика Windows версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="e8a83-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="e8a83-174">Установщик Windows версии 2.0 позволяет устанавливать, восстанавливать и удалять сборки .NET Framework в глобальном кэше сборок и в личных каталогах.</span><span class="sxs-lookup"><span data-stu-id="e8a83-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="e8a83-175">Расположение установки</span><span class="sxs-lookup"><span data-stu-id="e8a83-175">Installation Location</span></span>

<span data-ttu-id="e8a83-176">Сведения о том, как выбрать место для развертывания сборок приложения таким образом, чтобы их могла найти среда выполнения, см. в статье [Обнаружение сборок в среде выполнения](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="e8a83-177">На выбор способа развертывания приложения могут также влиять соображения безопасности.</span><span class="sxs-lookup"><span data-stu-id="e8a83-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="e8a83-178">Разрешения безопасности предоставляются управляемому коду в соответствии с его расположением.</span><span class="sxs-lookup"><span data-stu-id="e8a83-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="e8a83-179">Развертывание приложения или компонента в расположении, где они получают низкий уровень доверия, например в Интернете, ограничивает возможности приложения или компонента.</span><span class="sxs-lookup"><span data-stu-id="e8a83-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="e8a83-180">Дополнительные сведения о развертывании и аспектах безопасности см. в статье [Основы управления доступом для кода](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e8a83-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="e8a83-181">См. также</span><span class="sxs-lookup"><span data-stu-id="e8a83-181">Related Topics</span></span>

|<span data-ttu-id="e8a83-182">Заголовок</span><span class="sxs-lookup"><span data-stu-id="e8a83-182">Title</span></span>|<span data-ttu-id="e8a83-183">Описание</span><span class="sxs-lookup"><span data-stu-id="e8a83-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="e8a83-184">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="e8a83-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="e8a83-185">Описывается то, как среда CLR определяет, какую сборку следует использовать для выполнения запроса привязки.</span><span class="sxs-lookup"><span data-stu-id="e8a83-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="e8a83-186">Рекомендации для загрузки сборок</span><span class="sxs-lookup"><span data-stu-id="e8a83-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="e8a83-187">Описывается, как избежать проблем с идентификацией типов, которые могут привести к возникновению исключений <xref:System.InvalidCastException> и <xref:System.MissingMethodException> и других ошибок.</span><span class="sxs-lookup"><span data-stu-id="e8a83-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="e8a83-188">Уменьшение числа перезагрузок при установке платформы .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e8a83-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="e8a83-189">Описывается диспетчер перезапуска, который по возможности предотвращает перезагрузки, и его преимущества для приложений, устанавливающих платформу .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8a83-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="e8a83-190">Руководство по развертыванию для администраторов</span><span class="sxs-lookup"><span data-stu-id="e8a83-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="e8a83-191">Описывается развертывание платформы .NET Framework и ее системных зависимостей в сети с помощью System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="e8a83-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|
|[<span data-ttu-id="e8a83-192">Руководство по развертыванию для разработчиков</span><span class="sxs-lookup"><span data-stu-id="e8a83-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="e8a83-193">Описываются способы установки .NET Framework на компьютеры пользователей вместе с приложениями.</span><span class="sxs-lookup"><span data-stu-id="e8a83-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="e8a83-194">Развертывание приложений, служб и компонентов</span><span class="sxs-lookup"><span data-stu-id="e8a83-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="e8a83-195">Рассматриваются варианты развертывания в Visual Studio, включая инструкции по публикации приложения с помощью технологии ClickOnce и установщика Windows.</span><span class="sxs-lookup"><span data-stu-id="e8a83-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="e8a83-196">Публикация приложений ClickOnce</span><span class="sxs-lookup"><span data-stu-id="e8a83-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="e8a83-197">Описывается, как упаковать приложение Windows Forms и развернуть его на клиентских компьютерах в сети с помощью технологии ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="e8a83-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="e8a83-198">Упаковка и развертывание ресурсов</span><span class="sxs-lookup"><span data-stu-id="e8a83-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="e8a83-199">Описывается модель "звезда", которую платформа .NET Framework использует для упаковки и развертывания ресурсов; рассматриваются соглашения об именовании ресурсов, процесс перехода на резервные ресурсы и альтернативные способы упаковки.</span><span class="sxs-lookup"><span data-stu-id="e8a83-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="e8a83-200">Развертывание приложения взаимодействия</span><span class="sxs-lookup"><span data-stu-id="e8a83-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="e8a83-201">Описывается поставка и установка приложений взаимодействия, которые обычно включают клиентскую сборку .NET Framework, одну или несколько сборок взаимодействия (представляющих различные библиотеки типов COM) и один или несколько зарегистрированных COM-компонентов.</span><span class="sxs-lookup"><span data-stu-id="e8a83-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="e8a83-202">Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e8a83-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="e8a83-203">Описывается автоматический запуск и отслеживание процесса установки .NET Framework с выводом собственного представления хода выполнения установки.</span><span class="sxs-lookup"><span data-stu-id="e8a83-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e8a83-204">См. также</span><span class="sxs-lookup"><span data-stu-id="e8a83-204">See also</span></span>

- [<span data-ttu-id="e8a83-205">Руководство по разработке</span><span class="sxs-lookup"><span data-stu-id="e8a83-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
