---
title: Отладка, трассировка и профилирование
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754470"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="c5ad5-102">Отладка, трассировка и профилирование</span><span class="sxs-lookup"><span data-stu-id="c5ad5-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="c5ad5-103">Для отладки приложения .NET Framework компилятор и среда выполнения должны быть настроены для включения присоединения отладчика к приложению и создания символов и сопоставлений строк, если это возможно, для приложения и его соответствующего языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="c5ad5-104">После отладки управляемого приложения можно выполнить его профилирование для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="c5ad5-105">Профилирование оценивает и описывает строки исходного кода, создающие наиболее часто выполняемый код, и время, необходимое для их выполнения.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="c5ad5-106">Приложения .NET Framework можно легко отладить с помощью Visual Studio, который обрабатывает многие детали конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="c5ad5-107">Если Visual Studio не установлен, вы можете проверять и улучшать производительность приложений .NET Framework с помощью классов отладки в пространстве имен <xref:System.Diagnostics> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="c5ad5-108">Это пространство имен включает классы <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> и <xref:System.Diagnostics.TraceSource> для трассировки потока выполнения и классы <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> и <xref:System.Diagnostics.PerformanceCounter> для профилирования кода.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5ad5-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c5ad5-109">In This Section</span></span>  
 [<span data-ttu-id="c5ad5-110">Включение отладки с JIT-присоединением</span><span class="sxs-lookup"><span data-stu-id="c5ad5-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="c5ad5-111">Показывается, как настроить реестр для JIT-присоединения модуля отладки к приложению .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="c5ad5-112">Упрощение отладки образов</span><span class="sxs-lookup"><span data-stu-id="c5ad5-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="c5ad5-113">Показывается, как включить отслеживание JIT и отключить оптимизацию для упрощения процесса отладки сборки.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="c5ad5-114">Трассировка и инструментирование приложений</span><span class="sxs-lookup"><span data-stu-id="c5ad5-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="c5ad5-115">Описывается, как наблюдать за приложением, пока оно выполняется, и как инструментировать его для отображения того, насколько оно хорошо работает, или того, что пошло не так.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="c5ad5-116">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="c5ad5-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="c5ad5-117">Сведения о помощниках по отладке управляемого кода (MDA), которые являются вспомогательными средствами отладки, работающими совместно со средой CLR для предоставления сведений о состоянии времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="c5ad5-118">Повышение эффективности отладки с помощью атрибутов просмотра отладчика</span><span class="sxs-lookup"><span data-stu-id="c5ad5-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="c5ad5-119">Описывается, как разработчик типа может указать, как этот тип будет выглядеть при отображении в отладчике.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="c5ad5-120">Счетчики производительности</span><span class="sxs-lookup"><span data-stu-id="c5ad5-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="c5ad5-121">Описываются счетчики, которые можно использовать для отслеживания производительности приложения.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5ad5-122">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="c5ad5-122">Related Sections</span></span>  
 [<span data-ttu-id="c5ad5-123">Отладка приложений ASP.NET или ASP.NET Core в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5ad5-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 <span data-ttu-id="c5ad5-124">Предоставляются предварительные требования и инструкции по отладке приложения ASP.NET во время разработки или после развертывания.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="c5ad5-125">Руководство по разработке</span><span class="sxs-lookup"><span data-stu-id="c5ad5-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="c5ad5-126">Здесь содержится руководство по всем ключевым технологическим областям и задачам для разработки приложений, включая создание, настройку, отладку, безопасность и развертывание приложений, а также сведения о динамическом программировании, взаимодействии, расширении среды, управлении памятью и работе с потоками.</span><span class="sxs-lookup"><span data-stu-id="c5ad5-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
