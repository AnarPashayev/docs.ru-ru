---
title: URI типа "pack" в WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 59c72d9ae12a014a8c47cb3b2852b337b173446c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580623"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="ab1fe-102">URI типа "pack" в WPF</span><span class="sxs-lookup"><span data-stu-id="ab1fe-102">Pack URIs in WPF</span></span>

<span data-ttu-id="ab1fe-103">В Windows Presentation Foundation (WPF) универсальные идентификаторы ресурсов (URI) используются для идентификации и загрузки файлов различными способами, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-103">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="ab1fe-104">Указание [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], отображаемых при первом запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="ab1fe-105">Загрузка изображений.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-105">Loading images.</span></span>

- <span data-ttu-id="ab1fe-106">Переход по страницам.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-106">Navigating to pages.</span></span>

- <span data-ttu-id="ab1fe-107">Загрузка неисполняемых файлов данных.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-107">Loading non-executable data files.</span></span>

<span data-ttu-id="ab1fe-108">Кроме того, универсальные коды ресурса (URI) можно использовать для обнаружения и загрузки файлов из различных расположений, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-108">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="ab1fe-109">Текущая сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-109">The current assembly.</span></span>

- <span data-ttu-id="ab1fe-110">Указанная ссылками сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-110">A referenced assembly.</span></span>

- <span data-ttu-id="ab1fe-111">Расположение, связанное со сборкой.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="ab1fe-112">Исходный узел приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-112">The application's site of origin.</span></span>

<span data-ttu-id="ab1fe-113">Чтобы обеспечить единообразный механизм идентификации и загрузки этих типов файлов из этих расположений, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] использует расширяемость *схемы URI*типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="ab1fe-114">В этом разделе приводятся общие сведения о схеме, описывается создание URI типа "Pack" для различных сценариев, обсуждаются абсолютные и относительные URI и разрешение URI, прежде чем показано, как использовать URI типа "Pack" из разметки и кода.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-114">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="ab1fe-115">Схема URI типа "pack"</span><span class="sxs-lookup"><span data-stu-id="ab1fe-115">The Pack URI Scheme</span></span>

<span data-ttu-id="ab1fe-116">Схема URI типа "Pack" используется спецификацией [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC), которая описывает модель для Организации и идентификации содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-116">The pack URI scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="ab1fe-117">Ключевыми элементами этой модели являются пакеты и части, где *пакет* является логическим контейнером для одной или нескольких логических *частей*.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="ab1fe-118">Эта структура показана на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-118">The following figure illustrates this concept.</span></span>

![Схема пакета и частей](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="ab1fe-120">Для определения частей в спецификации OPC используется расширяемость RFC 2396 (универсальные идентификаторы ресурсов (URI): универсальный синтаксис) для определения схемы URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="ab1fe-121">Схема, заданная с помощью URI, определяется его префиксом. HTTP, FTP и файлы — это хорошо известные примеры.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-121">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="ab1fe-122">В схеме универсального кода ресурса (URI) типа "Pack" в качестве схемы содержится два компонента: Authority и Path.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-122">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="ab1fe-123">Ниже приведен формат URI типа pack.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-123">The following is the format for a pack URI.</span></span>

<span data-ttu-id="ab1fe-124">*путь* /*центра* Pack://</span><span class="sxs-lookup"><span data-stu-id="ab1fe-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="ab1fe-125">*Центр* определяет тип пакета, который содержится в части, а *путь* указывает расположение части в пакете.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="ab1fe-126">Эта концепция показана на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-126">This concept is illustrated by the following figure:</span></span>

![Отношение между пакетом, сертификацией и путем](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="ab1fe-128">Пакеты и элементы аналогичны приложениям и файлам. Приложение (пакет) может содержать один или несколько файлов (элементов), в том числе:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="ab1fe-129">Файлы ресурсов, скомпилированные в локальную сборку.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="ab1fe-130">Файлы ресурсов, скомпилированные в сборку, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="ab1fe-131">Файлы ресурсов, скомпилированные в ссылающуюся сборку.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="ab1fe-132">Файлы содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-132">Content files.</span></span>

- <span data-ttu-id="ab1fe-133">Файлы исходного узла.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-133">Site of origin files.</span></span>

<span data-ttu-id="ab1fe-134">Для доступа к этим типам файлов [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] поддерживает два органа: application:///и siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="ab1fe-135">Центр application:/// определяет файлы данных приложения, известные во время компиляции, включая файлы ресурсов и файлы содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="ab1fe-136">Центр siteoforigin:/// определяет файлы исходного узла.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="ab1fe-137">На следующем рисунке показана область каждого центра.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-137">The scope of each authority is shown in the following figure.</span></span>

![Схема URI типа “pack”](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="ab1fe-139">Компонент центра URI типа "Pack" является внедренным универсальным кодом ресурса (URI), который указывает на пакет и должен соответствовать RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-139">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="ab1fe-140">Кроме того, символ "/" необходимо заменить символом ",", и необходимо обособлять escape-символами такие зарезервированные символы, как "%" и "?".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="ab1fe-141">Подробные сведения см. в OPC.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-141">See the OPC for details.</span></span>

<span data-ttu-id="ab1fe-142">В следующих разделах объясняется, как создать URI типа "Pack" с помощью этих двух центров в сочетании с соответствующими путями для определения файлов ресурсов, содержимого и исходного узла.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-142">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="ab1fe-143">URI типа "pack" для файла ресурсов</span><span class="sxs-lookup"><span data-stu-id="ab1fe-143">Resource File Pack URIs</span></span>

<span data-ttu-id="ab1fe-144">Файлы ресурсов настраиваются как MSBuild `Resource` элементы и компилируются в сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="ab1fe-145">WPF поддерживает создание URI типа "Pack", которые можно использовать для обнаружения файлов ресурсов, которые либо компилируются в локальную сборку, либо компилируются в сборку, на которую ссылается локальная сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="ab1fe-146">Файл ресурсов локальной сборки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-146">Local Assembly Resource File</span></span>

<span data-ttu-id="ab1fe-147">URI типа "Pack" для файла ресурсов, компилируемого в локальную сборку, использует следующие полномочия и путь:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-147">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="ab1fe-148">**Центр**: application:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="ab1fe-149">**Путь**: имя файла ресурсов, включая его путь относительно корневой папки проекта локальной сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="ab1fe-150">В следующем примере показан URI типа "Pack" для файла ресурсов [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится в корне папки проекта локальной сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-150">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="ab1fe-151">В следующем примере показан URI типа "Pack" для файла ресурсов [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится во вложенной папке проекта локальной сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="ab1fe-152">Файл ресурсов указанной ссылками сборки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="ab1fe-153">URI типа "Pack" для файла ресурсов, компилируемого в указанную сборку, использует следующие полномочия и путь:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-153">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="ab1fe-154">**Центр**: application:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="ab1fe-155">**Путь**: имя файла ресурсов, который компилируется в указанную ссылками сборку.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="ab1fe-156">Путь должен соответствовать следующему формату:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="ab1fe-157">*Ассемблишортнаме*{ *; Версия*] { *; PublicKey*]; компонент или*путь*</span><span class="sxs-lookup"><span data-stu-id="ab1fe-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="ab1fe-158">**AssemblyShortName** — краткое имя для указанной ссылками сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="ab1fe-159">**;Version** [необязательно] — версия указанной ссылками сборки, которая содержит файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="ab1fe-160">Используется при загрузке двух или более указанных ссылками сборок с одинаковым кратким именем.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="ab1fe-161">**;PublicKey** [необязательно]: открытый ключ, который использовался для подписи указанной ссылками сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="ab1fe-162">Используется при загрузке двух или более указанных ссылками сборок с одинаковым кратким именем.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="ab1fe-163">**;component**: указывает, что на упоминаемую сборку ссылается локальная сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="ab1fe-164">**/Path**: имя файла ресурсов, включая его путь относительно корневой папки проекта указанной ссылками сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="ab1fe-165">В следующем примере показан URI типа "Pack" для файла ресурсов [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится в корне папки проекта указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-165">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="ab1fe-166">В следующем примере показан URI типа "Pack" для файла ресурсов [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится во вложенной папке проекта указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="ab1fe-167">В следующем примере показан URI типа "Pack" для файла ресурсов [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится в корневой папке указанной в папке проекта сборки для конкретной версии.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="ab1fe-168">Обратите внимание, что синтаксис URI типа "Pack" для файлов ресурсов сборки, на которые указывают ссылки, можно использовать только с центром application:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-168">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="ab1fe-169">Например, в [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] не поддерживается следующее.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="ab1fe-170">URI типа "pack" для файла содержимого</span><span class="sxs-lookup"><span data-stu-id="ab1fe-170">Content File Pack URIs</span></span>

<span data-ttu-id="ab1fe-171">В URI типа "Pack" для файла содержимого используются следующие полномочия и путь:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-171">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="ab1fe-172">**Центр**: application:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="ab1fe-173">**Путь**: имя файла содержимого, включая его путь относительно расположения файловой системы основной исполняемой сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="ab1fe-174">В следующем примере показан URI типа "Pack" для [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ного файла содержимого, расположенного в той же папке, что и исполняемая сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-174">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="ab1fe-175">В следующем примере показан URI типа "Pack" для файла содержимого [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], который находится во вложенной папке, относящейся к исполняемой сборке приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="ab1fe-176">Переход к файлам HTML-содержимого невозможен.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="ab1fe-177">Схема URI поддерживает только навигацию по HTML-файлам, расположенным на исходном узле.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-177">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="ab1fe-178">URI типа "pack" исходного узла</span><span class="sxs-lookup"><span data-stu-id="ab1fe-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="ab1fe-179">URI типа "Pack" для файла исходного узла использует следующие полномочия и путь:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-179">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="ab1fe-180">**Центр**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="ab1fe-181">**Путь**: имя файла исходного узла, включая его путь относительно расположения, из которого была запущена исполняемая сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="ab1fe-182">В следующем примере показан URI типа Pack для файла исходного узла [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], хранящегося в расположении, из которого запускается исполняемая сборка.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-182">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="ab1fe-183">В следующем примере показан URI типа Pack для файла исходного узла [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], хранящегося в подпапке, которая относится к расположению, из которого запускается исполняемая сборка приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="ab1fe-184">Файлы подкачки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-184">Page Files</span></span>

<span data-ttu-id="ab1fe-185">Файлы XAML, настроенные как MSBuild `Page` элементы, компилируются в сборки так же, как и файлы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="ab1fe-186">Следовательно, элементы `Page` MSBuild можно определить с помощью URI типа "Pack" для файлов ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="ab1fe-187">Типы [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] файлов, которые обычно настраиваются как элементы `Page` MSBuild, имеют в качестве корневого элемента один из следующих элементов:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="ab1fe-188">Абсолютные и относительные URI типа Pack</span><span class="sxs-lookup"><span data-stu-id="ab1fe-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="ab1fe-189">Полный URI типа "Pack" включает схему, центр и путь, и считается абсолютным URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-189">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="ab1fe-190">В качестве упрощения для разработчиков [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] элементы обычно позволяют задавать соответствующие атрибуты с помощью относительного URI типа "Pack", который включает только путь.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="ab1fe-191">Например, рассмотрим следующий абсолютный пакет URI для файла ресурсов в локальной сборке.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-191">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="ab1fe-192">Относительный URI типа "Pack", ссылающийся на этот файл ресурсов, будет следующим.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-192">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="ab1fe-193">Так как файлы исходного узла не связаны со сборками, они могут называться только абсолютными URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="ab1fe-194">По умолчанию относительный URI типа "Pack" рассматривается относительно расположения разметки или кода, содержащего ссылку.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-194">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="ab1fe-195">Однако если используется начальная обратная косая черта, ссылка на URI-адрес относительных пакетов будет рассматриваться относительно корня приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-195">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="ab1fe-196">Например, рассмотрим следующую структуру проекта.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="ab1fe-197">Если параметр ". XAML" содержит URI, который ссылается на *корневой*\SubFolder\Page2.XAML, ссылка может использовать следующий относительный URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-197">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="ab1fe-198">Если параметр ". XAML" содержит URI, который ссылается на *корневой*\Page2.XAML, ссылка может использовать следующий относительный URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-198">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="ab1fe-199">Разрешение URI типа "pack"</span><span class="sxs-lookup"><span data-stu-id="ab1fe-199">Pack URI Resolution</span></span>

<span data-ttu-id="ab1fe-200">Формат URI типа "Pack" позволяет одинаково различать URI типа "Pack" для различных типов файлов.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-200">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="ab1fe-201">Например, рассмотрим следующий абсолютный URI типа pack.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-201">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="ab1fe-202">Этот абсолютный URI типа "Pack" может ссылаться либо на файл ресурсов в локальной сборке, либо на файл содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-202">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="ab1fe-203">То же справедливо для следующего относительного URI.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-203">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="ab1fe-204">Чтобы определить тип файла, на который ссылается URI типа "Pack", [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] разрешает URI для файлов ресурсов в локальных сборках и файлах содержимого, используя следующие эвристики:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-204">In order to determine the type of file that a pack URI refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="ab1fe-205">Проверяет метаданные сборки для атрибута <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, соответствующего URI типа pack.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="ab1fe-206">Если найден атрибут <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, путь URI типа "Pack" ссылается на файл содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="ab1fe-207">Если атрибут <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> не найден, проверяют файлы ресурсов, компилируемые в локальную сборку.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="ab1fe-208">Если найден файл ресурсов, соответствующий пути URI типа "Pack", путь к URI типа "Pack" ссылается на файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-208">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="ab1fe-209">Если ресурс не найден, <xref:System.Uri>, созданный внутренним образом, является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="ab1fe-210">Разрешение URI не применяется для URI, которые ссылаются на следующие:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-210">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="ab1fe-211">Файлы содержимого в сборках, на которые имеются ссылки: эти типы файлов не поддерживаются [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab1fe-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="ab1fe-212">Внедренные файлы в упоминаемых сборках: URI, которые их определяют, являются уникальными, так как включают имя сборки, на которую указывает ссылка, и суффикс `;component`.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-212">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="ab1fe-213">Файлы исходного узла: универсальные коды ресурса (URI) являются уникальными, так как они являются единственными файлами, которые можно идентифицировать с помощью URI типа "Pack", содержащих центр siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-213">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="ab1fe-214">Одно упрощение, позволяющее разрешающему URI типа "Pack", заключается в том, что код может быть несколько независимым от расположения файлов ресурсов и содержимого.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-214">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="ab1fe-215">Например, если в локальной сборке есть файл ресурсов, который перестраивается как файл содержимого, URI типа "Pack" для ресурса остается прежним, так же как и код, использующий URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="ab1fe-216">Программирование с использованием URI типа "pack"</span><span class="sxs-lookup"><span data-stu-id="ab1fe-216">Programming with Pack URIs</span></span>

<span data-ttu-id="ab1fe-217">Многие классы [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] реализуют свойства, которые можно задать с помощью URI типа Pack, в том числе:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="ab1fe-218">Эти свойства можно задать из разметки и кода.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="ab1fe-219">В этом разделе демонстрируются основные конструкции для разметки и кода, а также приводятся примеры наиболее распространенных сценариев.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="ab1fe-220">Использование URI типа "pack" в разметке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="ab1fe-221">URI типа "Pack" указывается в разметке путем задания элемента атрибута с URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-221">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="ab1fe-222">Пример:</span><span class="sxs-lookup"><span data-stu-id="ab1fe-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="ab1fe-223">В таблице 1 показаны различные абсолютные URI типа "Pack", которые можно указать в разметке.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-223">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="ab1fe-224">Таблица 1. Абсолютные URI типа "pack" в разметке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="ab1fe-225">Файл</span><span class="sxs-lookup"><span data-stu-id="ab1fe-225">File</span></span>|<span data-ttu-id="ab1fe-226">Абсолютный URI типа Pack</span><span class="sxs-lookup"><span data-stu-id="ab1fe-226">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ab1fe-227">Файл ресурсов — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-228">Файл ресурсов в подпапке — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-229">Файл ресурсов — указанная ссылками сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-230">Файл ресурсов в подпапке указанной ссылками сборки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-231">Файл ресурсов в указанной ссылками сборке с несколькими версиями</span><span class="sxs-lookup"><span data-stu-id="ab1fe-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-232">Файл содержимого</span><span class="sxs-lookup"><span data-stu-id="ab1fe-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="ab1fe-233">Файл содержимого в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="ab1fe-234">Файл исходного узла</span><span class="sxs-lookup"><span data-stu-id="ab1fe-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="ab1fe-235">Файл исходного узла в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="ab1fe-236">В таблице 2 показаны различные относительные URI типа "Pack", которые можно указать в разметке.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-236">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="ab1fe-237">Таблица 2. Относительные URI типа "pack" в разметке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="ab1fe-238">Файл</span><span class="sxs-lookup"><span data-stu-id="ab1fe-238">File</span></span>|<span data-ttu-id="ab1fe-239">Относительный URI типа Pack</span><span class="sxs-lookup"><span data-stu-id="ab1fe-239">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ab1fe-240">Файл ресурсов в локальной сборке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-241">Файл ресурсов в подпапке — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-242">Файл ресурсов в указанной ссылками сборке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-243">Файл ресурсов в подпапке указанной ссылками сборки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ab1fe-244">Файл содержимого</span><span class="sxs-lookup"><span data-stu-id="ab1fe-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="ab1fe-245">Файл содержимого в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="ab1fe-246">Использование URI типа "pack" в коде</span><span class="sxs-lookup"><span data-stu-id="ab1fe-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="ab1fe-247">URI типа "Pack" указывается в коде путем создания экземпляра класса <xref:System.Uri> и передачи URI типа "Pack" в качестве параметра в конструктор.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-247">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="ab1fe-248">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="ab1fe-249">По умолчанию класс <xref:System.Uri> считает URI типа "Pack" абсолютным.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-249">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="ab1fe-250">Следовательно, исключение возникает, когда экземпляр класса <xref:System.Uri> создается с помощью относительного URI типа "Pack".</span><span class="sxs-lookup"><span data-stu-id="ab1fe-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="ab1fe-251">К счастью, перегрузка <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> конструктора класса <xref:System.Uri> принимает параметр типа <xref:System.UriKind>, чтобы можно было указать, является ли универсальный код ресурса (URI) абсолютным или относительным.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="ab1fe-252">Необходимо указать только <xref:System.UriKind.Absolute> или <xref:System.UriKind.Relative>, если вы уверены, что предоставленный URI типа "Pack" является одним или другим.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="ab1fe-253">Если неизвестно, какой тип URI используется, например, когда пользователь вводит URI типа "Pack" во время выполнения, используйте вместо этого <xref:System.UriKind.RelativeOrAbsolute>.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-253">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="ab1fe-254">В таблице 3 показаны различные относительные URI типа "Pack", которые можно указать в коде с помощью <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-254">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ab1fe-255">Таблица 3. Абсолютные URI типа "pack" в коде</span><span class="sxs-lookup"><span data-stu-id="ab1fe-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="ab1fe-256">Файл</span><span class="sxs-lookup"><span data-stu-id="ab1fe-256">File</span></span>|<span data-ttu-id="ab1fe-257">Абсолютный URI типа Pack</span><span class="sxs-lookup"><span data-stu-id="ab1fe-257">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ab1fe-258">Файл ресурсов — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-259">Файл ресурсов в подпапке — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-260">Файл ресурсов — указанная ссылками сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-261">Файл ресурсов в подпапке указанной ссылками сборки</span><span class="sxs-lookup"><span data-stu-id="ab1fe-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-262">Файл ресурсов в указанной ссылками сборке с несколькими версиями</span><span class="sxs-lookup"><span data-stu-id="ab1fe-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-263">Файл содержимого</span><span class="sxs-lookup"><span data-stu-id="ab1fe-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-264">Файл содержимого в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-265">Файл исходного узла</span><span class="sxs-lookup"><span data-stu-id="ab1fe-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ab1fe-266">Файл исходного узла в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="ab1fe-267">В таблице 4 показаны различные относительные URI типа "Pack", которые можно указать в коде с помощью <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-267">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ab1fe-268">Таблица 4. Относительные URI типа "pack" в коде</span><span class="sxs-lookup"><span data-stu-id="ab1fe-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="ab1fe-269">Файл</span><span class="sxs-lookup"><span data-stu-id="ab1fe-269">File</span></span>|<span data-ttu-id="ab1fe-270">Относительный URI типа Pack</span><span class="sxs-lookup"><span data-stu-id="ab1fe-270">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ab1fe-271">Файл ресурсов — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ab1fe-272">Файл ресурсов в подпапке — локальная сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ab1fe-273">Файл ресурсов — указанная ссылками сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ab1fe-274">Файл ресурсов в подпапке — указанная ссылками сборка</span><span class="sxs-lookup"><span data-stu-id="ab1fe-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ab1fe-275">Файл содержимого</span><span class="sxs-lookup"><span data-stu-id="ab1fe-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ab1fe-276">Файл содержимого в подпапке</span><span class="sxs-lookup"><span data-stu-id="ab1fe-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="ab1fe-277">Типичные сценарии URI типа "pack"</span><span class="sxs-lookup"><span data-stu-id="ab1fe-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="ab1fe-278">В предыдущих разделах обсуждалось создание URI типа "Pack" для указания файлов ресурсов, содержимого и исходного узла.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-278">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="ab1fe-279">В [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] эти конструкции используются различными способами, и в следующих разделах рассматриваются некоторые распространенные способы использования.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="ab1fe-280">Указание пользовательского интерфейса для отображения при запуске приложения</span><span class="sxs-lookup"><span data-stu-id="ab1fe-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="ab1fe-281"><xref:System.Windows.Application.StartupUri%2A> указывает первый [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], отображаемый при запуске приложения [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab1fe-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="ab1fe-282">Для автономных приложений [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] может быть окном, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="ab1fe-283">Автономные приложения и [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] также могут указывать страницу в качестве начального пользовательского интерфейса, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="ab1fe-284">Если приложение является автономным и страница указана с помощью <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] открывает <xref:System.Windows.Navigation.NavigationWindow> для размещения страницы.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="ab1fe-285">Для [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] страница отображается в браузере узла.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="ab1fe-286">Переход на страницу</span><span class="sxs-lookup"><span data-stu-id="ab1fe-286">Navigating to a Page</span></span>

<span data-ttu-id="ab1fe-287">В следующем примере показано, как перейти на какую-либо страницу.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="ab1fe-288">Дополнительные сведения о различных способах перехода по [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] см. в разделе [Общие сведения о навигации](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ab1fe-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="ab1fe-289">Указание значка окна</span><span class="sxs-lookup"><span data-stu-id="ab1fe-289">Specifying a Window Icon</span></span>

<span data-ttu-id="ab1fe-290">В следующем примере показано использование URI для указания значка окна.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="ab1fe-291">Для получения дополнительной информации см. <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="ab1fe-292">Загрузка файлов изображения, аудио и видео файлов</span><span class="sxs-lookup"><span data-stu-id="ab1fe-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="ab1fe-293">позволяет приложениям использовать разнообразные типы мультимедиа, которые можно определить и загрузить с помощью URI типа "Pack", как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="ab1fe-294">Дополнительные сведения о работе с мультимедийным содержимым см. в разделе [графика и мультимедиа](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab1fe-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="ab1fe-295">Загрузка словаря ресурсов с исходного узла</span><span class="sxs-lookup"><span data-stu-id="ab1fe-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="ab1fe-296">Словари ресурсов (<xref:System.Windows.ResourceDictionary>) можно использовать для поддержки тем приложений.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="ab1fe-297">Одним из способов создания тем и управления ими является создание нескольких тем в качестве словарей ресурсов, расположенных в исходном узле приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="ab1fe-298">Это позволяет добавлять и обновлять темы без повторной компиляции и развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="ab1fe-299">Эти словари ресурсов можно определить и загрузить с помощью URI типа "Pack", как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ab1fe-299">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="ab1fe-300">Общие сведения о темах в [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] см. в разделе [Стилизация и создание шаблонов](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="ab1fe-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab1fe-301">См. также</span><span class="sxs-lookup"><span data-stu-id="ab1fe-301">See also</span></span>

- [<span data-ttu-id="ab1fe-302">Файлы ресурсов, контента и данных WPF-приложения</span><span class="sxs-lookup"><span data-stu-id="ab1fe-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
