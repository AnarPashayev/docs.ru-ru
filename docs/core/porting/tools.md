---
title: Инструменты для переноса в .NET Core
description: Дополнительные сведения о некоторых инструментах, которые можно использовать для переноса в .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 64bad7600d8e17ada83d4bd8bc56762fd1789f43
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989133"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="1a82b-103">Инструменты для переноса в .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a82b-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="1a82b-104">Инструменты в этой статье помогут вам при переносе:</span><span class="sxs-lookup"><span data-stu-id="1a82b-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="1a82b-105">[Анализатор переносимости .NET](../../standard/analyzers/portability-analyzer.md) — цепочка инструментов, создающих отчеты о переносимости кода между .NET Framework и .NET Core:</span><span class="sxs-lookup"><span data-stu-id="1a82b-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="1a82b-106">как [программа командной строки](https://github.com/Microsoft/dotnet-apiport/releases);</span><span class="sxs-lookup"><span data-stu-id="1a82b-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="1a82b-107">как [расширение Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="1a82b-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="1a82b-108">[Анализатор API .NET](../../standard/analyzers/api-analyzer.md) — анализатор на основе Roslyn выявляет риски совместимости для API на языке C# на разных платформах, а также отслеживает вызовы устаревших API.</span><span class="sxs-lookup"><span data-stu-id="1a82b-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="1a82b-109">Кроме того, можно попытаться перенести более мелкие решения или отдельные проекты в формат файла проекта .NET Core с помощью средства [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).</span><span class="sxs-lookup"><span data-stu-id="1a82b-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="1a82b-110">CsprojToVs2017 — это стороннее средство.</span><span class="sxs-lookup"><span data-stu-id="1a82b-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="1a82b-111">Нет никакой гарантии, что оно будет поддерживать все проекты. Кроме того, оно может вызвать незначительные изменения в ожидаемом поведении.</span><span class="sxs-lookup"><span data-stu-id="1a82b-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="1a82b-112">CsprojToVs2017 следует использовать в качестве _начальной точки_, которая автоматизирует соответствующие основные процессы.</span><span class="sxs-lookup"><span data-stu-id="1a82b-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="1a82b-113">Это решение не может гарантировать перенос форматов файлов проекта.</span><span class="sxs-lookup"><span data-stu-id="1a82b-113">It is not a guaranteed solution to migrating project file formats.</span></span>
