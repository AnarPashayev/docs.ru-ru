---
title: Практическое руководство. Совместное использование одних и тех же данных в нескольких формах посредством компонента BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: 026b5456134be531b05e75474bcad6bbd46dc7fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630464"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="4b90b-102">Практическое руководство. Совместное использование одних и тех же данных в нескольких формах посредством компонента BindingSource</span><span class="sxs-lookup"><span data-stu-id="4b90b-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="4b90b-103">С помощью компонента <xref:System.Windows.Forms.BindingSource> одни и те же данные можно легко использовать в нескольких формах.</span><span class="sxs-lookup"><span data-stu-id="4b90b-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="4b90b-104">Например, может потребоваться отобразить одну форму только для чтения со сводкой данных и другую редактируемую форму с подробными сведениями о выбранном в данный момент элементе в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="4b90b-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="4b90b-105">В этом примере демонстрируется такая возможность.</span><span class="sxs-lookup"><span data-stu-id="4b90b-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b90b-106">Пример</span><span class="sxs-lookup"><span data-stu-id="4b90b-106">Example</span></span>  
 <span data-ttu-id="4b90b-107">В примере кода ниже показано, как совместно использовать источник <xref:System.Windows.Forms.BindingSource> и связанные с ним данные в разных формах.</span><span class="sxs-lookup"><span data-stu-id="4b90b-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="4b90b-108">В этом примере общий источник <xref:System.Windows.Forms.BindingSource> передается в конструктор дочерней формы.</span><span class="sxs-lookup"><span data-stu-id="4b90b-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="4b90b-109">Дочерняя форма позволяет пользователю изменять данные элемента, выбранного в настоящий момент в главной форме.</span><span class="sxs-lookup"><span data-stu-id="4b90b-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b90b-110">В этом примере обрабатывается событие <xref:System.Windows.Forms.BindingSource.BindingComplete> для компонента <xref:System.Windows.Forms.BindingSource>, обеспечивая синхронизацию двух форм.</span><span class="sxs-lookup"><span data-stu-id="4b90b-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="4b90b-111">Дополнительные сведения о том, почему это делать, см. в разделе [как: Элементов управления с привязкой к тому же источнику данных будут синхронизированы](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="4b90b-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b90b-112">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="4b90b-112">Compiling the Code</span></span>  
 <span data-ttu-id="4b90b-113">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="4b90b-113">This example requires:</span></span>  
  
- <span data-ttu-id="4b90b-114">Ссылки на сборки System, System.Windows.Forms, System.Drawing, System.Data и System.Xml.</span><span class="sxs-lookup"><span data-stu-id="4b90b-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="4b90b-115">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b90b-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4b90b-116">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="4b90b-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b90b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4b90b-117">See also</span></span>

- [<span data-ttu-id="4b90b-118">Компонент BindingSource</span><span class="sxs-lookup"><span data-stu-id="4b90b-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="4b90b-119">Привязка данных Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b90b-119">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="4b90b-120">Практическое руководство. Обработка ошибок и исключений, происходящих при выполнении привязки данных</span><span class="sxs-lookup"><span data-stu-id="4b90b-120">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
