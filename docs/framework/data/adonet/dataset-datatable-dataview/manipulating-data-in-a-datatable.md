---
title: Управление данными в таблице данных
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 96be67859d9fd136d7ad370ae06d9fcf33426f53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202577"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="cc956-102">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="cc956-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="cc956-103">После создания объекта <xref:System.Data.DataTable> в объекте <xref:System.Data.DataSet> можно выполнять такие же действия, как и при использовании таблицы в базе данных.</span><span class="sxs-lookup"><span data-stu-id="cc956-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="cc956-104">Можно добавлять, просматривать, изменять и удалять данные в таблице. Можно отслеживать ошибки и события; кроме того, можно запрашивать находящиеся в таблице данные.</span><span class="sxs-lookup"><span data-stu-id="cc956-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="cc956-105">При изменении данных в **DataTable**, также можно проверить правильность изменений и определить, программно принять или отклонить изменения.</span><span class="sxs-lookup"><span data-stu-id="cc956-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc956-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="cc956-106">In This Section</span></span>  
 [<span data-ttu-id="cc956-107">Добавление данных в DataTable</span><span class="sxs-lookup"><span data-stu-id="cc956-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="cc956-108">Рассказывает, как создавать новые строки и добавлять их в таблицу.</span><span class="sxs-lookup"><span data-stu-id="cc956-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="cc956-109">Просмотр данных в DataTable</span><span class="sxs-lookup"><span data-stu-id="cc956-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="cc956-110">Описывает, как получать доступ к данным в строке, включая исходную и текущую версии данных.</span><span class="sxs-lookup"><span data-stu-id="cc956-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="cc956-111">Метод Load</span><span class="sxs-lookup"><span data-stu-id="cc956-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="cc956-112">Описание использования **нагрузки** метод для заполнения **DataTable** со строками.</span><span class="sxs-lookup"><span data-stu-id="cc956-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="cc956-113">Редактирование DataTable</span><span class="sxs-lookup"><span data-stu-id="cc956-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="cc956-114">Рассказывает, как изменять данные в строке, в том числе приостанавливать внесение изменений в строку, пока предложенные изменения не будут проверены и приняты.</span><span class="sxs-lookup"><span data-stu-id="cc956-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="cc956-115">Состояния и версии строк</span><span class="sxs-lookup"><span data-stu-id="cc956-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="cc956-116">Приводит сведения о разных состояниях строки.</span><span class="sxs-lookup"><span data-stu-id="cc956-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="cc956-117">Удаление DataRow</span><span class="sxs-lookup"><span data-stu-id="cc956-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="cc956-118">Описывает, как удалять строку из таблицы.</span><span class="sxs-lookup"><span data-stu-id="cc956-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="cc956-119">Сведения об ошибках строк</span><span class="sxs-lookup"><span data-stu-id="cc956-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="cc956-120">Объясняет, как вставлять сведения об ошибках по одной строке, чтобы способствовать разрешению проблем с данными в приложении.</span><span class="sxs-lookup"><span data-stu-id="cc956-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="cc956-121">AcceptChanges и RejectChanges</span><span class="sxs-lookup"><span data-stu-id="cc956-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="cc956-122">Объясняет, как принимать или отклонять внесенные в строку изменения.</span><span class="sxs-lookup"><span data-stu-id="cc956-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc956-123">См. также</span><span class="sxs-lookup"><span data-stu-id="cc956-123">See also</span></span>

- [<span data-ttu-id="cc956-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="cc956-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="cc956-125">Обработка событий DataTable</span><span class="sxs-lookup"><span data-stu-id="cc956-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="cc956-126">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cc956-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
