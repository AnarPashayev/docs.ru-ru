---
title: Объекты DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607871"
---
# <a name="datatablereaders"></a><span data-ttu-id="dc45b-102">Объекты DataTableReader</span><span class="sxs-lookup"><span data-stu-id="dc45b-102">DataTableReaders</span></span>
<span data-ttu-id="dc45b-103"><xref:System.Data.DataTableReader> представляет содержимое объекта <xref:System.Data.DataTable> или <xref:System.Data.DataSet> в виде одного или нескольких результирующих наборов, предназначенных только для чтения и только для перенаправления.</span><span class="sxs-lookup"><span data-stu-id="dc45b-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="dc45b-104">При создании **DataTableReader** из **DataTable**, полученный в результате **DataTableReader** объект содержит один результирующий набор с теми же данными, как  **DataTable** из которого он был создан, за исключением любых строк, которые были помечены как удаленные.</span><span class="sxs-lookup"><span data-stu-id="dc45b-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="dc45b-105">Столбцы отображаются в том же порядке, как и в исходном **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="dc45b-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="dc45b-106">Объект **DataTableReader** может содержать несколько результирующих наборов, если он был создан путем вызова <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc45b-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="dc45b-107">Результаты отображаются в том же порядке **DataTables** в **набора данных** объекта <xref:System.Data.DataSet.Tables%2A> коллекции.</span><span class="sxs-lookup"><span data-stu-id="dc45b-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc45b-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="dc45b-108">In This Section</span></span>  
 [<span data-ttu-id="dc45b-109">Создание объекта DataReader</span><span class="sxs-lookup"><span data-stu-id="dc45b-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="dc45b-110">Рассматривается процесс создания **DataTableReader** объекта.</span><span class="sxs-lookup"><span data-stu-id="dc45b-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="dc45b-111">Навигация в объектах DataTable</span><span class="sxs-lookup"><span data-stu-id="dc45b-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="dc45b-112">Описание использования **чтения** метод для перехода по содержимому объекта **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="dc45b-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc45b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="dc45b-113">See also</span></span>

- [<span data-ttu-id="dc45b-114">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc45b-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="dc45b-115">Центр разработчиков наборов данных и управляемых поставщиков ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc45b-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
