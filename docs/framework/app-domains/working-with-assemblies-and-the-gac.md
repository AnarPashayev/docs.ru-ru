---
title: Работа со сборками и глобальным кэшем сборок
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f45f40cd66c63e660b9091c726533dcfe8db086
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971584"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="152ed-102">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="152ed-103">Если необходимо обеспечить возможность совместного использования сборки в нескольких приложениях, то ее можно поместить в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="152ed-104">Этот кэш кода уровня компьютера присутствует на любом компьютере, где установлена среда CLR.</span><span class="sxs-lookup"><span data-stu-id="152ed-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="152ed-105">В глобальном кэше сборок сохраняются сборки, специально предназначенные для совместного использования на компьютере несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="152ed-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="152ed-106">Для установки в глобальном кэше сборка должна иметь строгое имя.</span><span class="sxs-lookup"><span data-stu-id="152ed-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="152ed-107">Имя сборки, установленной в глобальном кэше сборок, должно совпадать с именем файла (без учета расширения имени файла).</span><span class="sxs-lookup"><span data-stu-id="152ed-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="152ed-108">К примеру, файл сборки с именем myAssembly должен иметь имя myAssembly.exe или myAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="152ed-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="152ed-109">Прибегать к совместному использованию сборок путем их установки в глобальном кэше сборок следует только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="152ed-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="152ed-110">Как правило, зависимости между сборками следует сохранять закрытыми, а сами сборки нужно размещать в папке приложения, если они не предназначены для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="152ed-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="152ed-111">Кроме того, установка сборок в глобальном кэше сборок для обеспечения доступа к ним с помощью COM-взаимодействия или из неуправляемого кода не является обязательной.</span><span class="sxs-lookup"><span data-stu-id="152ed-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="152ed-112">Существует несколько причин для установки сборки в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="152ed-113">Общее расположение.</span><span class="sxs-lookup"><span data-stu-id="152ed-113">Shared location.</span></span>  
  
     <span data-ttu-id="152ed-114">Используемые несколькими приложениями сборки можно располагать в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="152ed-115">Например, если все приложения используют сборку, расположенную в глобальном кэше сборок, то в файл Machine.config можно добавить оператор политики выбора версий, который перенаправляет ссылки на эту сборку.</span><span class="sxs-lookup"><span data-stu-id="152ed-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="152ed-116">Безопасность файлов.</span><span class="sxs-lookup"><span data-stu-id="152ed-116">File security.</span></span>  
  
     <span data-ttu-id="152ed-117">Администраторы часто защищают папку systemroot с помощью списка управления доступом, определяющего права на запись и выполнение.</span><span class="sxs-lookup"><span data-stu-id="152ed-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="152ed-118">Так как глобальный кэш сборок размещается в корневом каталоге системы, он наследует список управления доступом этого каталога.</span><span class="sxs-lookup"><span data-stu-id="152ed-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="152ed-119">Рекомендуется разрешать удаление файлов из глобального кэша сборок только пользователям, имеющим права доступа администратора.</span><span class="sxs-lookup"><span data-stu-id="152ed-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="152ed-120">Управление параллельными версиями.</span><span class="sxs-lookup"><span data-stu-id="152ed-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="152ed-121">В глобальном кэше сборок может храниться несколько сборок, имеющих одинаковые имена, но различные сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="152ed-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="152ed-122">Дополнительное место для поиска.</span><span class="sxs-lookup"><span data-stu-id="152ed-122">Additional search location.</span></span>  
  
     <span data-ttu-id="152ed-123">Перед проверкой или использованием сведений о базе кода в файле конфигурации среда CLR ищет в глобальном кэше сборки, соответствующие запросу.</span><span class="sxs-lookup"><span data-stu-id="152ed-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="152ed-124">Обратите внимание, что существуют сценарии, в которых установка сборки в глобальный кэш сборок явно не требуется.</span><span class="sxs-lookup"><span data-stu-id="152ed-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="152ed-125">Если одна из составляющих приложение сборок помещается в глобальный кэш сборок, то после этого нельзя будет скопировать или установить приложение с помощью команды XCOPY путем копирования каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="152ed-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="152ed-126">В этом случае также требуется переместить сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="152ed-127">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="152ed-127">In This Section</span></span>  
 [<span data-ttu-id="152ed-128">Практическое руководство. Установка сборки в глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
 <span data-ttu-id="152ed-129">Описание способов установки сборки в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="152ed-130">Практическое руководство. Просмотр содержимого глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="152ed-131">Описание того, как использовать [средство глобального кэша сборок (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) для просмотра содержимого глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="152ed-132">Практическое руководство. Удаление сборки из глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="152ed-133">Описание того, как использовать [средство глобального кэша сборок (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) для удаления сборки из глобального кэша сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="152ed-134">Использование обслуживаемых компонентов с глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="152ed-135">Содержит сведения о том, почему обслуживаемые компоненты (управляемые компоненты COM+) следует помещать в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="152ed-136">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="152ed-136">Related Sections</span></span>  
 [<span data-ttu-id="152ed-137">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-137">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
 <span data-ttu-id="152ed-138">Содержит общие сведения о создании сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="152ed-139">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="152ed-140">Содержит общие сведения о глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="152ed-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="152ed-141">Практическое руководство. Просмотр содержимого сборки</span><span class="sxs-lookup"><span data-stu-id="152ed-141">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
 <span data-ttu-id="152ed-142">Описание того, как использовать [программу Ildasm.exe (дизассемблер IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) для просмотра данных MSIL в сборке.</span><span class="sxs-lookup"><span data-stu-id="152ed-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="152ed-143">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="152ed-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="152ed-144">Описание того, как среда CLR находит и загружает сборки, составляющие приложение.</span><span class="sxs-lookup"><span data-stu-id="152ed-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="152ed-145">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="152ed-145">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
 <span data-ttu-id="152ed-146">Описывает сборки, "кирпичики", с помощью которых создаются управляемые приложения.</span><span class="sxs-lookup"><span data-stu-id="152ed-146">Describes assemblies, the building blocks of managed applications.</span></span>
