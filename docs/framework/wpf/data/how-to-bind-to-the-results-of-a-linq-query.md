---
title: Практическое руководство. Привязка к результатам запроса LINQ
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 5464ee9c59a7c99a83774a7535b9b3c422c1d2e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185904"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="11fa4-102">Практическое руководство. Привязка к результатам запроса LINQ</span><span class="sxs-lookup"><span data-stu-id="11fa4-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="11fa4-103">В этом примере показано, как выполнить запрос LINQ, а затем привязать к результатам.</span><span class="sxs-lookup"><span data-stu-id="11fa4-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11fa4-104">Пример</span><span class="sxs-lookup"><span data-stu-id="11fa4-104">Example</span></span>  
 <span data-ttu-id="11fa4-105">В следующем примере создается два окна.</span><span class="sxs-lookup"><span data-stu-id="11fa4-105">The following example creates two list boxes.</span></span> <span data-ttu-id="11fa4-106">Первый список содержит три элемента списка.</span><span class="sxs-lookup"><span data-stu-id="11fa4-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="11fa4-107">Выбор элемента из первого списка вызывает следующий обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="11fa4-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="11fa4-108">В этом примере `Tasks` — это коллекция `Task` объектов.</span><span class="sxs-lookup"><span data-stu-id="11fa4-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="11fa4-109">`Task` Класс имеет свойство с именем `Priority`.</span><span class="sxs-lookup"><span data-stu-id="11fa4-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="11fa4-110">Этот обработчик событий запускает запрос LINQ, возвращающий коллекцию `Task` объекты, которые имеют значение выбранного приоритета, а затем устанавливает его в качестве <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="11fa4-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="11fa4-111">Второй список привязывается к этой коллекции, так как его <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> имеет значение `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="11fa4-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="11fa4-112">Таким образом, он отображает возвращаемой коллекции (на основе `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="11fa4-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fa4-113">См. также</span><span class="sxs-lookup"><span data-stu-id="11fa4-113">See also</span></span>

- [<span data-ttu-id="11fa4-114">Обеспечение доступности данных для привязки в XAML</span><span class="sxs-lookup"><span data-stu-id="11fa4-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="11fa4-115">Привязка к коллекции и вывод сведений в зависимости от выделенного элемента</span><span class="sxs-lookup"><span data-stu-id="11fa4-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="11fa4-116">Новые возможности WPF версии 4.5</span><span class="sxs-lookup"><span data-stu-id="11fa4-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="11fa4-117">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="11fa4-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="11fa4-118">Практические руководства</span><span class="sxs-lookup"><span data-stu-id="11fa4-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
