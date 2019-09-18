---
title: Расположение сборки
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972657"
---
# <a name="assembly-location"></a><span data-ttu-id="58116-102">Расположение сборки</span><span class="sxs-lookup"><span data-stu-id="58116-102">Assembly location</span></span>
<span data-ttu-id="58116-103">От места расположения сборки зависит, сможет ли среда CLR найти сборку по ссылке на нее. Это расположение также определяет возможность совместного использования сборки вместе с другими сборками.</span><span class="sxs-lookup"><span data-stu-id="58116-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="58116-104">Для развертывания сборки можно использовать следующие расположения.</span><span class="sxs-lookup"><span data-stu-id="58116-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="58116-105">Каталог приложения или его подкаталоги</span><span class="sxs-lookup"><span data-stu-id="58116-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="58116-106">Это наиболее часто используемое место развертывания сборок.</span><span class="sxs-lookup"><span data-stu-id="58116-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="58116-107">Структура подкаталогов корневого каталога приложения может зависеть от языка или региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="58116-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="58116-108">Если в атрибутах сборки также задан язык и региональные параметры, то она должна располагаться в подкаталоге каталога приложения, название которого соответствует этому языку и региональным параметрам.</span><span class="sxs-lookup"><span data-stu-id="58116-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="58116-109">Глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="58116-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="58116-110">Это кэш кода уровня компьютера, который имеется на любом компьютере с установленной средой CLR.</span><span class="sxs-lookup"><span data-stu-id="58116-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="58116-111">В большинстве случаев при необходимости совместного использования сборки в нескольких приложениях ее следует расположить в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="58116-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="58116-112">На HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="58116-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="58116-113">Сборка, развернутая на HTTP-сервере, должна иметь строгое имя; в разделе базы кода файла конфигурации приложения должно присутствовать указание на сборку.</span><span class="sxs-lookup"><span data-stu-id="58116-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58116-114">См. также</span><span class="sxs-lookup"><span data-stu-id="58116-114">See also</span></span>

- [<span data-ttu-id="58116-115">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="58116-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="58116-116">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="58116-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="58116-117">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="58116-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="58116-118">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="58116-118">Program with assemblies</span></span>](program.md)
