---
title: Практическое руководство. Создание службы данных с помощью LINQ to SQL источника данных (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 6489e451f3790e38ea821104fd2aca5a8c091ba6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053005"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="9bbc5-102">Практическое руководство. Создание службы данных с помощью LINQ to SQL источника данных (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9bbc5-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="9bbc5-103">WCF Data Services предоставляет данные сущности в качестве службы данных.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="9bbc5-104">Поставщик отражения позволяет определить модель данных, основанную на любом классе, который предоставляет члены, возвращающие <xref:System.Linq.IQueryable%601> реализацию.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="9bbc5-105">Для выполнения обновлений данных в источнике данных эти классы должны также реализовать интерфейс <xref:System.Data.Services.IUpdatable>.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="9bbc5-106">Дополнительные сведения см. в разделе [поставщики служб данных](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc5-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="9bbc5-107">В этом разделе показано, как создать классы LINQ to SQL, обращающиеся к образцу базы данных Northwind с помощью поставщика, а также как создать службу данных на основе этих классов.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="9bbc5-108">Добавление в проект объектов классов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9bbc5-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="9bbc5-109">В Visual Basic C# или приложении в меню **проект** выберите команду **добавить** > **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9bbc5-110">Щелкните шаблон **LINQ to SQL классы** .</span><span class="sxs-lookup"><span data-stu-id="9bbc5-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="9bbc5-111">Измените имя на **Northwind. dbml**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="9bbc5-112">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-112">Click **Add**.</span></span>

     <span data-ttu-id="9bbc5-113">Файл Northwind.dbml добавляется в проект и открывается реляционный конструктор объектов.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="9bbc5-114">В**Обозреватель базы данных** **сервера**/в разделе Northwind разверните узел **таблицы** и перетащите `Customers` таблицу на Реляционный конструктор объектов (конструктор O/R).</span><span class="sxs-lookup"><span data-stu-id="9bbc5-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="9bbc5-115">При этом в области конструктора создается и отображается класс сущностей `Customer`.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="9bbc5-116">Повторите шаг 6 для таблиц `Orders`, `Order_Details` и `Products`.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="9bbc5-117">Щелкните правой кнопкой мыши новый DBML-файл, представляющий классы LINQ to SQL, и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="9bbc5-118">При этом создается новая страница с выделенным кодом Northwind.cs, содержащая разделяемый класс, производный от класса <xref:System.Data.Linq.DataContext>, представляющего в данном случае контекст `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="9bbc5-119">Замените содержимое файла Northwind.cs следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="9bbc5-120">Этот код реализует поставщик отражения, расширяя контекст <xref:System.Data.Linq.DataContext> и классы данных, сформированные LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="9bbc5-121">Создание службы данных с использованием модели данных на основе LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9bbc5-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="9bbc5-122">В **Обозреватель решений**щелкните правой кнопкой мыши имя проекта ASP.NET и выберите команду **Добавить** > **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="9bbc5-123">В диалоговом окне **Добавление нового элемента** выберите шаблон **WCF Data Service** из категории **веб** .</span><span class="sxs-lookup"><span data-stu-id="9bbc5-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Шаблон элемента службы данных WCF в Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="9bbc5-125">Шаблон **службы данных WCF** доступен в visual Studio 2015, но не в visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="9bbc5-126">Укажите имя службы и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="9bbc5-127">В Visual Studio для новой службы создаются файлы разметки и кодов XML.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="9bbc5-128">По умолчанию открывается окно редактора кода.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="9bbc5-129">В коде службы данных замените комментарий `/* TODO: put your data source class name here */` в определении класса, задающего службу данных, типом контейнера сущностей модели данных, который в данном случае равен `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="9bbc5-130">В коде службы данных замените код местозаполнителя в функции `InitializeService` следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="9bbc5-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="9bbc5-131">Это позволяет авторизованным клиентам осуществлять доступ к ресурсам трех указанных наборов сущностей.</span><span class="sxs-lookup"><span data-stu-id="9bbc5-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="9bbc5-132">Чтобы протестировать службу данных Northwind. svc с помощью веб-браузера, следуйте инструкциям в разделе [обращение к службе из веб-браузера](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc5-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bbc5-133">См. также</span><span class="sxs-lookup"><span data-stu-id="9bbc5-133">See also</span></span>

- [<span data-ttu-id="9bbc5-134">Практическое руководство. Создание службы данных с помощью источника данных ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9bbc5-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="9bbc5-135">Практическое руководство. Создание службы данных с помощью поставщика отражения</span><span class="sxs-lookup"><span data-stu-id="9bbc5-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="9bbc5-136">Поставщики служб данных</span><span class="sxs-lookup"><span data-stu-id="9bbc5-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
