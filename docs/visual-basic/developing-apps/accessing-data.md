---
title: Доступ к данным в приложениях Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
ms.openlocfilehash: 0f17df93fc4ef22ef45f7ceff89bfb5f1ab1c18d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523953"
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="f07d0-102">Доступ к данным в приложениях Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f07d0-102">Accessing data in Visual Basic applications</span></span>

<span data-ttu-id="f07d0-103">В Visual Basic входит несколько новых возможностей для разработки приложений, обращающихся к данным.</span><span class="sxs-lookup"><span data-stu-id="f07d0-103">Visual Basic includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="f07d0-104">Формы с привязкой к данным для приложений Windows создаются путем перетаскивания элементов из [окна "Источники данных"](/visualstudio/data-tools/add-new-data-sources) на форму.</span><span class="sxs-lookup"><span data-stu-id="f07d0-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="f07d0-105">Привязка элементов управления к данным осуществляется путем перетаскивания элементов из **окна "Источники данных"** на форму.</span><span class="sxs-lookup"><span data-stu-id="f07d0-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f07d0-106">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="f07d0-106">Related sections</span></span>

[<span data-ttu-id="f07d0-107">Доступ к данным в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f07d0-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
<span data-ttu-id="f07d0-108">Содержит ссылки на страницы, посвященные добавлению в приложения функциональности доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="f07d0-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

[<span data-ttu-id="f07d0-109">Visual Studio Data Tools для .NET</span><span class="sxs-lookup"><span data-stu-id="f07d0-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
<span data-ttu-id="f07d0-110">Содержит ссылки на страницы, посвященные созданию в Visual Studio приложений для работы с данными.</span><span class="sxs-lookup"><span data-stu-id="f07d0-110">Provides links to pages on creating applications that work with data, using Visual Studio.</span></span>

[<span data-ttu-id="f07d0-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="f07d0-111">LINQ</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)  
<span data-ttu-id="f07d0-112">Содержит ссылки на разделы, описывающие использование LINQ с Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f07d0-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>

[<span data-ttu-id="f07d0-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f07d0-113">LINQ to SQL</span></span>](../../framework/data/adonet/sql/linq/index.md)  
<span data-ttu-id="f07d0-114">Содержит сведения о [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f07d0-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="f07d0-115">Включает примеры программирования.</span><span class="sxs-lookup"><span data-stu-id="f07d0-115">Includes programming examples.</span></span>  

[<span data-ttu-id="f07d0-116">Средства LINQ to SQL в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f07d0-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
<span data-ttu-id="f07d0-117">Содержит ссылки на разделы, посвященные созданию объектной модели [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f07d0-117">Provides links to topics about how to create a [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>

[<span data-ttu-id="f07d0-118">Работа с наборами данных в N-уровневых приложениях</span><span class="sxs-lookup"><span data-stu-id="f07d0-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
<span data-ttu-id="f07d0-119">Содержит ссылки на разделы о создании многоуровневых приложений для работы с данными.</span><span class="sxs-lookup"><span data-stu-id="f07d0-119">Provides links to topics about how to create multitiered data applications.</span></span>

[<span data-ttu-id="f07d0-120">Добавление новых подключений</span><span class="sxs-lookup"><span data-stu-id="f07d0-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
<span data-ttu-id="f07d0-121">Содержит ссылки на страницы, посвященные подключению приложения к данным при помощи инструментов времени разработки и объектов подключения ADO.NET в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f07d0-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using Visual Studio.</span></span>

[<span data-ttu-id="f07d0-122">Инструменты для работы с наборами данных в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f07d0-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
<span data-ttu-id="f07d0-123">Содержит ссылки на страницы, описывающие загрузку данных в наборы данных, а также выполнение инструкций SQL и хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="f07d0-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  

[<span data-ttu-id="f07d0-124">Привязка элементов управления к данным в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f07d0-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
<span data-ttu-id="f07d0-125">Содержит ссылки на страницы, в которых объясняется, как отображать данные в формах Windows Forms с помощью элементов управления с привязкой к данным.</span><span class="sxs-lookup"><span data-stu-id="f07d0-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>

[<span data-ttu-id="f07d0-126">Изменение данных в наборах данных</span><span class="sxs-lookup"><span data-stu-id="f07d0-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
<span data-ttu-id="f07d0-127">Содержит ссылки на страницы, описывающие способы управления данными в таблицах данных набора данных.</span><span class="sxs-lookup"><span data-stu-id="f07d0-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  

[<span data-ttu-id="f07d0-128">Проверка данных в наборах данных</span><span class="sxs-lookup"><span data-stu-id="f07d0-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
<span data-ttu-id="f07d0-129">Содержит ссылки на страницы, описывающие добавление функции проверки набора данных при изменении столбцов и строк.</span><span class="sxs-lookup"><span data-stu-id="f07d0-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>

[<span data-ttu-id="f07d0-130">Сохранение данных обратно в базу данных</span><span class="sxs-lookup"><span data-stu-id="f07d0-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
<span data-ttu-id="f07d0-131">Содержит ссылки на страницы с объяснением процедуры отправки обновленных данных из приложения в базу данных.</span><span class="sxs-lookup"><span data-stu-id="f07d0-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>

[<span data-ttu-id="f07d0-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f07d0-132">ADO.NET</span></span>](../../framework/data/adonet/index.md)  
<span data-ttu-id="f07d0-133">Описание классов ADO.NET, которые предоставляют программистам .NET Framework службы доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="f07d0-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

[<span data-ttu-id="f07d0-134">Данные в решениях Office</span><span class="sxs-lookup"><span data-stu-id="f07d0-134">Data in Office Solutions</span></span>](/visualstudio/vsto/data-in-office-solutions)  
<span data-ttu-id="f07d0-135">Содержит ссылки на страницы с пояснением работы данных в решениях Office, включая информацию о схемо-ориентированном программировании, кэшировании данных и доступе к данным на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="f07d0-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
