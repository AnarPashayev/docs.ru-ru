---
title: Практическое руководство. установку сборки в глобальный кэш сборок
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155567"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="5c452-102">Практическое руководство. установку сборки в глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="5c452-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="5c452-103">В глобальном кэше сборок сохраняются сборки, которые могут использоваться несколькими приложениями.</span><span class="sxs-lookup"><span data-stu-id="5c452-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="5c452-104">Установите сборку в [глобальный кэш сборок](gac.md) с одним из следующих компонентов:</span><span class="sxs-lookup"><span data-stu-id="5c452-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="5c452-105">Установщик Windows</span><span class="sxs-lookup"><span data-stu-id="5c452-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="5c452-106">Средство глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="5c452-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="5c452-107">В глобальный кэш сборок можно установить только сборки со строгими именами.</span><span class="sxs-lookup"><span data-stu-id="5c452-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="5c452-108">Дополнительные сведения о создании сборки со строгим именем см. в разделе [Практическое руководство. Подписание сборки со строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="5c452-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="5c452-109">Установщик Windows</span><span class="sxs-lookup"><span data-stu-id="5c452-109">Windows Installer</span></span>

<span data-ttu-id="5c452-110">[Установщик Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache) — средство установки Windows, которое рекомендуется использовать для добавления сборок в GAC.</span><span class="sxs-lookup"><span data-stu-id="5c452-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="5c452-111">Установщик Windows предоставляет возможность подсчета ссылок на сборки в GAC и другие дополнительные возможности.</span><span class="sxs-lookup"><span data-stu-id="5c452-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="5c452-112">Создать пакет установщика для установщика Windows можно с помощью [расширения Wix Toolset для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="5c452-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="5c452-113">Средство глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="5c452-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="5c452-114">[Служебную программу глобального кэша сборок .NET (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) можно использовать для добавления сборок в глобальный кэш сборок и для просмотра содержимого указанного кэша.</span><span class="sxs-lookup"><span data-stu-id="5c452-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5c452-115">*Gacutil.exe* предназначен только для разработки.</span><span class="sxs-lookup"><span data-stu-id="5c452-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="5c452-116">Не используйте его для установки рабочих сборок в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="5c452-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="5c452-117">Синтаксис для использования *gacutil.exe* для установки сборки в глобальном кэше сборок выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5c452-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="5c452-118">В этой команде *\<имя сборки>* представляет собой имя сборки, устанавливаемой в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="5c452-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="5c452-119">Если *gacutil.exe* не находится в системном пути, используйте [командную строку разработчика для VS *\<версия>* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5c452-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="5c452-120">В следующем примере выполняется установка сборки с именем файла *hello.dll* в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="5c452-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="5c452-121">В предыдущих версиях .NET Framework расширение оболочки Windows *Shfusion.dll* позволяло устанавливать сборки, перетаскивая их в проводнике.</span><span class="sxs-lookup"><span data-stu-id="5c452-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="5c452-122">Начиная с версии .NET Framework 4 расширение оболочки *Shfusion.dll* является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="5c452-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c452-123">См. также</span><span class="sxs-lookup"><span data-stu-id="5c452-123">See also</span></span>

- [<span data-ttu-id="5c452-124">Работа со сборками и глобальным кэшем сборок</span><span class="sxs-lookup"><span data-stu-id="5c452-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="5c452-125">Практическое руководство. Удаление сборки из глобального кэша сборок</span><span class="sxs-lookup"><span data-stu-id="5c452-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="5c452-126">Gacutil.exe (программа глобального кэша сборок)</span><span class="sxs-lookup"><span data-stu-id="5c452-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="5c452-127">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="5c452-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
