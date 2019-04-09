---
title: Практическое руководство. Разрешение переупорядочивания столбцов элемента управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 625c4987a45ed3749284e7abc7b6cde6d24821ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161477"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="54f11-102">Практическое руководство. Разрешение переупорядочивания столбцов элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54f11-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="54f11-103">При разрешении изменения порядка столбцов в элементе управления <xref:System.Windows.Forms.DataGridView> пользователи могут переместить столбец в новое местоположение, перетащив заголовок столбца с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="54f11-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="54f11-104">В элементе управления <xref:System.Windows.Forms.DataGridView> значение свойства <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> определяет, могут ли пользователи перемещать столбцы.</span><span class="sxs-lookup"><span data-stu-id="54f11-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="54f11-105">Эта задача поддерживается в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="54f11-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="54f11-106">Также см. раздел [Как Включить изменение порядка столбцов в Windows Forms с помощью конструктора элемента управления DataGridView](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="54f11-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="54f11-107">Разрешение изменения порядка столбцов программным путем</span><span class="sxs-lookup"><span data-stu-id="54f11-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="54f11-108">Задайте для свойства <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="54f11-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54f11-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="54f11-109">Compiling the Code</span></span>  
 <span data-ttu-id="54f11-110">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="54f11-110">This example requires:</span></span>  
  
-   <span data-ttu-id="54f11-111">элемент управления <xref:System.Windows.Forms.DataGridView> с именем `dataGridView1`;</span><span class="sxs-lookup"><span data-stu-id="54f11-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="54f11-112">ссылки на сборки <xref:System?displayProperty=nameWithType> и <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54f11-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f11-113">См. также</span><span class="sxs-lookup"><span data-stu-id="54f11-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="54f11-114">Базовые характеристики столбцов, строк и ячеек элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54f11-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="54f11-115">Практическое руководство. Замораживание столбцов элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54f11-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
