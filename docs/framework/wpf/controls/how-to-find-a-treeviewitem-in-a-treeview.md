---
title: Практическое руководство. Поиск элемента TreeViewItem в TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219048"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="099a6-102">Практическое руководство. Поиск элемента TreeViewItem в TreeView</span><span class="sxs-lookup"><span data-stu-id="099a6-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="099a6-103"><xref:System.Windows.Controls.TreeView> Элемент управления предоставляет удобный способ отображения иерархических данных.</span><span class="sxs-lookup"><span data-stu-id="099a6-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="099a6-104">Если ваш <xref:System.Windows.Controls.TreeView> привязан к источнику данных <xref:System.Windows.Controls.TreeView.SelectedItem%2A> свойство предоставляет удобный способ для быстрого извлечения выбранного объекта данных.</span><span class="sxs-lookup"><span data-stu-id="099a6-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="099a6-105">Обычно лучше всего работать с основной объект данных, но иногда необходимо программно управлять данных, содержащий <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="099a6-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="099a6-106">Например, может потребоваться программным образом развернуть <xref:System.Windows.Controls.TreeViewItem>, или выберите другой элемент в <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="099a6-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="099a6-107">Чтобы найти <xref:System.Windows.Controls.TreeViewItem> , содержащий конкретный объект данных, необходимо пройти каждый уровень <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="099a6-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="099a6-108">Элементы в <xref:System.Windows.Controls.TreeView> также могут быть виртуализированы для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="099a6-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="099a6-109">В случае, когда виртуализации элементов, необходимо также реализовать <xref:System.Windows.Controls.TreeViewItem> для проверки, содержит ли объект данных.</span><span class="sxs-lookup"><span data-stu-id="099a6-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="099a6-110">Пример</span><span class="sxs-lookup"><span data-stu-id="099a6-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="099a6-111">Описание</span><span class="sxs-lookup"><span data-stu-id="099a6-111">Description</span></span>  
 <span data-ttu-id="099a6-112">В следующем примере производится поиск <xref:System.Windows.Controls.TreeView> для определенного объекта и возвращает, содержащий этот объект <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="099a6-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="099a6-113">В примере проверяется, чтобы каждый <xref:System.Windows.Controls.TreeViewItem> создается таким образом, чтобы поиска дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="099a6-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="099a6-114">В этом примере также работает, если <xref:System.Windows.Controls.TreeView> используются виртуализированные элементы.</span><span class="sxs-lookup"><span data-stu-id="099a6-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="099a6-115">Следующий пример работает для любого <xref:System.Windows.Controls.TreeView>, вне зависимости от базовой модели данных и выполняет каждый <xref:System.Windows.Controls.TreeViewItem> пока не будет найден объект.</span><span class="sxs-lookup"><span data-stu-id="099a6-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="099a6-116">Другой метод, имеющий более высокую производительность заключается поиск модели данных для указанного объекта, отслеживать его положение в иерархии данных и затем найти соответствующий <xref:System.Windows.Controls.TreeViewItem> в <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="099a6-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="099a6-117">Тем не менее, метод, имеющий более высокую производительность требует знаний модели данных и не может быть обобщить для любого заданного <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="099a6-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="099a6-118">Код</span><span class="sxs-lookup"><span data-stu-id="099a6-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="099a6-119">Предыдущий код использует пользовательский <xref:System.Windows.Controls.VirtualizingStackPanel> , предоставляет метод с именем `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="099a6-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="099a6-120">Следующий код определяет пользовательский <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="099a6-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="099a6-121">Следующий XAML показан способ создания <xref:System.Windows.Controls.TreeView> , использующего пользовательский <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="099a6-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="099a6-122">См. также</span><span class="sxs-lookup"><span data-stu-id="099a6-122">See also</span></span>

- [<span data-ttu-id="099a6-123">Повышение производительности элемента управления TreeView</span><span class="sxs-lookup"><span data-stu-id="099a6-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
