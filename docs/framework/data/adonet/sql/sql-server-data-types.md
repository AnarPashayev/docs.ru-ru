---
title: Типы данных SQL Server и ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780851"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="fde16-102">Типы данных SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fde16-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="fde16-103">В SQL Server и .NET Framework используются различные системы типов, что может привести к потенциальной потере данных.</span><span class="sxs-lookup"><span data-stu-id="fde16-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="fde16-104">Чтобы сохранить целостность данных, поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>) предоставляет типизированные методы доступа для работы с данными SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fde16-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="fde16-105">Для указания типов данных <xref:System.Data.SqlDbType> можно использовать перечисления классов <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="fde16-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="fde16-106">Дополнительные сведения и таблица с описанием сопоставлений типов данных между типами данных SQL Server и .NET Framework см. в разделе [SQL Server сопоставления типов данных](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="fde16-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="fde16-107">В SQL Server 2008 появились новые типы данных, разработанные для удовлетворения бизнес-потребностей по работе с датами и временем, структурированными, частично структурированными и неструктурированными данными.</span><span class="sxs-lookup"><span data-stu-id="fde16-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="fde16-108">Новые типы данных описаны в электронной документации по SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fde16-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="fde16-109">Типы данных SQL Server, которые можно использовать в приложениях, зависят от используемой версии SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fde16-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="fde16-110">Дополнительные сведения см. в электронной документации для соответствующей версии SQL Server в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="fde16-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="fde16-111">**Электронная документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fde16-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="fde16-112">Типы данных (ядро СУБД)</span><span class="sxs-lookup"><span data-stu-id="fde16-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="fde16-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="fde16-113">In This Section</span></span>  
 [<span data-ttu-id="fde16-114">Типы SqlType и набор данных</span><span class="sxs-lookup"><span data-stu-id="fde16-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="fde16-115">Описывается поддержка типов для объекта `SqlTypes` в объекте `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="fde16-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="fde16-116">Обработка значений NULL</span><span class="sxs-lookup"><span data-stu-id="fde16-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="fde16-117">Демонстрируется работа со значениями NULL и тройственной логикой.</span><span class="sxs-lookup"><span data-stu-id="fde16-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="fde16-118">Сравнение значений идентификатора GUID и uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="fde16-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="fde16-119">Демонстрируется работа со значениями GUID и uniqueidentifier в SQL Server и .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fde16-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="fde16-120">Данные даты и времени</span><span class="sxs-lookup"><span data-stu-id="fde16-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="fde16-121">Описывается использование новых типов данных даты и времени, появившихся в SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fde16-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="fde16-122">Большие определяемые пользователем типы</span><span class="sxs-lookup"><span data-stu-id="fde16-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="fde16-123">Демонстрируется извлечение данных из определяемых пользователем типов данных большого размера, появившихся в SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fde16-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="fde16-124">Данные XML в SQL Server</span><span class="sxs-lookup"><span data-stu-id="fde16-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="fde16-125">Описание работы с данными XML, извлеченными из SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fde16-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fde16-126">Ссылка</span><span class="sxs-lookup"><span data-stu-id="fde16-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="fde16-127">Описывает класс `DataSet` и все его члены.</span><span class="sxs-lookup"><span data-stu-id="fde16-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="fde16-128">Описывает пространство имен `SqlTypes` и все его элементы.</span><span class="sxs-lookup"><span data-stu-id="fde16-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="fde16-129">Описывает перечисление `SqlDbType` и все его члены.</span><span class="sxs-lookup"><span data-stu-id="fde16-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="fde16-130">Описывает перечисление `DbType` и все его члены.</span><span class="sxs-lookup"><span data-stu-id="fde16-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde16-131">См. также</span><span class="sxs-lookup"><span data-stu-id="fde16-131">See also</span></span>

- [<span data-ttu-id="fde16-132">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="fde16-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="fde16-133">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="fde16-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="fde16-134">Возвращающие табличное значение параметры</span><span class="sxs-lookup"><span data-stu-id="fde16-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="fde16-135">Двоичные данные и данные большого объема SQL Server</span><span class="sxs-lookup"><span data-stu-id="fde16-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="fde16-136">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fde16-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
