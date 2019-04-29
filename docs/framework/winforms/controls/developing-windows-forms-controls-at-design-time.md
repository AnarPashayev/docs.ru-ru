---
title: Создание элементов управления Windows Forms во время разработки
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972241"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="a8525-102">Создание элементов управления Windows Forms во время разработки</span><span class="sxs-lookup"><span data-stu-id="a8525-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="a8525-103">Среда .NET Framework предоставляет широкий набор технологий создания элементов управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="a8525-104">Авторы больше не ограничены созданием составных элементов управления, которые действуют как коллекция стандартных элементов управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="a8525-105">Через наследование можно создать свои собственные элементы управления на основе существующих составных элементов управления или существующих элементов управления Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8525-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="a8525-106">Можно также создать собственные элементы управления, реализующие настраиваемое рисование.</span><span class="sxs-lookup"><span data-stu-id="a8525-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="a8525-107">Эти возможности обеспечивают высокую степень гибкости разработки и функциональности визуального интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8525-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="a8525-108">Чтобы воспользоваться преимуществами этих функций, вы должны быть знакомы с понятиями объектно-ориентированного программирования.</span><span class="sxs-lookup"><span data-stu-id="a8525-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8525-109">Это не обязательно иметь глубокие знания о наследовании, но могут оказаться полезными для ссылки на [Основы наследования (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a8525-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="a8525-110">Если вам необходимо создать пользовательский элемент управления для использования в веб-формах, см. раздел [Разработка пользовательских серверных элементов управления ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8525-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8525-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a8525-111">In This Section</span></span>  
 [<span data-ttu-id="a8525-112">Пошаговое руководство: Создание составного элемента управления с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8525-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="a8525-113">Демонстрируется создание простого составного элемента управления в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8525-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="a8525-114">Пошаговое руководство: Создание составного элемента управления с помощью VisualC#</span><span class="sxs-lookup"><span data-stu-id="a8525-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="a8525-115">Демонстрируется создание простого составного элемента управления в C#.</span><span class="sxs-lookup"><span data-stu-id="a8525-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="a8525-116">Пошаговое руководство: Наследование элементов управления Windows Forms с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8525-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="a8525-117">Демонстрируется создание простого элемента управления Windows Forms с помощью наследования в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8525-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="a8525-118">Пошаговое руководство: Наследование элементов управления Windows Forms с помощью VisualC#</span><span class="sxs-lookup"><span data-stu-id="a8525-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="a8525-119">Демонстрируется создание простого элемента управления Windows Forms с помощью наследования в C#.</span><span class="sxs-lookup"><span data-stu-id="a8525-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="a8525-120">Пошаговое руководство: Выполнение типичных задач с помощью смарт-тегов в Windows Forms элементы управления</span><span class="sxs-lookup"><span data-stu-id="a8525-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="a8525-121">Демонстрируется использование функции смарт-тегов в элементах управления Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8525-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a8525-122">Пошаговое руководство: Сериализация коллекций стандартных типов с использованием атрибута DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="a8525-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="a8525-123">Демонстрируется использование <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> атрибут для сериализации коллекции.</span><span class="sxs-lookup"><span data-stu-id="a8525-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="a8525-124">Пошаговое руководство: Отладка пользовательских элементов управления Windows Forms во время разработки</span><span class="sxs-lookup"><span data-stu-id="a8525-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="a8525-125">Демонстрируется процедура отладки поведения элемента управления Windows Forms во время разработки.</span><span class="sxs-lookup"><span data-stu-id="a8525-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="a8525-126">Пошаговое руководство: Создание элемента управления Windows Forms, используются преимущества функций Visual Studio во время разработки</span><span class="sxs-lookup"><span data-stu-id="a8525-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="a8525-127">Демонстрируется интеграция составного элемента управления в среду разработки.</span><span class="sxs-lookup"><span data-stu-id="a8525-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="a8525-128">Практическое руководство. Автор элементы управления для форм Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8525-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="a8525-129">Общие рекомендации по реализации элемента управления Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8525-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="a8525-130">Практическое руководство. Создание составных элементов управления</span><span class="sxs-lookup"><span data-stu-id="a8525-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="a8525-131">Демонстрируется создание элемента управления путем наследования из составного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="a8525-132">Практическое руководство. Наследование класса UserControl</span><span class="sxs-lookup"><span data-stu-id="a8525-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="a8525-133">Обзор процедуры создания составного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="a8525-134">Практическое руководство. Наследование Windows существующих элементов управления формы</span><span class="sxs-lookup"><span data-stu-id="a8525-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="a8525-135">Демонстрируется создание расширенного элемента управления путем наследования от <xref:System.Windows.Forms.Button> класс элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="a8525-136">Практическое руководство. Наследовать от класса Control</span><span class="sxs-lookup"><span data-stu-id="a8525-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="a8525-137">Обзор создания расширенного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="a8525-138">Практическое руководство. Выравнивание элементов управления по границам формы во время разработки</span><span class="sxs-lookup"><span data-stu-id="a8525-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="a8525-139">Показано, как использовать <xref:System.Windows.Forms.Control.Dock%2A> свойства выравнивания элемента управления по краю занимаемой им формы.</span><span class="sxs-lookup"><span data-stu-id="a8525-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="a8525-140">Практическое руководство. Отображение элемента управления в Выбор элементов панели элементов-диалоговое окно</span><span class="sxs-lookup"><span data-stu-id="a8525-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="a8525-141">Описание процедуры установки элемента управления таким образом, чтобы он отображался в диалоговом окне **Настройка области элементов**.</span><span class="sxs-lookup"><span data-stu-id="a8525-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="a8525-142">Практическое руководство. Предоставление точечного рисунка панели элементов для элемента управления</span><span class="sxs-lookup"><span data-stu-id="a8525-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="a8525-143">Демонстрируется использование <xref:System.Drawing.ToolboxBitmapAttribute> для отображения значка рядом с пользовательского элемента управления в **элементов**.</span><span class="sxs-lookup"><span data-stu-id="a8525-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="a8525-144">Практическое руководство. Тестирование во время выполнения поведения элемента UserControl</span><span class="sxs-lookup"><span data-stu-id="a8525-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="a8525-145">Демонстрируется использование **тестового контейнера UserControl** для тестирования поведения составного элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="a8525-146">Ошибки во время разработки в конструкторе Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8525-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="a8525-147">Объяснение значения и использования списка ошибок во время разработки, отображаемого в Microsoft Visual Studio при невозможности загрузить конструктор Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8525-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="a8525-148">Разрешение вопросов, связанных с созданием элементов управления и компонентов</span><span class="sxs-lookup"><span data-stu-id="a8525-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="a8525-149">Демонстрируются диагностика и исправление распространенных проблем, возникающих при разработке пользовательского компонента или элемента управления.</span><span class="sxs-lookup"><span data-stu-id="a8525-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8525-150">Ссылка</span><span class="sxs-lookup"><span data-stu-id="a8525-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="a8525-151">Описывает данный класс и предоставляет ссылки на все его члены.</span><span class="sxs-lookup"><span data-stu-id="a8525-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="a8525-152">Описывает данный класс и предоставляет ссылки на все его члены.</span><span class="sxs-lookup"><span data-stu-id="a8525-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8525-153">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="a8525-153">Related Sections</span></span>  
 [<span data-ttu-id="a8525-154">Разработка пользовательских элементов управления Windows Forms в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8525-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="a8525-155">Описывается создание пользовательских элементов управления с помощью .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8525-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="a8525-156">Независимость от языка и независимые от языка компоненты</span><span class="sxs-lookup"><span data-stu-id="a8525-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="a8525-157">Основные сведения об общеязыковой среде выполнения (CLR), которая предназначена для упрощения создания и использования компонентов.</span><span class="sxs-lookup"><span data-stu-id="a8525-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="a8525-158">Важным аспектом этого упрощения является расширение возможностей взаимодействия между компонентами, написанными на разных языках программирования.</span><span class="sxs-lookup"><span data-stu-id="a8525-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="a8525-159">Спецификация CLS делает возможным создание инструментов и компонентов, которые работают с несколькими языками программирования.</span><span class="sxs-lookup"><span data-stu-id="a8525-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="a8525-160">Пошаговое руководство: Автоматическое заполнение панели элементов пользовательскими компонентами</span><span class="sxs-lookup"><span data-stu-id="a8525-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="a8525-161">Описание включения компонентов или элементов управления для отображения в диалоговом окне **Настройка области элементов**.</span><span class="sxs-lookup"><span data-stu-id="a8525-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
