---
title: Практическое руководство. Наследование форм Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 0d8799359a12b9bb64331d83df2500bede8c0ff2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314548"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="d1a3a-102">Практическое руководство. Наследование форм Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1a3a-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="d1a3a-103">Создание новых форм Windows Forms путем наследования базовых форм является удобным способом для дублирования уже созданного, минуя процесс повторного создания формы с нуля каждый раз, когда она необходима.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="d1a3a-104">Дополнительные сведения о наследовании форм во время разработки с помощью **Выбор компонентов для наследования** диалоговое окно и как визуально различать уровни безопасности производных элементов управления, см. в разделе [как: Наследование форм с помощью диалогового окна выбора наследования](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="d1a3a-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="d1a3a-105">**Примечание** Чтобы произвести наследование от формы, файл или пространство имен, содержащие форму, должны быть встроены в исполняемый файл или библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="d1a3a-106">Для сборки проекта выберите в меню **Сборка** пункт **Собрать**.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="d1a3a-107">Кроме того необходимо добавить ссылку на пространство имен к классу, наследующему форму.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="d1a3a-108">Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d1a3a-109">Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** .</span><span class="sxs-lookup"><span data-stu-id="d1a3a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d1a3a-110">Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d1a3a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="d1a3a-111">Наследование формы программными средствами</span><span class="sxs-lookup"><span data-stu-id="d1a3a-111">To inherit a form programmatically</span></span>  
  
1. <span data-ttu-id="d1a3a-112">В классе добавьте ссылку на пространство имен, содержащее форму, которую вы хотите наследовать.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2. <span data-ttu-id="d1a3a-113">В определении класса добавьте ссылку на форму для наследования.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="d1a3a-114">Ссылка должна содержать пространство имен, в котором содержится форма, точку, а затем имя базовой формы.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="d1a3a-115">При наследовании форм следует помнить, что могут возникнуть проблемы с обработчиками событий, которые вызываются дважды, так как каждое событие обрабатывается базовым классом и производным классом.</span><span class="sxs-lookup"><span data-stu-id="d1a3a-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="d1a3a-116">Дополнительные сведения о том, как избежать этой проблемы, см. в разделе [Устранение неполадок, связанных с унаследованными обработчиками событий в Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="d1a3a-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a3a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d1a3a-117">See also</span></span>

- [<span data-ttu-id="d1a3a-118">Оператор Inherits</span><span class="sxs-lookup"><span data-stu-id="d1a3a-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="d1a3a-119">Оператор Imports (пространство имен и тип .NET)</span><span class="sxs-lookup"><span data-stu-id="d1a3a-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d1a3a-120">using</span><span class="sxs-lookup"><span data-stu-id="d1a3a-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="d1a3a-121">Влияние изменения внешнего вида базовой формы</span><span class="sxs-lookup"><span data-stu-id="d1a3a-121">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="d1a3a-122">Визуальное наследование в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1a3a-122">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
