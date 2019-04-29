---
title: Практическое руководство. Отражения в элементе управления данных, которые обновились в источнике, с использованием компонента BindingSource в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 16dbe4da1efecd120d4da4d66c3d79ec907b92a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947996"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="6a23d-102">Практическое руководство. Отражения в элементе управления данных, которые обновились в источнике, с использованием компонента BindingSource в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6a23d-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="6a23d-103">При использовании элементов управления с привязкой к данным иногда необходимо реагировать на изменения в источнике данных, если источник данных не вызывает события изменения списка.</span><span class="sxs-lookup"><span data-stu-id="6a23d-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="6a23d-104">При использовании компонента <xref:System.Windows.Forms.BindingSource> для привязки источника данных к элементу управления Windows Forms можно уведомить элемент управления об изменении источника данных путем вызова метода <xref:System.Windows.Forms.BindingSource.ResetBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a23d-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a23d-105">Пример</span><span class="sxs-lookup"><span data-stu-id="6a23d-105">Example</span></span>  
 <span data-ttu-id="6a23d-106">В следующем примере кода показано использование метода <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> для уведомления связанного элемента управления об изменении в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="6a23d-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a23d-107">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="6a23d-107">Compiling the Code</span></span>  
 <span data-ttu-id="6a23d-108">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="6a23d-108">This example requires:</span></span>  
  
- <span data-ttu-id="6a23d-109">ссылки на сборки System, System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6a23d-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6a23d-110">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6a23d-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6a23d-111">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="6a23d-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a23d-112">См. также</span><span class="sxs-lookup"><span data-stu-id="6a23d-112">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="6a23d-113">Компонент BindingSource</span><span class="sxs-lookup"><span data-stu-id="6a23d-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="6a23d-114">Практическое руководство. Привязка элемента управления Windows Forms к типу</span><span class="sxs-lookup"><span data-stu-id="6a23d-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
