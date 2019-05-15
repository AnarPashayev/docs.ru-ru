---
title: Практическое руководство. Доступ к связанным объектам в строках DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 244047f27b0eb109aba599bd26881046eb538163
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582620"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="21e28-102">Практическое руководство. Доступ к связанным объектам в строках DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21e28-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="21e28-103">Иногда полезно отображать таблицу данных, которые хранятся в коллекции бизнес-объектов.</span><span class="sxs-lookup"><span data-stu-id="21e28-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="21e28-104">При привязке элемента управления <xref:System.Windows.Forms.DataGridView> к такого рода коллекции каждое открытое свойство отображается в собственном столбце, если только оно не помечено как недоступное для просмотра с помощью <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="21e28-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="21e28-105">Например, коллекция объектов `Customer` будет содержать такие столбцы, как **Имя** и **Адрес**.</span><span class="sxs-lookup"><span data-stu-id="21e28-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="21e28-106">Если такие объекты содержат дополнительную информацию и код, к которым требуется доступ, можно использовать объекты строк.</span><span class="sxs-lookup"><span data-stu-id="21e28-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="21e28-107">В примере кода ниже пользователи могут выбрать несколько строк и отправить счета каждому из соответствующих клиентов путем нажатия на кнопку.</span><span class="sxs-lookup"><span data-stu-id="21e28-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="21e28-108">Получение доступа к объектам, связанным со строками</span><span class="sxs-lookup"><span data-stu-id="21e28-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="21e28-109">Используйте свойство <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21e28-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="21e28-110">Пример</span><span class="sxs-lookup"><span data-stu-id="21e28-110">Example</span></span>  
 <span data-ttu-id="21e28-111">Полный пример кода включает в себя простую реализацию `Customer` и связывает <xref:System.Windows.Forms.DataGridView> со списком <xref:System.Collections.ArrayList>, содержащим несколько объектов `Customer`.</span><span class="sxs-lookup"><span data-stu-id="21e28-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="21e28-112">Доступ обработчика событий <xref:System.Windows.Forms.Control.Click> элемента <xref:System.Windows.Forms.Button?displayProperty=nameWithType> к объектам `Customer` должен осуществляться через строки, так как коллекция клиентов недоступна вне обработчика событий <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21e28-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21e28-113">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="21e28-113">Compiling the Code</span></span>  
 <span data-ttu-id="21e28-114">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="21e28-114">This example requires:</span></span>  
  
- <span data-ttu-id="21e28-115">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="21e28-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e28-116">См. также</span><span class="sxs-lookup"><span data-stu-id="21e28-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="21e28-117">Отображение данных с помощью элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21e28-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="21e28-118">Практическое руководство. Привязка объектов к элементам управления DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21e28-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
