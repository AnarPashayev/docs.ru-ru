---
title: Программирование с использованием доменов приложений и сборок
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675355"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="dc170-102">Программирование с использованием доменов приложений и сборок</span><span class="sxs-lookup"><span data-stu-id="dc170-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="dc170-103">Такие узлы, как Microsoft Internet Explorer, ASP.NET и оболочки Windows, загружают среду CLR в процесс, создают в этом процессе [домен приложения](../../../docs/framework/app-domains/application-domains.md), а затем загружают и выполняют пользовательский код в этом домене приложения при запуске приложения .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc170-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="dc170-104">В большинстве случаев вам не нужно беспокоиться о создании доменов приложений и загрузке сборок в них, так как эти задачи выполняет хост-приложение среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dc170-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="dc170-105">Тем не менее, если вы создаете приложение для размещения среды CLR, средства или код для создания средств или код для выгрузки программным способом, а также подключаемые компоненты для динамической выгрузки и повторной загрузки, вы будете создавать домены приложений.</span><span class="sxs-lookup"><span data-stu-id="dc170-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="dc170-106">Даже если вы не создаете хост-приложение среды выполнения, в этом разделе содержатся важные сведения по работе с доменами приложений и загруженными в них сборками.</span><span class="sxs-lookup"><span data-stu-id="dc170-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc170-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="dc170-107">In This Section</span></span>  
 [<span data-ttu-id="dc170-108">Руководства по работе с доменами приложений и сборками</span><span class="sxs-lookup"><span data-stu-id="dc170-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="dc170-109">Ссылки на все разделы практического руководства базовой документации по программированию с использованием доменов приложений и сборок.</span><span class="sxs-lookup"><span data-stu-id="dc170-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="dc170-110">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="dc170-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="dc170-111">Примеры создания, настройки и использования доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="dc170-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="dc170-112">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="dc170-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="dc170-113">Описание способов создания, подписи и установки атрибутов сборок.</span><span class="sxs-lookup"><span data-stu-id="dc170-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dc170-114">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="dc170-114">Related Sections</span></span>  
 [<span data-ttu-id="dc170-115">Предоставление динамических методов и сборок</span><span class="sxs-lookup"><span data-stu-id="dc170-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="dc170-116">Описание способов создания динамических сборок.</span><span class="sxs-lookup"><span data-stu-id="dc170-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="dc170-117">Сборки в среде CLR</span><span class="sxs-lookup"><span data-stu-id="dc170-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="dc170-118">Общие сведения о сборках.</span><span class="sxs-lookup"><span data-stu-id="dc170-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="dc170-119">Домены приложений</span><span class="sxs-lookup"><span data-stu-id="dc170-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="dc170-120">Общие сведения о доменах приложений.</span><span class="sxs-lookup"><span data-stu-id="dc170-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="dc170-121">Общие сведения о классе Reflection</span><span class="sxs-lookup"><span data-stu-id="dc170-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="dc170-122">Использование класса **Reflection** для получения сведений о сборке.</span><span class="sxs-lookup"><span data-stu-id="dc170-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
