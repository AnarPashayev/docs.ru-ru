---
title: Практическое руководство. Создание в Windows Forms формы для ввода данных, размер которой можно изменять
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 724dfa79358548530eab49683f1cb2db55f889c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625981"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="df5c1-102">Практическое руководство. Создание в Windows Forms формы для ввода данных, размер которой можно изменять</span><span class="sxs-lookup"><span data-stu-id="df5c1-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="df5c1-103">Удачно сконструированный макет должен реагировать на изменение размеров родительской формы.</span><span class="sxs-lookup"><span data-stu-id="df5c1-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="df5c1-104">Для согласованного изменения размера и положения элементов управления на макете формы при изменении размеров формы можно использовать элемент управления <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="df5c1-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="df5c1-105">Элемент управления <xref:System.Windows.Forms.TableLayoutPanel> также полезен в случаях, когда изменение содержимого элементов управления приводит к изменению макета.</span><span class="sxs-lookup"><span data-stu-id="df5c1-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="df5c1-106">Процесс, описанный в этой процедуре, можно выполнить в среде Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df5c1-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="df5c1-107">Также см. в разделе [Пошаговое руководство: Создание переменного размера Windows формы для ввода данных](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="df5c1-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df5c1-108">Пример</span><span class="sxs-lookup"><span data-stu-id="df5c1-108">Example</span></span>  
 <span data-ttu-id="df5c1-109">В следующем примере демонстрируется использование элемента управления <xref:System.Windows.Forms.TableLayoutPanel> для построения макета, который соответствующим образом меняется при изменении пользователем размера формы.</span><span class="sxs-lookup"><span data-stu-id="df5c1-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="df5c1-110">Он также демонстрирует, как макет учитывает будущую локализацию.</span><span class="sxs-lookup"><span data-stu-id="df5c1-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="df5c1-111">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="df5c1-111">Compiling the Code</span></span>  
 <span data-ttu-id="df5c1-112">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="df5c1-112">This example requires:</span></span>  
  
- <span data-ttu-id="df5c1-113">ссылки на сборки System, System.Data, System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="df5c1-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="df5c1-114">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="df5c1-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="df5c1-115">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="df5c1-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5c1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="df5c1-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="df5c1-117">Практическое руководство. Привязка и закрепление дочерних элементов управления в элементе управления TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="df5c1-117">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="df5c1-118">Практическое руководство. Разработка макета формы Windows, с учетом будущей локализации</span><span class="sxs-lookup"><span data-stu-id="df5c1-118">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="df5c1-119">Взаимодействие с пользователем в Microsoft Windows, официальные рекомендации для разработчиков и конструкторов пользовательских интерфейсов. Редмонд, штат Вашингтон: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="df5c1-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
