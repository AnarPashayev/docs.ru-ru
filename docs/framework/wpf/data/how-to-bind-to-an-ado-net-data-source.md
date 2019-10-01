---
title: Практическое руководство. Привязка к источнику данных ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697146"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="65584-102">Практическое руководство. Привязка к источнику данных ADO.NET</span><span class="sxs-lookup"><span data-stu-id="65584-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="65584-103">В этом примере показано, как привязать [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> элемент управления к ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="65584-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="65584-104">Пример</span><span class="sxs-lookup"><span data-stu-id="65584-104">Example</span></span>

<span data-ttu-id="65584-105">В этом примере объект `OleDbConnection` используется для подключения к источнику данных, который представляет собой файл `Access MDB`, указанный в строке подключения.</span><span class="sxs-lookup"><span data-stu-id="65584-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="65584-106">После установления соединения создается объект `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="65584-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="65584-107">Объект `OleDbDataAdapter` выполняет инструкцию SELECT язык SQL (SQL) для получения набора записей из базы данных.</span><span class="sxs-lookup"><span data-stu-id="65584-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="65584-108">Результаты выполнения команды SQL хранятся в `DataTable` `DataSet` путем вызова метода `Fill` `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="65584-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="65584-109">`DataTable` в этом примере назван `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="65584-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="65584-110">Затем в примере задается свойство <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> для объекта `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="65584-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="65584-111">Затем можно привязать свойство <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> к `BookTable` `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="65584-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="65584-112">`BookItemTemplate` — <xref:System.Windows.DataTemplate>, определяющая, как отображаются данные:</span><span class="sxs-lookup"><span data-stu-id="65584-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="65584-113">`IntColorConverter` преобразует `int` в цвет.</span><span class="sxs-lookup"><span data-stu-id="65584-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="65584-114">При использовании этого преобразователя цвет <xref:System.Windows.Controls.TextBlock.Background%2A> третьего <xref:System.Windows.Controls.TextBlock> отображается зеленым, если значение `NumPages` меньше 350 и красный в противном случае.</span><span class="sxs-lookup"><span data-stu-id="65584-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="65584-115">Здесь не приведена реализация преобразователя.</span><span class="sxs-lookup"><span data-stu-id="65584-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="65584-116">См. также</span><span class="sxs-lookup"><span data-stu-id="65584-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="65584-117">Общие сведения о привязке данных</span><span class="sxs-lookup"><span data-stu-id="65584-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="65584-118">Разделы практического руководства</span><span class="sxs-lookup"><span data-stu-id="65584-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
