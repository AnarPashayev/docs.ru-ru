---
title: Службы WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 6910bfbc94f69292bb8c2a52bf3ebef8fcfb3a8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876464"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="a5c48-102">Службы WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="a5c48-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="a5c48-103">Службы WCF Data Services (прежнее название «Службы данных ADO.NET») — это компонент платформы .NET Framework, которая позволяет создавать службы, использующие [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] для предоставления и получения данных через Интернет или интрасеть с помощью семантики [ передачи репрезентативного состояния (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="a5c48-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="a5c48-104">OData предоставляет доступ к данным в виде ресурсов, которые адресуются по URI.</span><span class="sxs-lookup"><span data-stu-id="a5c48-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="a5c48-105">Доступ и изменение данных производится с помощью таких стандартных команд HTTP, как GET, PUT, POST и DELETE.</span><span class="sxs-lookup"><span data-stu-id="a5c48-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="a5c48-106">OData использует правила сущность связь [модели EDM](../../../../docs/framework/data/adonet/entity-data-model.md) для предоставления ресурсов в виде наборов сущностей, связанных ассоциациями.</span><span class="sxs-lookup"><span data-stu-id="a5c48-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="a5c48-107">Службы WCF Data Services использует протокол OData для адресации и обновлении ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a5c48-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="a5c48-108">Таким образом доступ к этим службам из любого клиента, поддерживающего OData.</span><span class="sxs-lookup"><span data-stu-id="a5c48-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="a5c48-109">OData позволяет запрашивать и записывать данные в ресурсы с использованием традиционных форматов передачи: Atom, набора стандартов обмена и обновления данных XML и нотации объектов JavaScript (JSON), формат текстовых данных exchange, применяемого в приложениях AJAX.</span><span class="sxs-lookup"><span data-stu-id="a5c48-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="a5c48-110">Службы WCF Data Services позволяет предоставлять данные, поступающие из различных источников, как веб-каналов OData.</span><span class="sxs-lookup"><span data-stu-id="a5c48-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="a5c48-111">Набор средств Visual Studio упрощают создание службы на основе OData с помощью модели данных ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a5c48-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="a5c48-112">Можно также создать веб-каналов OData на основе классы CLR (CLR) и даже с поздним связыванием или нетипизированных данных.</span><span class="sxs-lookup"><span data-stu-id="a5c48-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="a5c48-113">Службы WCF Data Services также включает набор клиентских библиотек: одну для типовых клиентских приложений .NET Framework, а другую специально для приложений на основе Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a5c48-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="a5c48-114">Эти клиентские библиотеки предоставляют модель объектно ориентированного программирования, при доступе к каналу OData из среды, например .NET Framework и Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a5c48-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="a5c48-115">Подготовка к изучению темы</span><span class="sxs-lookup"><span data-stu-id="a5c48-115">Where Should I Start?</span></span>

<span data-ttu-id="a5c48-116">В зависимости от потребностей рассмотрите возможность Приступая к работе со службами данных WCF в одном из следующих разделов.</span><span class="sxs-lookup"><span data-stu-id="a5c48-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="a5c48-117">Необходимо перейти непосредственно к…</span><span class="sxs-lookup"><span data-stu-id="a5c48-117">I want to jump right in...</span></span>

- [<span data-ttu-id="a5c48-118">Краткое руководство</span><span class="sxs-lookup"><span data-stu-id="a5c48-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [<span data-ttu-id="a5c48-119">Начало работы</span><span class="sxs-lookup"><span data-stu-id="a5c48-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="a5c48-120">Краткое руководство по Silverlight</span><span class="sxs-lookup"><span data-stu-id="a5c48-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="a5c48-121">Краткое руководство по Silverlight для разработчиков Windows Phone</span><span class="sxs-lookup"><span data-stu-id="a5c48-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="a5c48-122">Просто Ознакомьте меня примерами кода...</span><span class="sxs-lookup"><span data-stu-id="a5c48-122">Just show me some code...</span></span>

- [<span data-ttu-id="a5c48-123">Краткое руководство</span><span class="sxs-lookup"><span data-stu-id="a5c48-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [<span data-ttu-id="a5c48-124">Практическое руководство. Выполнение запросов к службе данных</span><span class="sxs-lookup"><span data-stu-id="a5c48-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="a5c48-125">Практическое руководство. Привязка данных к элементам Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a5c48-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="a5c48-126">Я хочу узнать больше о OData...</span><span class="sxs-lookup"><span data-stu-id="a5c48-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="a5c48-127">Технический документ. Введение в OData</span><span class="sxs-lookup"><span data-stu-id="a5c48-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="a5c48-128">Веб-сайт протокола Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="a5c48-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="a5c48-129">OData: ПАКЕТ SDK</span><span class="sxs-lookup"><span data-stu-id="a5c48-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="a5c48-130">OData: Вопросы и ответы</span><span class="sxs-lookup"><span data-stu-id="a5c48-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="a5c48-131">Я хочу посмотреть некоторые видеоматериалы...</span><span class="sxs-lookup"><span data-stu-id="a5c48-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="a5c48-132">Руководство для начинающих по службам данных WCF</span><span class="sxs-lookup"><span data-stu-id="a5c48-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="a5c48-133">Видеофильмы о службах данных WCF для разработчиков</span><span class="sxs-lookup"><span data-stu-id="a5c48-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="a5c48-134">OData: Веб-узел разработчиков</span><span class="sxs-lookup"><span data-stu-id="a5c48-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="a5c48-135">Я хочу см. в разделе примеров end-to-end...</span><span class="sxs-lookup"><span data-stu-id="a5c48-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="a5c48-136">Образцы документации по службам WCF Data Services в коллекции образцов MSDN</span><span class="sxs-lookup"><span data-stu-id="a5c48-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="a5c48-137">Другие образцы служб WCF Data Services в коллекции образцов MSDN</span><span class="sxs-lookup"><span data-stu-id="a5c48-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="a5c48-138">OData: ПАКЕТ SDK</span><span class="sxs-lookup"><span data-stu-id="a5c48-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="a5c48-139">Как происходит интеграция со средствами Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5c48-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="a5c48-140">Создание библиотеки клиентов службы данных</span><span class="sxs-lookup"><span data-stu-id="a5c48-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="a5c48-141">Создание службы данных</span><span class="sxs-lookup"><span data-stu-id="a5c48-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

- [<span data-ttu-id="a5c48-142">Поставщик Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a5c48-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="a5c48-143">Рекомендуемые действия в этой ситуации</span><span class="sxs-lookup"><span data-stu-id="a5c48-143">What can I do with it?</span></span>

- [<span data-ttu-id="a5c48-144">Обзор</span><span class="sxs-lookup"><span data-stu-id="a5c48-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

- [<span data-ttu-id="a5c48-145">Технический документ. Введение в OData</span><span class="sxs-lookup"><span data-stu-id="a5c48-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="a5c48-146">Сценарии приложения</span><span class="sxs-lookup"><span data-stu-id="a5c48-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="a5c48-147">Я хочу использовать Silverlight...</span><span class="sxs-lookup"><span data-stu-id="a5c48-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="a5c48-148">Краткое руководство по Silverlight</span><span class="sxs-lookup"><span data-stu-id="a5c48-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="a5c48-149">Службы WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="a5c48-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="a5c48-150">Приступая к работе с Silverlight</span><span class="sxs-lookup"><span data-stu-id="a5c48-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="a5c48-151">Я хочу использовать LINQ...</span><span class="sxs-lookup"><span data-stu-id="a5c48-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="a5c48-152">Выполнение запросов к службе данных</span><span class="sxs-lookup"><span data-stu-id="a5c48-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="a5c48-153">Рекомендации по LINQ</span><span class="sxs-lookup"><span data-stu-id="a5c48-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="a5c48-154">Практическое руководство. Выполнение запросов к службе данных</span><span class="sxs-lookup"><span data-stu-id="a5c48-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="a5c48-155">Я по-прежнему требуются некоторые дополнительные сведения...</span><span class="sxs-lookup"><span data-stu-id="a5c48-155">I still need some more information...</span></span>

- [<span data-ttu-id="a5c48-156">Блог группы служб WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5c48-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="a5c48-157">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="a5c48-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

- [<span data-ttu-id="a5c48-158">Центр разработчиков WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5c48-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="a5c48-159">Веб-сайт протокола Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="a5c48-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="a5c48-160">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a5c48-160">In This Section</span></span>

[<span data-ttu-id="a5c48-161">Обзор</span><span class="sxs-lookup"><span data-stu-id="a5c48-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

<span data-ttu-id="a5c48-162">Обзор возможностей и функций, доступных в службах WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="a5c48-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="a5c48-163">[Новые возможности в службах WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="a5c48-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="a5c48-164">Описывает новые возможности в службах WCF Data Services и поддержка новых функций OData.</span><span class="sxs-lookup"><span data-stu-id="a5c48-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="a5c48-165">Начало работы</span><span class="sxs-lookup"><span data-stu-id="a5c48-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

<span data-ttu-id="a5c48-166">Описывает предоставление и использование веб-каналов OData с помощью служб данных WCF.</span><span class="sxs-lookup"><span data-stu-id="a5c48-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="a5c48-167">Определение служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="a5c48-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

<span data-ttu-id="a5c48-168">Описывает создание и настройка службы данных, которая предоставляет веб-каналов OData.</span><span class="sxs-lookup"><span data-stu-id="a5c48-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="a5c48-169">Библиотека клиентов служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="a5c48-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

<span data-ttu-id="a5c48-170">Описывает использование клиентских библиотек для использования каналов OData из клиентского приложения .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5c48-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5c48-171">См. также</span><span class="sxs-lookup"><span data-stu-id="a5c48-171">See also</span></span>

- [<span data-ttu-id="a5c48-172">Передача состояния представления (REST)</span><span class="sxs-lookup"><span data-stu-id="a5c48-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
