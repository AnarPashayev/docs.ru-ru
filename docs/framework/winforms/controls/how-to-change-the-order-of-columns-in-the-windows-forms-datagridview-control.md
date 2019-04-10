---
title: Практическое руководство. Изменение порядка столбцов элемента управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 90d262e738f092215e88e38e31169d74059e4401
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228800"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bc47e-102">Практическое руководство. Изменение порядка столбцов элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc47e-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bc47e-103">При использовании <xref:System.Windows.Forms.DataGridView> для отображения данных из источника данных столбцы в схеме данных не всегда выводятся в нужном порядке.</span><span class="sxs-lookup"><span data-stu-id="bc47e-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="bc47e-104">Порядок отображения столбцов можно изменить с помощью свойства <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> класса <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="bc47e-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="bc47e-105">В примере кода ниже изменяется положение некоторых столбцов, автоматически созданных при привязке к таблице Customers в базе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="bc47e-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="bc47e-106">Дополнительные сведения о том, как привязать <xref:System.Windows.Forms.DataGridView> управления с таблицей базы данных, см. в разделе [как: Привязка данных к Windows Forms элемента управления DataGridView](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bc47e-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="bc47e-107">Эта задача поддерживается в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc47e-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="bc47e-108">Также см. раздел [Как Изменить порядок столбцов в элементе управления DataGridView формы Windows с помощью конструктора](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="bc47e-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc47e-109">Пример</span><span class="sxs-lookup"><span data-stu-id="bc47e-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc47e-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="bc47e-110">Compiling the Code</span></span>  
 <span data-ttu-id="bc47e-111">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="bc47e-111">This example requires:</span></span>  
  
-   <span data-ttu-id="bc47e-112">элемент управления <xref:System.Windows.Forms.DataGridView> с именем `customersDataGridView`, связанный с таблицей с указанными именами столбцов, например с таблицей `Customers` базы данных Northwind;</span><span class="sxs-lookup"><span data-stu-id="bc47e-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="bc47e-113">ссылки на сборки <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType> и <xref:System.Xml?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bc47e-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc47e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="bc47e-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc47e-115">Отображение данных с помощью элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc47e-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bc47e-116">Практическое руководство. Привязка данных к элементу управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc47e-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
