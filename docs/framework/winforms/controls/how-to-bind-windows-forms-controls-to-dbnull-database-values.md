---
title: Практическое руководство. Привязка элементов управления Windows Forms к значениям DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: cc3dde0db3dad6faff548951ff06a39d23248d53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666564"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="24f5d-102">Практическое руководство. Привязка элементов управления Windows Forms к значениям DBNull</span><span class="sxs-lookup"><span data-stu-id="24f5d-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="24f5d-103">Если элементы управления Windows Forms привязаны к источнику данных и источник данных возвращает значение <xref:System.DBNull>, соответствующее значение можно заменить без обработки, форматирования или анализа событий.</span><span class="sxs-lookup"><span data-stu-id="24f5d-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="24f5d-104">Свойство <xref:System.Windows.Forms.Binding.NullValue%2A> преобразует <xref:System.DBNull> в указанный объект при форматировании или анализе значений источника данных.</span><span class="sxs-lookup"><span data-stu-id="24f5d-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f5d-105">Пример</span><span class="sxs-lookup"><span data-stu-id="24f5d-105">Example</span></span>  
 <span data-ttu-id="24f5d-106">В примере ниже демонстрируется привязка значения <xref:System.DBNull> в двух разных случаях.</span><span class="sxs-lookup"><span data-stu-id="24f5d-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="24f5d-107">В первом случае показано, как задать <xref:System.Windows.Forms.Binding.NullValue%2A> для свойства строки; во втором — как задать <xref:System.Windows.Forms.Binding.NullValue%2A> для свойства изображения.</span><span class="sxs-lookup"><span data-stu-id="24f5d-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="24f5d-108">Типы связанного свойства и свойства <xref:System.Windows.Forms.Binding.NullValue%2A> должны быть одинаковыми, иначе произойдет ошибка и следующие значения <xref:System.Windows.Forms.Binding.NullValue%2A> обрабатываться не будут.</span><span class="sxs-lookup"><span data-stu-id="24f5d-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="24f5d-109">В этом случае исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="24f5d-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24f5d-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="24f5d-110">Compiling the Code</span></span>  
 <span data-ttu-id="24f5d-111">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="24f5d-111">This example requires:</span></span>  
  
- <span data-ttu-id="24f5d-112">ссылки на сборки System, System.Data, System.Drawing и System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="24f5d-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="24f5d-113">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="24f5d-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="24f5d-114">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="24f5d-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f5d-115">См. также</span><span class="sxs-lookup"><span data-stu-id="24f5d-115">See also</span></span>

- [<span data-ttu-id="24f5d-116">Компонент BindingSource</span><span class="sxs-lookup"><span data-stu-id="24f5d-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="24f5d-117">Практическое руководство. Обработка ошибок и исключений, происходящих при выполнении привязки данных</span><span class="sxs-lookup"><span data-stu-id="24f5d-117">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="24f5d-118">Практическое руководство. Привязка элемента управления Windows Forms к типу</span><span class="sxs-lookup"><span data-stu-id="24f5d-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
