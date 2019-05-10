---
title: Практическое руководство. Как динамически создать базу данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: e5d66b49782d5f26b6d487e655aca6fbd6bdfb1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623868"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="786b0-102">Практическое руководство. Как динамически создать базу данных</span><span class="sxs-lookup"><span data-stu-id="786b0-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="786b0-103">В LINQ to SQL модель объектов сопоставляется с реляционной базой данных.</span><span class="sxs-lookup"><span data-stu-id="786b0-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="786b0-104">Сопоставление обеспечивается применением для описания структуры реляционной базы данных сопоставления на основе атрибутов или внешнего файла сопоставления.</span><span class="sxs-lookup"><span data-stu-id="786b0-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="786b0-105">В обоих случаях имеется достаточно сведений о реляционной базе данных, позволяющих создать новый экземпляр базы данных с помощью метода <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="786b0-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="786b0-106">Метод <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> создает реплику базы данных с той степенью подробности, которую позволяет обеспечить информация, закодированная в модели объектов.</span><span class="sxs-lookup"><span data-stu-id="786b0-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="786b0-107">Файлы сопоставления и атрибуты из модели объектов могут включать не все сведения относительно структуры существующей базы.</span><span class="sxs-lookup"><span data-stu-id="786b0-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="786b0-108">Сведения сопоставления не представляют содержимого определяемых пользователем функций, хранимых процедур, триггеров и проверочных ограничений.</span><span class="sxs-lookup"><span data-stu-id="786b0-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="786b0-109">Для большинства баз данных такого поведения достаточно.</span><span class="sxs-lookup"><span data-stu-id="786b0-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="786b0-110">Методом <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> можно воспользоваться в произвольном числе случаев, особенно если доступен известный поставщик данных наподобие Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="786b0-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="786b0-111">К числу типовых сценариев относятся.</span><span class="sxs-lookup"><span data-stu-id="786b0-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="786b0-112">Построение приложения, которое автоматически устанавливает себя на клиентской системе.</span><span class="sxs-lookup"><span data-stu-id="786b0-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="786b0-113">Построение клиентского приложения, которому требуется локальная база данных для сохранения своего автономного состояния.</span><span class="sxs-lookup"><span data-stu-id="786b0-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="786b0-114">Можно также вызвать с SQL Server метод <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>, указав имя MDF-файла или каталога, в зависимости от строки соединения.</span><span class="sxs-lookup"><span data-stu-id="786b0-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="786b0-115">использует строку соединения исходя из создаваемой базы данных и сервера, на котором она должна быть создана.</span><span class="sxs-lookup"><span data-stu-id="786b0-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="786b0-116">При любой возможности применяйте встроенную безопасность Windows для соединения с базой данных, чтобы не требовались пароли в строке соединения.</span><span class="sxs-lookup"><span data-stu-id="786b0-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="786b0-117">Пример</span><span class="sxs-lookup"><span data-stu-id="786b0-117">Example</span></span>  
 <span data-ttu-id="786b0-118">В приведенном ниже коде дан пример того, как создать новую базу данных с именем MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="786b0-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="786b0-119">Пример</span><span class="sxs-lookup"><span data-stu-id="786b0-119">Example</span></span>  
 <span data-ttu-id="786b0-120">Для создания базы данных можно использовать модель объектов, выполняя следующее:</span><span class="sxs-lookup"><span data-stu-id="786b0-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="786b0-121">Пример</span><span class="sxs-lookup"><span data-stu-id="786b0-121">Example</span></span>  
 <span data-ttu-id="786b0-122">При построении приложения, которое автоматически устанавливает себя на клиентской системе, проверьте, существует ли уже база данных, и удалите ее перед созданием новой базы.</span><span class="sxs-lookup"><span data-stu-id="786b0-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="786b0-123">Класс <xref:System.Data.Linq.DataContext> предоставляет методы <xref:System.Data.Linq.DataContext.DatabaseExists%2A> и <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> для помощи в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="786b0-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="786b0-124">Следующий пример показывает один из способов применения этих методов для реализации такого подхода.</span><span class="sxs-lookup"><span data-stu-id="786b0-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="786b0-125">См. также</span><span class="sxs-lookup"><span data-stu-id="786b0-125">See also</span></span>

- [<span data-ttu-id="786b0-126">Сопоставление, основанное на атрибутах</span><span class="sxs-lookup"><span data-stu-id="786b0-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="786b0-127">Внешнее сопоставление</span><span class="sxs-lookup"><span data-stu-id="786b0-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="786b0-128">Сопоставление типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="786b0-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="786b0-129">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="786b0-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="786b0-130">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="786b0-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
