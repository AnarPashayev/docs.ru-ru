---
title: Обзор
description: Ознакомьтесь с обзором ADO.NET в .NET Framework и прочитайте о ресурсах для получения более подробных пояснений и примеров.
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 459e4a548a4d1358b196dc41ec495921833728d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153499"
---
# <a name="adonet-overview"></a><span data-ttu-id="fe19d-103">Общие сведения о ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-103">ADO.NET Overview</span></span>

<span data-ttu-id="fe19d-104">ADO.NET предоставляет согласованный доступ к таким источникам данных, как SQL Server и XML, а также к источникам данных, предоставляемым при помощи OLE DB и ODBC.</span><span class="sxs-lookup"><span data-stu-id="fe19d-104">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="fe19d-105">Пользовательские приложения, использующие общие данные, могут использовать ADO.NET для соединения с этими источниками данных и для получения, обработки и обновления имеющихся в них данных.</span><span class="sxs-lookup"><span data-stu-id="fe19d-105">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="fe19d-106">ADO.NET разделят доступ к данным и обработку данных на дискретные компоненты, которые могут использоваться отдельно или совместно.</span><span class="sxs-lookup"><span data-stu-id="fe19d-106">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="fe19d-107">ADO.NET включает поставщиков данных .NET Framework для соединения с базой данных, выполнения команд и получения результатов.</span><span class="sxs-lookup"><span data-stu-id="fe19d-107">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="fe19d-108">Эти результаты, помещенные в объект ADO.NET <xref:System.Data.DataSet>, обрабатываются непосредственно, чтобы они могли быть предоставлены пользователю нерегламентированным образом, объединенные с данными из многих источников или передаваемые между уровнями.</span><span class="sxs-lookup"><span data-stu-id="fe19d-108">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="fe19d-109">Объект `DataSet` также может независимо использоваться поставщиком данных .NET Framework для управления локальными для приложения данными или данными, источником которых является XML.</span><span class="sxs-lookup"><span data-stu-id="fe19d-109">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="fe19d-110">Классы ADO.NET имеются в System.Data.dll и интегрируются с классами XML, имеющимися в System.Xml.dll.</span><span class="sxs-lookup"><span data-stu-id="fe19d-110">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="fe19d-111">Пример кода, который подключается к базе данных, извлекает из нее данные, а затем отображает эти данные в окне консоли, см. в разделе [примеры кода ADO.NET](ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="fe19d-111">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="fe19d-112">Для разработчиков, которые пишут управляемый код, ADO.NET предоставляет функциональный набор, сходный с функциональным набором, который предоставляют объекты данных ActiveX (ADO) разработчикам моделей объектов собственных компонентов (COM).</span><span class="sxs-lookup"><span data-stu-id="fe19d-112">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="fe19d-113">Для доступа к данным в приложении .NET мы рекомендуем использовать ADO.NET, а не ADO.</span><span class="sxs-lookup"><span data-stu-id="fe19d-113">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="fe19d-114">ADO.NET предоставляет самый прямой способ доступа к данным в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe19d-114">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="fe19d-115">Для абстракции более высокого уровня, которая позволяет приложениям работать с концептуальной моделью, а не с базовой моделью хранения, см. [ADO.NET Entity Framework](./ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe19d-115">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](./ef/index.md).</span></span>  
  
 <span data-ttu-id="fe19d-116">**Заявление о конфиденциальности**. сборки System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll и System.Data.DataSetExtensions.dll не различают закрытые и закрытые данные пользователя.</span><span class="sxs-lookup"><span data-stu-id="fe19d-116">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="fe19d-117">Эти сборки не собирают, не хранят и не переносят пользовательские личные данные.</span><span class="sxs-lookup"><span data-stu-id="fe19d-117">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="fe19d-118">Но приложения сторонних производителей могут собирать, хранить и переносить пользовательские личные данные с использованием этих сборок.</span><span class="sxs-lookup"><span data-stu-id="fe19d-118">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe19d-119">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="fe19d-119">In This Section</span></span>  

 [<span data-ttu-id="fe19d-120">Архитектура ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-120">ADO.NET Architecture</span></span>](ado-net-architecture.md)  
 <span data-ttu-id="fe19d-121">Предоставляет общие сведения об архитектуре и компонентах ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="fe19d-121">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="fe19d-122">Возможности технологии и рекомендации по ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-122">ADO.NET Technology Options and Guidelines</span></span>](ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="fe19d-123">Описываются продукты и технологии, входящие в состав платформы Entity Data Platform.</span><span class="sxs-lookup"><span data-stu-id="fe19d-123">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="fe19d-124">LINQ и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-124">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)  
 <span data-ttu-id="fe19d-125">Описывается реализация технологии LINQ (Language-Integrated Query) в ADO.NET и приводятся ссылки на соответствующие разделы.</span><span class="sxs-lookup"><span data-stu-id="fe19d-125">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="fe19d-126">Поставщики данных .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fe19d-126">.NET Framework Data Providers</span></span>](data-providers.md)  
 <span data-ttu-id="fe19d-127">Предоставляет общие сведения о конструкции поставщика данных .NET Framework и поставщиков данных .NET Framework, включенных при помощи ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="fe19d-127">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="fe19d-128">Наборы данных ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-128">ADO.NET DataSets</span></span>](ado-net-datasets.md)  
 <span data-ttu-id="fe19d-129">Предоставляет общие сведения о конструкции и компонентах `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="fe19d-129">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="fe19d-130">Одновременное выполнение в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-130">Side-by-Side Execution in ADO.NET</span></span>](side-by-side-execution.md)  
 <span data-ttu-id="fe19d-131">Рассматривает различия версий ADO.NET и их влияние на параллельное выполнение и совместимость приложений.</span><span class="sxs-lookup"><span data-stu-id="fe19d-131">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="fe19d-132">Примеры кода ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-132">ADO.NET Code Examples</span></span>](ado-net-code-examples.md)  
 <span data-ttu-id="fe19d-133">Предоставляет образцы кода, который получает данные при помощи поставщиков данных ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="fe19d-133">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fe19d-134">См. также</span><span class="sxs-lookup"><span data-stu-id="fe19d-134">Related Sections</span></span>  

 [<span data-ttu-id="fe19d-135">Новые возможности в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-135">What's New in ADO.NET</span></span>](whats-new.md)  
 <span data-ttu-id="fe19d-136">Представляет новые возможности ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="fe19d-136">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="fe19d-137">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-137">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="fe19d-138">Описывает приемы безопасного программирования при использовании ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="fe19d-138">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="fe19d-139">Сопоставления типов данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-139">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="fe19d-140">Описывается сопоставление между типами данных .NET Framework и поставщиками данных .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe19d-140">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="fe19d-141">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="fe19d-142">Описывает, как выполнять соединение с источником данных, получать и изменять данные.</span><span class="sxs-lookup"><span data-stu-id="fe19d-142">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="fe19d-143">К этому относятся `DataReaders` и `DataAdapters`.</span><span class="sxs-lookup"><span data-stu-id="fe19d-143">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe19d-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fe19d-144">See also</span></span>

- [<span data-ttu-id="fe19d-145">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe19d-145">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="fe19d-146">Доступ к данным в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe19d-146">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
