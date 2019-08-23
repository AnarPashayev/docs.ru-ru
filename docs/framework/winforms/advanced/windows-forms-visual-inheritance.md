---
title: Визуальное наследование в Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: 11a90615938da9e7dda5e05c55546918ccde137d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957099"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="6d4ba-102">Визуальное наследование в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d4ba-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="6d4ba-103">В некоторых случаях вы можете решить, что проект вызывает форму, похожую на форму, созданную в предыдущем проекте.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="6d4ba-104">Или можете захотеть создать базовую форму с параметрами, например водяным знаком или определенной структурой элементов управления, которые будут затем повторно использоваться в проекте, с каждой итерацией, содержащей изменения в исходном шаблоне формы.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="6d4ba-105">Наследование форм позволяет создать базовую форму, затем наследовать от нее и вносить изменения, сохраняя при этом все необходимые исходные параметры.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="6d4ba-106">Формы производного класса можно создавать программно или с помощью выбора компонентов для визуального наследования.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d4ba-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="6d4ba-107">In This Section</span></span>  
 [<span data-ttu-id="6d4ba-108">Практическое руководство. Наследовать Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d4ba-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="6d4ba-109">Указания по созданию наследуемых форм в коде.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="6d4ba-110">Практическое руководство. Наследование форм с помощью диалогового окна "Выбор наследования"</span><span class="sxs-lookup"><span data-stu-id="6d4ba-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="6d4ba-111">Указания по созданию наследуемых форм с помощью окна выбора компонентов для наследования.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="6d4ba-112">Влияние изменения внешнего вида базовой формы</span><span class="sxs-lookup"><span data-stu-id="6d4ba-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="6d4ba-113">Указания по изменению элементов управления базовой формы и их свойств.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="6d4ba-114">Пошаговое руководство: Демонстрация визуального наследования</span><span class="sxs-lookup"><span data-stu-id="6d4ba-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="6d4ba-115">Создание базовой формы Windows Forms и ее компиляция в библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="6d4ba-116">После этого данная библиотека классов импортируется в другой проект и создается новая форма, которая наследуется от базовой формы.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="6d4ba-117">Практическое руководство. Использование модификаторов и свойств Женератемембер</span><span class="sxs-lookup"><span data-stu-id="6d4ba-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="6d4ba-118">Указания по использованию свойств `GenerateMember` и `Modifiers`, актуальных в случае, когда конструктор Windows Forms создает переменную-член для компонента.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6d4ba-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="6d4ba-119">Related Sections</span></span>  
 [<span data-ttu-id="6d4ba-120">Основы наследования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d4ba-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="6d4ba-121">Описание способов определения классов Visual Basic, которые служат основой для других классов.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="6d4ba-122">class</span><span class="sxs-lookup"><span data-stu-id="6d4ba-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="6d4ba-123">Описание принципов особенностей классов в C#, в которых разрешено единичное наследование.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="6d4ba-124">Устранение неполадок, связанных с унаследованными обработчиками событий, в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d4ba-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="6d4ba-125">Перечисление распространенных проблем, возникающих в обработчиках событий в наследуемых компонентах.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-125">Lists common issues that arise with event handlers in inherited components</span></span>
