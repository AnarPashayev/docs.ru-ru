---
title: Практическое руководство. Заключение элемента управления в оболочку ToolStripControlHost в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: 6335d09a89225ae1e202a781a73bfd149608f5fc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364186"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="2c19e-102">Практическое руководство. Заключение элемента управления в оболочку ToolStripControlHost в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c19e-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="2c19e-103"><xref:System.Windows.Forms.ToolStripControlHost> обеспечивает возможность размещения произвольных элементов управления Windows Forms с помощью конструктора <xref:System.Windows.Forms.ToolStripControlHost> или путем расширения самого <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="2c19e-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="2c19e-104">Создавать оболочку для элемента управления проще путем расширения <xref:System.Windows.Forms.ToolStripControlHost> и реализации свойств и методов, которые будут предоставлять часто используемые свойства и методы элемента управления.</span><span class="sxs-lookup"><span data-stu-id="2c19e-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="2c19e-105">Можно также обеспечить доступ к событиям для элемента управления на уровне <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="2c19e-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="2c19e-106">Размещение элемента управления в ToolStripControlHost путем наследования</span><span class="sxs-lookup"><span data-stu-id="2c19e-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="2c19e-107">Расширьте <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="2c19e-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="2c19e-108">Реализуйте конструктор без параметров, который вызывает конструктор базового класса, передавая нужный элемент управления.</span><span class="sxs-lookup"><span data-stu-id="2c19e-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="2c19e-109">Объявите свойство с типом, совпадающим с типом оболочки элемента управления и возвращающее `Control` в качестве корректного типа элемента управления в методе доступа для свойства.</span><span class="sxs-lookup"><span data-stu-id="2c19e-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="2c19e-110">Обеспечьте доступ к часто используемым свойствам и методам оболочки элемента управления, реализовав свойства и метода в расширенном классе.</span><span class="sxs-lookup"><span data-stu-id="2c19e-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="2c19e-111">При необходимости переопределите методы <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A> и <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> и добавьте события элемента управления, к которому требуется предоставить доступ.</span><span class="sxs-lookup"><span data-stu-id="2c19e-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="2c19e-112">Создайте необходимую оболочку для событий, доступ к которым требуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="2c19e-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="2c19e-113">Пример</span><span class="sxs-lookup"><span data-stu-id="2c19e-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2c19e-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="2c19e-114">Compiling the Code</span></span>  
  
<span data-ttu-id="2c19e-115">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="2c19e-115">This example requires:</span></span>
  
- <span data-ttu-id="2c19e-116">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="2c19e-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c19e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2c19e-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="2c19e-118">Общие сведения об элементе управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2c19e-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="2c19e-119">Архитектура элемента управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2c19e-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="2c19e-120">Технологии, положенные в основу работы элемента управления ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2c19e-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
