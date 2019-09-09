---
title: Руководство по разработке для .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebbf0b28da04e2e70dd2d0a9689b80fcdbeee4be
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779535"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="32d3b-102">Руководство по разработке для .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="32d3b-103">В этом разделе поясняются способы создания, настройки, отладки, защиты и развертывания приложений .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="32d3b-104">В этом разделе также приводятся сведения о технологических областях, таких как динамическое программирование, взаимодействие, расширяемость, управление памятью и потоки.</span><span class="sxs-lookup"><span data-stu-id="32d3b-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32d3b-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="32d3b-105">In This Section</span></span>  
 [<span data-ttu-id="32d3b-106">Основные сведения о приложениях .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-106">Application Essentials</span></span>](../standard/application-essentials.md)  
 <span data-ttu-id="32d3b-107">Здесь приводится информация об основных задачах разработки приложений, таких как программирование с использованием доменов приложений и сборок, использование атрибутов, форматирование и анализ базовых типов, использование коллекций, обработка событий и исключений, использование файлов и потоков данных и использование универсальных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="32d3b-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="32d3b-108">Данные и модели в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-108">Data and Modeling</span></span>](./data/index.md)  
 <span data-ttu-id="32d3b-109">Здесь приводится информация о способах доступа к данным с использованием ADO.NET, LINQ, служб данных WCF и XML.</span><span class="sxs-lookup"><span data-stu-id="32d3b-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="32d3b-110">Разработка клиентских приложений с использованием .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-110">Client Applications</span></span>](develop-client-apps.md)  
 <span data-ttu-id="32d3b-111">Здесь поясняются способы создания приложений Windows с помощью Windows Presentation Foundation (WPF) и Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="32d3b-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="32d3b-112">Разработка веб-приложений с помощью ASP.NET</span><span class="sxs-lookup"><span data-stu-id="32d3b-112">Web Applications with ASP.NET</span></span>](develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="32d3b-113">Здесь приводятся ссылки на сведения об использовании ASP.NET для сборки веб-приложений корпоративного уровня с минимальным объемом кода.</span><span class="sxs-lookup"><span data-stu-id="32d3b-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="32d3b-114">Разработка сервисноориентированных приложений с помощью WCF</span><span class="sxs-lookup"><span data-stu-id="32d3b-114">Service-Oriented Applications with WCF</span></span>](./wcf/index.md)  
 <span data-ttu-id="32d3b-115">Здесь приводится описание способов использования Windows Communication Foundation (WCF) для сборки безопасных и надежных сервисноориентированных приложений.</span><span class="sxs-lookup"><span data-stu-id="32d3b-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="32d3b-116">[Построение рабочих процессов в .NET Framework](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="32d3b-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="32d3b-117">Здесь приводятся сведения о модели программирования и средствах Windows Workflow Foundation (WF), а также примеры.</span><span class="sxs-lookup"><span data-stu-id="32d3b-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="32d3b-118">Приложения служб Windows</span><span class="sxs-lookup"><span data-stu-id="32d3b-118">Windows Service Applications</span></span>](./windows-services/index.md)  
 <span data-ttu-id="32d3b-119">Здесь поясняется, как можно использовать Visual Studio и .NET Framework для создания приложения, которое устанавливается в качестве службы, а также запускать его, останавливать и иными способами управлять его поведением.</span><span class="sxs-lookup"><span data-stu-id="32d3b-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="32d3b-120">Параллельная обработка, параллелизм и асинхронное программирование в .NET</span><span class="sxs-lookup"><span data-stu-id="32d3b-120">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="32d3b-121">Здесь приводятся сведения о шаблонах разработки с применением управляемых потоков, параллельного программирования и асинхронного программирования.</span><span class="sxs-lookup"><span data-stu-id="32d3b-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="32d3b-122">Сетевое программирование в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-122">Network Programming in the .NET Framework</span></span>](./network-programming/index.md)  
 <span data-ttu-id="32d3b-123">Здесь приводится описание многоуровневой, расширяемой и управляемой реализации служб Интернета, которую можно быстро и легко интегрировать в приложения.</span><span class="sxs-lookup"><span data-stu-id="32d3b-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="32d3b-124">[Настройка приложений .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="32d3b-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="32d3b-125">Здесь поясняется, как можно использовать файлы конфигурации для изменения параметров без необходимости повторной компиляции приложений .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="32d3b-126">Компиляция приложений с помощью машинного кода .NET</span><span class="sxs-lookup"><span data-stu-id="32d3b-126">Compiling Apps with .NET Native</span></span>](./net-native/index.md)  
 <span data-ttu-id="32d3b-127">Здесь поясняется, как можно использовать технологию предварительной компиляции .NET Native для сборки и развертывания приложений Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="32d3b-127">Explains how you can use the .NET Native precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="32d3b-128">.NET Native компилирует приложения, написанные с помощью управляемого кода (C#) и адаптирующие .NET Framework к машинному коду.</span><span class="sxs-lookup"><span data-stu-id="32d3b-128">.NET Native compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="32d3b-129">Безопасность</span><span class="sxs-lookup"><span data-stu-id="32d3b-129">Security</span></span>](../standard/security/index.md)  
 <span data-ttu-id="32d3b-130">Сведения о классах и службах .NET Framework, предназначенных для упрощения разработки безопасных приложений.</span><span class="sxs-lookup"><span data-stu-id="32d3b-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="32d3b-131">Отладка, трассировка и профилирование</span><span class="sxs-lookup"><span data-stu-id="32d3b-131">Debugging, Tracing, and Profiling</span></span>](./debug-trace-profile/index.md)  
 <span data-ttu-id="32d3b-132">Здесь приводится описание способов тестирования, оптимизации и профилирования приложений .NET Framework и среды приложения.</span><span class="sxs-lookup"><span data-stu-id="32d3b-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="32d3b-133">Информация, содержащаяся в этом разделе, предназначена как для администраторов, так и для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="32d3b-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="32d3b-134">Разработка для нескольких платформ с помощью .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-134">Developing for Multiple Platforms</span></span>](../standard/cross-platform/index.md)  
 <span data-ttu-id="32d3b-135">Здесь поясняется, как можно использовать платформу .NET Framework для создания сборок, которые могут совместно использоваться несколькими платформами и устройствами, такими как телефоны, настольные системы и интернет-устройства.</span><span class="sxs-lookup"><span data-stu-id="32d3b-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="32d3b-136">Развертывание</span><span class="sxs-lookup"><span data-stu-id="32d3b-136">Deployment</span></span>](./deployment/index.md)  
 <span data-ttu-id="32d3b-137">Здесь поясняется порядок упаковки и распространения приложения .NET Framework; сюда также включены руководства по развертыванию как для разработчиков, так и для администраторов.</span><span class="sxs-lookup"><span data-stu-id="32d3b-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="32d3b-138">Производительность</span><span class="sxs-lookup"><span data-stu-id="32d3b-138">Performance</span></span>](./performance/index.md)  
 <span data-ttu-id="32d3b-139">Здесь приводятся сведения о кэшировании, отложенной инициализации, надежности и событиях трассировки событий Windows.</span><span class="sxs-lookup"><span data-stu-id="32d3b-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
 
## <a name="reference"></a><span data-ttu-id="32d3b-140">Справочник</span><span class="sxs-lookup"><span data-stu-id="32d3b-140">Reference</span></span>  
 [<span data-ttu-id="32d3b-141">Библиотека классов .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d3b-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="32d3b-142">Предоставляет синтаксис, примеры кода и сведения об использовании для каждого класса, содержащегося в пространствах имен .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-142">Supplies syntax, code examples, and usage information for each class that is contained in the .NET Framework namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32d3b-143">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="32d3b-143">Related Sections</span></span>  
 [<span data-ttu-id="32d3b-144">Начало работы</span><span class="sxs-lookup"><span data-stu-id="32d3b-144">Getting Started</span></span>](./get-started/index.md)  
 <span data-ttu-id="32d3b-145">Здесь содержится комплексный обзор платформы .NET Framework и ссылки на дополнительные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="32d3b-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="32d3b-146">Новые возможности</span><span class="sxs-lookup"><span data-stu-id="32d3b-146">What's New</span></span>](./whats-new/index.md)  
 <span data-ttu-id="32d3b-147">Здесь приводится описание ключевых новых возможностей и изменений в последней версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="32d3b-148">Сюда включены списки новых и устаревших типов и членов; также здесь приводится руководство по переносу приложений из предыдущей версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="32d3b-149">Инструменты</span><span class="sxs-lookup"><span data-stu-id="32d3b-149">Tools</span></span>](./tools/index.md)  
 <span data-ttu-id="32d3b-150">Инструменты, описанные в этом разделе, помогут в разработке, настройке и развертывании приложений с помощью технологий .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32d3b-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="32d3b-151">Примеры и руководства .NET</span><span class="sxs-lookup"><span data-stu-id="32d3b-151">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="32d3b-152">Предоставляет ссылки на примеры и руководства для изучения .NET.</span><span class="sxs-lookup"><span data-stu-id="32d3b-152">Provides links to samples and tutorials that help you learn about .NET.</span></span>
