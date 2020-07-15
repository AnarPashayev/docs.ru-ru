---
title: Managed Extensibility Framework (MEF)
description: Ознакомьтесь с решением Managed Extensibility Framework (MEF), которое позволяет разработчикам приложений обнаруживать и использовать расширения без необходимости настраивать конфигурацию в .NET 4 или более поздней версии.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 00ed48f2202d4c04039ac264b1fe71474a02432e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281255"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="3b2dd-103">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="3b2dd-103">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="3b2dd-104">В этой статье приводятся общие сведения о библиотеке Managed Extensibility Framework, которая появилась на платформе .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-104">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="3b2dd-105">Что такое MEF</span><span class="sxs-lookup"><span data-stu-id="3b2dd-105">What is MEF?</span></span>

<span data-ttu-id="3b2dd-106">Платформа Managed Extensibility Framework (MEF) — это библиотека для создания простых и расширяемых приложений.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-106">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="3b2dd-107">Она позволяет разработчикам приложений находить и использовать расширения без каких-либо настроек.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-107">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="3b2dd-108">Она также позволяет разработчикам расширений легко инкапсулировать код и избегать ненадежных жестких зависимостей.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-108">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="3b2dd-109">MEF позволяет повторно использовать в приложениях не только расширения, но и целые приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-109">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="3b2dd-110">Проблема расширяемости</span><span class="sxs-lookup"><span data-stu-id="3b2dd-110">The problem of extensibility</span></span>

<span data-ttu-id="3b2dd-111">Представьте себе, что вы являетесь архитектором крупного приложения, которое должно обеспечивать поддержку для расширяемости.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-111">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="3b2dd-112">Приложение должно включать потенциально большое количество небольших компонентов, а также отвечает за их создание и запуск.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-112">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="3b2dd-113">Простейшим подходом к решению такой проблемы является включение компонентов в виде исходного кода в приложение и их вызов прямо из кода.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-113">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="3b2dd-114">Такой подход имеет ряд очевидных недостатков.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-114">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="3b2dd-115">Самое главное, что нельзя добавлять новые компоненты без изменения исходного кода — данное ограничение может быть приемлемым, например, для веб-приложения, но не для клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-115">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="3b2dd-116">Столь же проблематичной может оказаться ситуация, что у вас не будет доступа к исходному коду для компонентов, так как они могут разрабатываться сторонними производителями, и в силу ряда причин вы не сможете разрешить им доступ к своим приложениям.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-116">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="3b2dd-117">Несколько более сложный подход будет заключаться в предоставлении точки или интерфейса расширения, позволяющего разделять приложение и его компоненты.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-117">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="3b2dd-118">В рамках этой модели можно предоставить интерфейс, который может реализовывать компонент, а также интерфейс API, позволяющий ему взаимодействовать с приложением.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-118">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="3b2dd-119">Это позволяет решить проблему необходимости доступа к исходному коду, но по-прежнему имеет свои собственные сложности.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-119">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="3b2dd-120">Так как приложение не в состоянии самостоятельно обнаруживать компоненты, ему по-прежнему необходимо явным образом сообщать, какие компоненты имеются в наличии и подлежат загрузке.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-120">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="3b2dd-121">Обычно для этого применяется явная регистрация доступных компонентов в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-121">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="3b2dd-122">Это означает, что обеспечение нужных компонентов превращается в задачу обслуживания, особенно в тех случаях, когда обновление должен выполнять конечный пользователь, а не сам разработчик.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-122">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="3b2dd-123">Кроме того, компоненты могут взаимодействовать друг с другом, за исключением строго определенных каналов самого приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-123">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="3b2dd-124">Если в архитектуре приложения не учтена потребность в определенной связи, то обычно это оказывается невозможным.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-124">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="3b2dd-125">Наконец, разработчики компонентов вынуждены принимать жесткие зависимости от того, какая именно сборка содержит реализуемый ими интерфейс.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-125">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="3b2dd-126">Это затрудняет возможное применение компонента в нескольких приложениях и также может вызвать проблемы при создании тестовой платформы для компонентов.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-126">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="3b2dd-127">Сведения о возможностях MEF</span><span class="sxs-lookup"><span data-stu-id="3b2dd-127">What MEF provides</span></span>

<span data-ttu-id="3b2dd-128">Вместо явной регистрации доступных компонент MEF позволяет обнаруживать их неявным образом — с помощью *композиции*.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-128">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="3b2dd-129">Компонент MEF, называемый *частью*, декларативно указывает как свои зависимости (называемые *импортом*), так и свои возможности, которые он предоставляет (называемые *экспортом*).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-129">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="3b2dd-130">При создании некоторой части обработчик композиции MEF удовлетворяет свои импортируемые компоненты за счет элементов, доступных из других частей.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-130">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="3b2dd-131">Такой поход позволяет решить проблемы, рассмотренные в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-131">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="3b2dd-132">Так как части MEF декларативно указывают свои возможности, они могут быть обнаружены во время выполнения, то есть, приложение может применять части без жестко кодированных ссылок или ненадежных файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-132">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="3b2dd-133">Платформа MEF позволяет приложениям обнаруживать и анализировать части с помощью своих метаданных без создания экземпляров и даже без загрузки их сборок.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-133">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="3b2dd-134">В результате нет необходимости четко указывать время и способ загрузки расширений.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-134">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="3b2dd-135">Кроме обеспечиваемого экспорта, часть может указать свои импортируемые элементы, которые будут заполнены другими частями.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-135">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="3b2dd-136">Это делает связь между частями не только возможной, но и простой, и обеспечивает качественное разбиение кода.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-136">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="3b2dd-137">Например, общие для нескольких компонентов службы можно выделить в отдельную часть, которую можно будет легко изменять или заменять.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-137">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="3b2dd-138">Так как для модели MEF жесткие зависимости от определенной сборки приложения не требуются, она позволяет повторно использовать расширения в различных приложениях.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-138">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="3b2dd-139">Это также упрощает разработку окружения теста, не зависящего от приложения, для тестирования компонентов расширений.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-139">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="3b2dd-140">Расширяемое приложение, созданное с помощью платформы MEF, объявляет импортируемый элемент, который может быть заполнен компонентами расширения, а также может объявить экспортируемые элементы, позволяющие применять службы приложений для расширений.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-140">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="3b2dd-141">Каждый компонент расширения объявляет экспортируемый элемент, а также может объявлять импортируемые элементы.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-141">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="3b2dd-142">Таким образом, сами компоненты расширения автоматически становятся расширяемыми.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-142">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="3b2dd-143">Где доступна MEF</span><span class="sxs-lookup"><span data-stu-id="3b2dd-143">Where MEF is available</span></span>

<span data-ttu-id="3b2dd-144">MEF является неотъемлемой частью .NET Framework 4 и присутствует везде, где применяется платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-144">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="3b2dd-145">MEF можно использовать в клиентских приложениях, независимо от того, применяют они Windows Forms, WPF или любую другую технологию, либо в серверных приложениях, где применяется ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-145">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="3b2dd-146">MEF и MAF</span><span class="sxs-lookup"><span data-stu-id="3b2dd-146">MEF and MAF</span></span>

<span data-ttu-id="3b2dd-147">На платформе .NET Framework предыдущих версий появилась платформа Managed Add-in Framework (MAF), которая позволяет изолировать и управлять расширениями в приложениях.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-147">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="3b2dd-148">MAF находится на более высоком уровне, чем MEF, и отвечает за изоляцию расширения, а также загрузку и выгрузку сборки, тогда как MEF отвечает за возможность обнаружения, расширяемости и переноса.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-148">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="3b2dd-149">Обе эти платформы тесно взаимодействуют друг с другом, и каждое одиночное приложение могут воспользоваться преимуществами их обоих.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-149">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="3b2dd-150">SimpleCalculator — пример приложения</span><span class="sxs-lookup"><span data-stu-id="3b2dd-150">SimpleCalculator: An example application</span></span>

<span data-ttu-id="3b2dd-151">Чтобы узнать о возможностях MEF, проще всего создать простое приложение MEF.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-151">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="3b2dd-152">В этом примере выполняется создание очень простого калькулятора, который называется SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-152">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="3b2dd-153">SimpleCalculator предназначен для создания консольного приложения, принимающего основные арифметические команды в формате «5 + 3» или «6 - 2» и возвращающего правильные ответы.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-153">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="3b2dd-154">Благодаря применению MEF, вы сможете добавлять новые операторы без изменения кода приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-154">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="3b2dd-155">Чтобы скачать полный исходный код для этого примера, см. раздел [Пример SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-155">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="3b2dd-156">Пример с SimpleCalculator предназначен просто для демонстрации концепции и синтаксиса платформы MEF, а не описания реального сценария для ее использования.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-156">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="3b2dd-157">Многие приложения, которые будут использовать возможности MEF, являются более сложными, чем SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-157">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="3b2dd-158">Более сложные примеры см. в разделе [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) в GitHub.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-158">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="3b2dd-159">Чтобы приступить к работе, создайте проект консольного приложения в Visual Studio и назовите его `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-159">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="3b2dd-160">Добавьте ссылку на сборку `System.ComponentModel.Composition`, где находится MEF.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-160">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="3b2dd-161">Откройте *Module1.vb* или *Program.cs* и добавьте инструкции `Imports` или `using` для `System.ComponentModel.Composition` и `System.ComponentModel.Composition.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-161">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="3b2dd-162">Оба этих пространства имен содержат типы MEF, необходимые для разработки расширяемого приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-162">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="3b2dd-163">Если вы используете Visual Basic, добавьте ключевое слово `Public` в строку, в которой объявляется модуль `Module1`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-163">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="3b2dd-164">Контейнер композиции и каталоги</span><span class="sxs-lookup"><span data-stu-id="3b2dd-164">Composition container and catalogs</span></span>

<span data-ttu-id="3b2dd-165">Основным элементом модели композиции MEF является *контейнер композиции*, который содержит все доступные части и выполняет композицию.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-165">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="3b2dd-166">Композиция обеспечивает сопоставление импортируемых и экспортируемых элементов.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-166">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="3b2dd-167">Наиболее распространенным типом контейнера композиции является <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, который вы будете использовать для SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-167">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="3b2dd-168">Если вы используете Visual Basic, добавьте открытый класс с именем `Program` в *Module1.vb*.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-168">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="3b2dd-169">Добавьте следующую строку в класс `Program` в *Module1.vb* или *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-169">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="3b2dd-170">Для обнаружения доступных частей в контейнерах композиции используется *каталог*.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-170">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="3b2dd-171">Каталог – это объект, который делает доступными части, обнаруженные в определенном источнике.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-171">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="3b2dd-172">MEF содержит каталоги для обнаружения частей с заданным типом, сборкой или директорией.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-172">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="3b2dd-173">Разработчики приложений могут легко создавать новые каталоги для обнаружения частей из других источников, например, веб-служб.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-173">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="3b2dd-174">Добавьте следующий конструктор в класс `Program`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-174">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="3b2dd-175">Вызов <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> указывает контейнеру композиции на необходимость компоновки определенного набора частей (в данном случае текущий экземпляр `Program`).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-175">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="3b2dd-176">Однако на этом этапе ничего не происходит, так как в `Program` нет импортируемых элементов для заполнения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-176">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="3b2dd-177">Импортируемые и экспортируемые элементы с атрибутами</span><span class="sxs-lookup"><span data-stu-id="3b2dd-177">Imports and Exports with attributes</span></span>

<span data-ttu-id="3b2dd-178">Во-первых, необходимо выбрать `Program` для импорта калькулятора.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-178">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="3b2dd-179">Это позволит отделять вопросы пользовательского интерфейса, например, ввод и вывод консоли, который будет поступать в `Program`, от логики калькулятора.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-179">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="3b2dd-180">Добавьте следующий код в класс `Program` :</span><span class="sxs-lookup"><span data-stu-id="3b2dd-180">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="3b2dd-181">Следует отметить, что объявление объекта `calculator` не является необычным, однако он содержит атрибут <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-181">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="3b2dd-182">Этот атрибут объявляет что-нибудь, подлежащее импорту; то есть, это будет заполнено обработчиком композиции при составлении объекта.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-182">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="3b2dd-183">Каждый импортируемый элемент имеет *контракт*, определяющий, с какими экспортируемыми элементами будет выполняться сопоставление.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-183">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="3b2dd-184">Контракт может быть явно заданный строкой, или он может создаваться автоматически платформой MEF из заданного типа (в данном случае интерфейс `ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-184">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="3b2dd-185">Любой экспортируемый элемент, объявленный с помощью контракта сопоставления, будет подставляться в этот импорт.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-185">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="3b2dd-186">Следует отметить, что типом объекта `calculator` на самом деле является `ICalculator`, это не является обязательным.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-186">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="3b2dd-187">Контракт не зависит от типа импортирующего объекта.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-187">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="3b2dd-188">(В этом случае можно опустить `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-188">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="3b2dd-189">MEF автоматически предположит, что контракт должен быть основан на типе импорта, если не указано явным образом.)</span><span class="sxs-lookup"><span data-stu-id="3b2dd-189">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="3b2dd-190">Добавьте этот простейший интерфейс в модуль или пространство имен `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-190">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="3b2dd-191">Теперь, после определения `ICalculator`, нужен класс, который его реализует.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-191">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="3b2dd-192">Добавьте следующий класс в модуль или пространство имен `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-192">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

<span data-ttu-id="3b2dd-193">Здесь используется экспортируемый элемент, соответствующий импортируемому элементу в `Program`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-193">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="3b2dd-194">Чтобы экспортируемый элемент соответствовал импортируемому, экспорт должен иметь такой же контракт.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-194">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="3b2dd-195">Экспорт по контракту на основе `typeof(MySimpleCalculator)` вызовет несовпадение, и импортируемый элемент не будет заполнен; контракт должен в точности совпадать.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-195">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="3b2dd-196">Так как контейнер композиции будет заполняться всеми доступными в этой сборке частями, часть `MySimpleCalculator` будет доступна.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-196">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="3b2dd-197">Когда конструктор для `Program` выполняет композицию для объекта `Program`, его импортируемый элемент будет заполняться объектом `MySimpleCalculator`, который будет создан для этой цели.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-197">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="3b2dd-198">Для уровня пользовательского интерфейса (`Program`) никакая другая информация не требуется.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-198">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="3b2dd-199">Таким образом, можно заполнить остальную часть логики интерфейса пользователя в методе `Main`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-199">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="3b2dd-200">Добавьте следующий код в метод `Main`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-200">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="3b2dd-201">Этот код просто считывает строку входных данных и вызывает функцию `Calculate` калькулятора `ICalculator` с результатом, который он записывает в консоль.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-201">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="3b2dd-202">То есть, весь код, требуемый в `Program`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-202">That is all the code you need in `Program`.</span></span> <span data-ttu-id="3b2dd-203">Все остальные действия будут выполняться по частям.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-203">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="3b2dd-204">Дополнительные импортируемые элементы и атрибут ImportMany</span><span class="sxs-lookup"><span data-stu-id="3b2dd-204">Further Imports and ImportMany</span></span>

<span data-ttu-id="3b2dd-205">Чтобы приложение SimpleCalculator было расширяемым, оно должно импортировать список операций.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-205">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="3b2dd-206">Обычный атрибут <xref:System.ComponentModel.Composition.ImportAttribute> заполняется одним и только одним <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-206">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="3b2dd-207">Если имеется несколько значений, обработчик композиции выдаст ошибку.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-207">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="3b2dd-208">Чтобы создать импортируемый элемент, который может заполняться произвольным количеством экспортируемых элементов, можно использовать атрибут <xref:System.ComponentModel.Composition.ImportManyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-208">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="3b2dd-209">Добавьте в класс `MySimpleCalculator` следующее свойство операций:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-209">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="3b2dd-210"><xref:System.Lazy%602> — это тип, задаваемый платформой MEF для сохранения косвенных ссылок на экспортируемые элементы.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-210"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="3b2dd-211">Здесь, кроме самого экспортируемого объекта, вы также получаете *метаданные экспорта* или информацию, описывающую экспортируемый объект.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-211">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="3b2dd-212">Каждый <xref:System.Lazy%602> содержит объект `IOperation`, представляющий собой фактическую операцию, и объект `IOperationData`, представляющий ее метаданные.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-212">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="3b2dd-213">Добавьте следующие простые интерфейсы в модуль или пространство имен `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-213">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="3b2dd-214">В этом случае метаданными для каждой операции является символ, представляющий данную операцию, например, +, -, \* и т. д.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-214">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="3b2dd-215">Чтобы сделать доступной операцию сложения, добавьте следующий класс в модуль или пространство имен `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-215">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<span data-ttu-id="3b2dd-216">Атрибут <xref:System.ComponentModel.Composition.ExportAttribute> функционирует так же, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-216">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="3b2dd-217">Атрибут <xref:System.ComponentModel.Composition.ExportMetadataAttribute> присоединяет метаданные к данному экспортируемому элементу в виде пары "имя значение".</span><span class="sxs-lookup"><span data-stu-id="3b2dd-217">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="3b2dd-218">Если `Add` реализует `IOperation`, то класс, реализующий `IOperationData`, явным образом не определен.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-218">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="3b2dd-219">Вместо этого, он создается неявным образом платформой MEF со свойствами на основе имен предоставленных метаданных.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-219">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="3b2dd-220">(Это один из нескольких способов доступа к метаданным в MEF.)</span><span class="sxs-lookup"><span data-stu-id="3b2dd-220">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="3b2dd-221">Композиция на платформе MEF является *рекурсивной*.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-221">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="3b2dd-222">Вы явным образом составили композицию объекта `Program`, импортировавшего `ICalculator`, который получил тип `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-222">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="3b2dd-223">`MySimpleCalculator`, в свою очередь, импортирует коллекцию объектов `IOperation`, и данный импорт будет заполнен при создании `MySimpleCalculator`, одновременно с импортируемыми элементами `Program`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-223">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="3b2dd-224">Если `Add` класс объявил дополнительный импортируемый элемент, он тоже должен быть заполнен, и т. д.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-224">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="3b2dd-225">Любой незаполненный импорт будет вызывать ошибку композиции.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-225">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="3b2dd-226">(Однако можно объявить, что импортируемые элементы являются необязательными, или присвоить им значения по умолчанию.)</span><span class="sxs-lookup"><span data-stu-id="3b2dd-226">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="3b2dd-227">Логика калькулятора</span><span class="sxs-lookup"><span data-stu-id="3b2dd-227">Calculator Logic</span></span>

<span data-ttu-id="3b2dd-228">При наличии всех этих частей все, что остается, представляет собой саму логику калькулятора.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-228">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="3b2dd-229">Добавьте следующий код в класс `MySimpleCalculator` для реализации метода `Calculate`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-229">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

<span data-ttu-id="3b2dd-230">Начальные действия анализируют входную строку по левому и правому операндам, а также символ оператора.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-230">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="3b2dd-231">В цикле `foreach` анализируется каждый член коллекции `operations`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-231">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="3b2dd-232">Эти объекты относятся к типу <xref:System.Lazy%602>, а доступ к значениям их метаданных и экспортируемому объекту можно получить с помощью, соответственно, свойств <xref:System.Lazy%602.Metadata%2A> и <xref:System.Lazy%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-232">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="3b2dd-233">В этом случае, если обнаружено, что свойство `Symbol` объекта `IOperationData` совпадает, калькулятор вызывает метод `Operate` объекта `IOperation` и возвращает результат.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-233">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="3b2dd-234">Для завершения работы над калькулятором также нужен вспомогательный метод, который возвращает позицию первого нецифрового символа в строке.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-234">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="3b2dd-235">Добавьте в класс `MySimpleCalculator` следующий вспомогательный метод:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-235">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="3b2dd-236">Теперь вы должны получить возможность скомпилировать и запустить проект.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-236">You should now be able to compile and run the project.</span></span> <span data-ttu-id="3b2dd-237">В Visual Basic убедитесь, что вы добавили ключевое слово `Public` в `Module1`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-237">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="3b2dd-238">В окне консоли введите операцию сложения, например "5 + 3", и калькулятор вернет результат.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-238">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="3b2dd-239">Любой другой оператор вернет сообщение "Operation Not Found" (Операция не найдена).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-239">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="3b2dd-240">!".</span><span class="sxs-lookup"><span data-stu-id="3b2dd-240">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="3b2dd-241">Расширение приложения SimpleCalculator с помощью нового класса</span><span class="sxs-lookup"><span data-stu-id="3b2dd-241">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="3b2dd-242">Теперь, когда калькулятор работает, добавление новой операции является простой задачей.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-242">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="3b2dd-243">Добавьте следующий класс в модуль или пространство имен `SimpleCalculator`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-243">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

<span data-ttu-id="3b2dd-244">Скомпилируйте и запустите проект.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-244">Compile and run the project.</span></span> <span data-ttu-id="3b2dd-245">Выполните операцию вычитания, например, "5 - 3".</span><span class="sxs-lookup"><span data-stu-id="3b2dd-245">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="3b2dd-246">Теперь калькулятор выполняет операции вычитания наряду со сложением.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-246">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="3b2dd-247">Расширение приложения SimpleCalculator с помощью новой сборки</span><span class="sxs-lookup"><span data-stu-id="3b2dd-247">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="3b2dd-248">Процедура добавления классов в исходный код является довольно простой, но MEF позволяет искать части за пределами исходного кода приложения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-248">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="3b2dd-249">Чтобы продемонстрировать это, необходимо изменить приложение SimpleCalculator для поиска в каталоге, а также в его собственной сборке, частей путем добавления <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-249">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="3b2dd-250">Добавьте новый каталог с именем `Extensions` в проект SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-250">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="3b2dd-251">Убедитесь, что добавление выполняется на уровне проекта, а не на уровне решения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-251">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="3b2dd-252">Затем добавьте новый проект библиотеки классов в решение с именем `ExtendedOperations`.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-252">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="3b2dd-253">Новый проект будет скомпилирован в отдельную сборку.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-253">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="3b2dd-254">Откройте конструктор свойств проекта для проекта ExtendedOperations и перейдите на вкладку **Компиляция** или **Сборка**. Измените значение в поле **Выходной путь сборки** или **Выходной путь** так, чтобы оно указывало на каталог расширений в каталоге проекта SimpleCalculator ( *..\SimpleCalculator\Extensions\\* ).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-254">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="3b2dd-255">В *Module1.vb* или *Program.cs* добавьте следующую строку в конструктор `Program`:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-255">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="3b2dd-256">Замените пример пути на путь к каталогу расширений.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-256">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="3b2dd-257">(Этот абсолютный путь используется только для отладки.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-257">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="3b2dd-258">В реальном приложении будет использоваться относительный путь.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> добавит все части, найденные в сборках в каталоге расширений, в контейнер композиции.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-258">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="3b2dd-259">В проекте ExtendedOperations добавьте ссылки на приложение SimpleCalculator и System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-259">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="3b2dd-260">В файле класса ExtendedOperations добавьте оператор `Imports` или `using` для System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-260">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="3b2dd-261">В Visual Basic также добавьте оператор `Imports` для SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-261">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="3b2dd-262">Затем добавьте следующий класс в файл класса ExtendedOperations:</span><span class="sxs-lookup"><span data-stu-id="3b2dd-262">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

<span data-ttu-id="3b2dd-263">Следует отметить, что для совпадения контрактов атрибут <xref:System.ComponentModel.Composition.ExportAttribute> должен иметь тот же тип, что и <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-263">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="3b2dd-264">Скомпилируйте и запустите проект.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-264">Compile and run the project.</span></span> <span data-ttu-id="3b2dd-265">Проверьте новый оператор Mod (%).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-265">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="3b2dd-266">Заключение</span><span class="sxs-lookup"><span data-stu-id="3b2dd-266">Conclusion</span></span>

<span data-ttu-id="3b2dd-267">В этом разделе рассмотрены основные концепции платформы MEF.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-267">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="3b2dd-268">Части, каталоги и контейнер композиции</span><span class="sxs-lookup"><span data-stu-id="3b2dd-268">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="3b2dd-269">Части и контейнер композиции являются базовыми строительными блоками приложения MEF.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-269">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="3b2dd-270">Часть — это любой объект, который импортирует или экспортирует значение, вплоть до самого себя.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-270">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="3b2dd-271">Каталог содержит коллекцию частей из определенного источника.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-271">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="3b2dd-272">Контейнер композиции использует части, предоставленные каталогом для выполнения композиции, привязки импортируемых и экспортируемых элементов.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-272">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="3b2dd-273">Импортируемые и экспортируемые элементы</span><span class="sxs-lookup"><span data-stu-id="3b2dd-273">Imports and exports</span></span>

     <span data-ttu-id="3b2dd-274">Импортируемые и экспортируемые элементы позволяют компонентам взаимодействовать друг с другом.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-274">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="3b2dd-275">При импорте компонент указывает на необходимость в определенном значении или объекте, а при экспорте он указывает на доступность значения.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-275">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="3b2dd-276">Каждый импортируемый элемент сопоставляется со списком экспортируемых элементов при помощи своего контракта.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-276">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3b2dd-277">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="3b2dd-277">Next steps</span></span>

<span data-ttu-id="3b2dd-278">Чтобы скачать полный исходный код для этого примера, см. раздел [Пример SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-278">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="3b2dd-279">Дополнительные сведения и примеры кода см. в разделе [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="3b2dd-279">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="3b2dd-280">Список типов MEF см. в пространстве имен <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b2dd-280">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
