---
title: Интеграция среды CLR и SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: fd043aa6c7e5b9246a36146e000e5cba9e090d3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297504"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="0e782-102">Интеграция среды CLR и SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e782-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="0e782-103">В версии SQL Server 2005 появилась поддержка интеграции сервера со средой CLR инфраструктуры .NET Framework для Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="0e782-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="0e782-104">Это означает, что хранимые процедуры, триггеры, определяемые пользователем типы, определяемые пользователем функции, определяемые пользователем агрегатные функции и возвращающие табличные значение потоковые функции теперь можно разрабатывать с использованием любого языка .NET Framework, включая Microsoft Visual Basic .NET и Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="0e782-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="0e782-105">Пространство имен <xref:Microsoft.SqlServer.Server> содержит ряд новых API-интерфейсов, что позволяет обеспечить взаимодействие управляемого кода со средой Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0e782-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="0e782-106">В настоящем разделе приведено описание средств и особенностей функционирования, которые появляются в результате интеграции SQL Server со средой CLR, а также внутрипроцессные модули SQL Server, предназначенные для поддержки технологии ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0e782-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="0e782-107">Этот раздел предназначен для предоставления лишь такого количества сведений, с которого можно приступать к программированию в рамках интеграции SQL Server со средой CLR, и не рассчитан на всестороннее изложение.</span><span class="sxs-lookup"><span data-stu-id="0e782-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="0e782-108">Более подробные сведения см. в электронной документации по SQL Server для используемой версии SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0e782-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0e782-109">**Электронная документация по SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0e782-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="0e782-110">Распространенные языка среды CLR Integration основные понятия программирования</span><span class="sxs-lookup"><span data-stu-id="0e782-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="0e782-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="0e782-111">In This Section</span></span>  
 [<span data-ttu-id="0e782-112">Знакомство с интеграцией CLR в SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e782-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="0e782-113">Предоставляет вводные сведения об интеграции SQL Server со средой CLR.</span><span class="sxs-lookup"><span data-stu-id="0e782-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="0e782-114">Приводятся ссылки на дополнительные разделы.</span><span class="sxs-lookup"><span data-stu-id="0e782-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0e782-115">Определяемые пользователем функции среды CLR</span><span class="sxs-lookup"><span data-stu-id="0e782-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="0e782-116">Содержит описание реализации и использования различных типов функций среды CLR: возвращающих табличное значение, скалярных и определяемых пользователем агрегатных функций.</span><span class="sxs-lookup"><span data-stu-id="0e782-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="0e782-117">Определяемые пользователем типы CLR</span><span class="sxs-lookup"><span data-stu-id="0e782-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="0e782-118">Показывает, как реализовать и использовать определяемые пользователем типы среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0e782-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="0e782-119">Приводятся ссылки на дополнительные разделы.</span><span class="sxs-lookup"><span data-stu-id="0e782-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0e782-120">Хранимые процедуры CLR</span><span class="sxs-lookup"><span data-stu-id="0e782-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="0e782-121">Показывает, как реализовать и использовать хранимые процедуры среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0e782-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="0e782-122">Приводятся ссылки на дополнительные разделы.</span><span class="sxs-lookup"><span data-stu-id="0e782-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0e782-123">Триггеры CLR</span><span class="sxs-lookup"><span data-stu-id="0e782-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="0e782-124">Показывает, как реализовать и использовать триггеры CLR.</span><span class="sxs-lookup"><span data-stu-id="0e782-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="0e782-125">Приводятся ссылки на дополнительные разделы.</span><span class="sxs-lookup"><span data-stu-id="0e782-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0e782-126">Подключение контекста</span><span class="sxs-lookup"><span data-stu-id="0e782-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="0e782-127">Описывает контекстное соединение.</span><span class="sxs-lookup"><span data-stu-id="0e782-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="0e782-128">Внутрипроцессное поведение ADO.NET в SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e782-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="0e782-129">Описывает внутрипроцессные модули SQL Server, предназначенные для поддержки технологии ADO.NET, и контекстное соединение.</span><span class="sxs-lookup"><span data-stu-id="0e782-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="0e782-130">Приводятся ссылки на дополнительные разделы.</span><span class="sxs-lookup"><span data-stu-id="0e782-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e782-131">См. также</span><span class="sxs-lookup"><span data-stu-id="0e782-131">See also</span></span>

- [<span data-ttu-id="0e782-132">SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e782-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="0e782-133">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e782-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
