---
title: Практическое руководство. Отображение содержимого элемента управления ListView в Windows Forms в виде мозаичного представления
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966681"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="3ed1a-102">Практическое руководство. Отображение содержимого элемента управления ListView в Windows Forms в виде мозаичного представления</span><span class="sxs-lookup"><span data-stu-id="3ed1a-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="3ed1a-103">Функция мозаичного представления элемента управления <xref:System.Windows.Forms.ListView> обеспечивает визуальный баланс между графическими и текстовыми представлениями информации.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="3ed1a-104">Текстовые данные, отображаемые для мозаичного представления элемента совпадают с данными о столбцах, определенных для подробного представления.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="3ed1a-105">Мозаичное представление работает в сочетании с возможностями группирования или вставки метки элемента управления <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="3ed1a-106">Мозаичное представление использует значок размером 32 x 32 пикселя и несколько строк текста, как показано на следующих рисунках.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="3ed1a-107">![Мозаичное представление в элементе управления ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Значки и текст мозаичного представления")</span><span class="sxs-lookup"><span data-stu-id="3ed1a-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="3ed1a-108">Чтобы включить мозаичное представление, присвойте свойству <xref:System.Windows.Forms.ListView.View%2A> значение <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="3ed1a-109">Размер элементов мозаики можно настроить, задав свойство <xref:System.Windows.Forms.ListView.TileSize%2A> и количество отображаемых строк текста в плитке путем настройки коллекции <xref:System.Windows.Forms.ListView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ed1a-110">Функция мозаичного представления доступна только в [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)], когда приложение вызывает метод <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3ed1a-111">В предыдущих версиях операционных систем код, связанный с мозаичным представлением, не оказывает никакого влияния, элемент управления <xref:System.Windows.Forms.ListView> отображается в представлении крупных значков.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="3ed1a-112">Дополнительные сведения см. в разделе <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="3ed1a-113">Выбор мозаичного представления программными средствами</span><span class="sxs-lookup"><span data-stu-id="3ed1a-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="3ed1a-114">Используйте перечисление <xref:System.Windows.Forms.View> элемента управления <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="3ed1a-115">Пример</span><span class="sxs-lookup"><span data-stu-id="3ed1a-115">Example</span></span>  
 <span data-ttu-id="3ed1a-116">В завершенном примере кода ниже показано мозаичное представление с плиткой, в которой отображаются три строки текста.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="3ed1a-117">Размер мозаики был подобран для предотвращения переноса строк.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ed1a-118">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="3ed1a-118">Compiling the Code</span></span>  
 <span data-ttu-id="3ed1a-119">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="3ed1a-119">This example requires:</span></span>  
  
- <span data-ttu-id="3ed1a-120">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="3ed1a-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="3ed1a-121">файл значка с именем book.ico в том же каталоге, что и исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="3ed1a-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed1a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3ed1a-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="3ed1a-123">Элемент управления ListView</span><span class="sxs-lookup"><span data-stu-id="3ed1a-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="3ed1a-124">Общие сведения об элементе управления ListView</span><span class="sxs-lookup"><span data-stu-id="3ed1a-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
