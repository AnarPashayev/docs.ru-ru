---
title: Практическое руководство. Группирование элементов в элементе управления ListView в формах Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 3a070db6c580f0f3798e52b1afbe0ee36947aeb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091542"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="7302a-102">Практическое руководство. Группирование элементов в элементе управления ListView в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7302a-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7302a-103">Функция группирования из <xref:System.Windows.Forms.ListView> элемента управления, можно отобразить соответствующие наборы элементов в группах.</span><span class="sxs-lookup"><span data-stu-id="7302a-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="7302a-104">Эти группы, разделенных на экране группу горизонтальных заголовков, содержащих заголовки групп.</span><span class="sxs-lookup"><span data-stu-id="7302a-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="7302a-105">Можно использовать <xref:System.Windows.Forms.ListView> группы для упрощения просмотра больших списков, сгруппировав элементы по алфавиту, по дате или по другим критериям.</span><span class="sxs-lookup"><span data-stu-id="7302a-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="7302a-106">На следующем рисунке показана некоторые сгруппированных элементов.</span><span class="sxs-lookup"><span data-stu-id="7302a-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="7302a-107">![Группы ListView](./media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="7302a-107">![ListView Groups](./media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="7302a-108">ListView сгруппированные элементы</span><span class="sxs-lookup"><span data-stu-id="7302a-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="7302a-109">Чтобы включить группирования, сначала необходимо создать одну или несколько групп, либо в конструкторе, либо программным способом.</span><span class="sxs-lookup"><span data-stu-id="7302a-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="7302a-110">После определения группы можно назначить <xref:System.Windows.Forms.ListView> элементы в группу.</span><span class="sxs-lookup"><span data-stu-id="7302a-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="7302a-111">Вы также можно перемещать элементы из одной группы в другую программным способом.</span><span class="sxs-lookup"><span data-stu-id="7302a-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> <span data-ttu-id="7302a-112">группы доступны только на [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] когда приложение вызывает <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="7302a-112">groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7302a-113">В предыдущих версиях операционных систем любой код, относящийся к группам не влияет, и группы не будут.</span><span class="sxs-lookup"><span data-stu-id="7302a-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="7302a-114">Дополнительные сведения см. в разделе <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7302a-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="7302a-115">Чтобы добавить группы</span><span class="sxs-lookup"><span data-stu-id="7302a-115">To add groups</span></span>  
  
1.  <span data-ttu-id="7302a-116">Используйте метод <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> коллекции <xref:System.Windows.Forms.ListView.Groups%2A> .</span><span class="sxs-lookup"><span data-stu-id="7302a-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="7302a-117">Удаление групп</span><span class="sxs-lookup"><span data-stu-id="7302a-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="7302a-118">Используйте <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> или <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> метод <xref:System.Windows.Forms.ListView.Groups%2A> коллекции.</span><span class="sxs-lookup"><span data-stu-id="7302a-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="7302a-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Метод удаляет одну группу; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> метод удаляет все группы из списка.</span><span class="sxs-lookup"><span data-stu-id="7302a-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7302a-120">Удаление группы не приводит к удалению элементов в этой группе.</span><span class="sxs-lookup"><span data-stu-id="7302a-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="7302a-121">Чтобы назначить группам элементов или перемещать элементы между группами</span><span class="sxs-lookup"><span data-stu-id="7302a-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="7302a-122">Задать <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> свойства отдельных элементов.</span><span class="sxs-lookup"><span data-stu-id="7302a-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7302a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="7302a-123">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="7302a-124">Элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="7302a-124">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7302a-125">Общие сведения об элементе управления ListView</span><span class="sxs-lookup"><span data-stu-id="7302a-125">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7302a-126">Практическое руководство. Добавление и удаление элементов с помощью элемента управления ListView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7302a-126">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
