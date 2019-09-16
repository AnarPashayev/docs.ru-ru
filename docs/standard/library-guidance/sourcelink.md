---
title: Source Link и библиотеки .NET
description: Практические рекомендации по использованию Source Link для повышения эффективности отладки для библиотек .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928987"
---
# <a name="source-link"></a><span data-ttu-id="a0838-103">Source Link</span><span class="sxs-lookup"><span data-stu-id="a0838-103">Source Link</span></span>

<span data-ttu-id="a0838-104">Source Link — это технология, которая дает возможность разработчикам выполнять отладку исходного кода сборок .NET из NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0838-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="a0838-105">Source Link выполняется при создании пакета NuGet и внедряет метаданные системы управления версиями внутри сборки и пакета.</span><span class="sxs-lookup"><span data-stu-id="a0838-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="a0838-106">Разработчики, загрузившие пакет и включившие Source Link в Visual Studio, могут выполнить исходный код по шагам.</span><span class="sxs-lookup"><span data-stu-id="a0838-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="a0838-107">Source Link предоставляет метаданные системы управления версиями для создания эффективной среды отладки.</span><span class="sxs-lookup"><span data-stu-id="a0838-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="a0838-108">Демонстрация Source Link</span><span class="sxs-lookup"><span data-stu-id="a0838-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="a0838-109">Использование Source Link</span><span class="sxs-lookup"><span data-stu-id="a0838-109">Using Source Link</span></span>

<span data-ttu-id="a0838-110">Инструкции по использованию Source Link можно найти в репозитории GitHub [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="a0838-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="a0838-111">Вы можете использовать [обозреватель пакетов NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), чтобы убедиться, что метаданные Source Link успешно внедрены в пакет.</span><span class="sxs-lookup"><span data-stu-id="a0838-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="a0838-112">Проверьте наличие метаданных `Repository` с идентификатором комментария и убедитесь, что для каждой DLL-библиотеки целевого пакета есть PDB-файлы.</span><span class="sxs-lookup"><span data-stu-id="a0838-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="a0838-113">![Source Link в обозревателе пакетов NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link в обозревателе пакетов NuGet")</span><span class="sxs-lookup"><span data-stu-id="a0838-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="a0838-114">**✔️ РЕКОМЕНДУЕТСЯ** использовать Source Link для добавления метаданных системы управления версиями в сборки и пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="a0838-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="a0838-115">Вы можете дополнительно повысить эффективность отладки путем добавления атрибутов отладчика в типы.</span><span class="sxs-lookup"><span data-stu-id="a0838-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="a0838-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> может определять, как класс или поле будет отображаться в окнах переменных отладчика.</span><span class="sxs-lookup"><span data-stu-id="a0838-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="a0838-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> дает отладчику указание о сквозной обработке кода (вместо выполнения по шагам).</span><span class="sxs-lookup"><span data-stu-id="a0838-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="a0838-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> определяет, будет ли член отображаться в окнах переменных отладчика.</span><span class="sxs-lookup"><span data-stu-id="a0838-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="a0838-119">**✔️ ДОПУСТИМО.** Публикация файлов символов (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="a0838-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="a0838-120">Для повышения качества отладки библиотеки следует публиковать файлы символов, а также использовать ссылки на источник.</span><span class="sxs-lookup"><span data-stu-id="a0838-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="a0838-121">См. дополнительные сведения о [файлах и пакетах символов](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="a0838-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0838-122">[Назад](dependencies.md)
>[Вперед](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="a0838-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
