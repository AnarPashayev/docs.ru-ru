---
title: Практическое руководство. Изменение стилей элемента в управляемой объектной модели HTML-документов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 804041991199dd2722e3a0f38800bafd8933bbab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608402"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="36e99-102">Практическое руководство. Изменение стилей элемента в управляемой объектной модели HTML-документов</span><span class="sxs-lookup"><span data-stu-id="36e99-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>

<span data-ttu-id="36e99-103">Стили в формате HTML можно использовать для управления внешним видом документа и его элементов.</span><span class="sxs-lookup"><span data-stu-id="36e99-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="36e99-104"><xref:System.Windows.Forms.HtmlDocument> и <xref:System.Windows.Forms.HtmlElement> поддержки <xref:System.Windows.Forms.HtmlElement.Style%2A> свойств, которые принимают строки в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="36e99-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>

`name1:value1;...;nameN:valueN;`

<span data-ttu-id="36e99-105">Вот `DIV` с стиля строка, задающая шрифт Arial и весь текст, будут выводиться полужирным шрифтом:</span><span class="sxs-lookup"><span data-stu-id="36e99-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

<span data-ttu-id="36e99-106">Проблема при управлении стилей с помощью <xref:System.Windows.Forms.HtmlElement.Style%2A> свойство является то, что он может оказаться нелегкой задачей Добавление и удаление отдельных параметров стилей из строки.</span><span class="sxs-lookup"><span data-stu-id="36e99-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="36e99-107">Например, он стал бы сложная процедура для отображение текста курсивом, при наведении курсора на `DIV`и отключение курсивного начертания, когда курсор покидает `DIV`.</span><span class="sxs-lookup"><span data-stu-id="36e99-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="36e99-108">Время может стать проблемой, если необходимо управлять большим числом стили таким образом.</span><span class="sxs-lookup"><span data-stu-id="36e99-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>

<span data-ttu-id="36e99-109">Следующая процедура содержит код, который можно использовать, чтобы упростить управление стилями в HTML-документы и элементы.</span><span class="sxs-lookup"><span data-stu-id="36e99-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="36e99-110">Процедура требует, что вы знаете, как для выполнения основных задач в Windows Forms, таких как создание нового проекта и добавление элемента управления в форму.</span><span class="sxs-lookup"><span data-stu-id="36e99-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>

### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="36e99-111">Для обработки изменений стилей в приложении Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36e99-111">To process style changes in a Windows Forms application</span></span>

1. <span data-ttu-id="36e99-112">Создайте проект Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="36e99-112">Create a new Windows Forms project.</span></span>

2. <span data-ttu-id="36e99-113">Создайте новый файл класса с расширением соответствующие для используемого языка программирования.</span><span class="sxs-lookup"><span data-stu-id="36e99-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>

3. <span data-ttu-id="36e99-114">Копировать `StyleGenerator` код в разделе "Пример" в этом разделе класса в файл класса и сохраните код.</span><span class="sxs-lookup"><span data-stu-id="36e99-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>

4. <span data-ttu-id="36e99-115">Сохраните следующий код HTML в файл с именем отнести.</span><span class="sxs-lookup"><span data-stu-id="36e99-115">Save the following HTML to a file named Test.htm.</span></span>

    ```html
    <HTML>
        <BODY>

            <DIV style="font-face:arial;font-weight:bold;">
                Hello, world!
            </DIV><P>

            <DIV>
                Hello again, world!
            </DIV><P>

        </BODY>
    </HTML>
    ```

5. <span data-ttu-id="36e99-116">Добавить <xref:System.Windows.Forms.WebBrowser> управления с именем `webBrowser1` в главную форму проекта.</span><span class="sxs-lookup"><span data-stu-id="36e99-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>

6. <span data-ttu-id="36e99-117">Добавьте следующий код в файл кода проекта.</span><span class="sxs-lookup"><span data-stu-id="36e99-117">Add the following code to your project's code file.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="36e99-118">Убедитесь, что `webBrowser1_DocumentCompleted` обработчик событий работает в режиме прослушивателя для <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> событий.</span><span class="sxs-lookup"><span data-stu-id="36e99-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="36e99-119">В Visual Studio, дважды щелкните <xref:System.Windows.Forms.WebBrowser> управления; в текстовом редакторе, настройте прослушиватель программными средствами.</span><span class="sxs-lookup"><span data-stu-id="36e99-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7. <span data-ttu-id="36e99-120">Запустите проект.</span><span class="sxs-lookup"><span data-stu-id="36e99-120">Run the project.</span></span> <span data-ttu-id="36e99-121">Наведите курсор на первый `DIV` Обратите внимание на действия кода.</span><span class="sxs-lookup"><span data-stu-id="36e99-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36e99-122">Пример</span><span class="sxs-lookup"><span data-stu-id="36e99-122">Example</span></span>  
 <span data-ttu-id="36e99-123">В следующем примере кода показан полный код для `StyleGenerator` класс, который выполняет синтаксический анализ значение существующего стиля, поддерживает добавление, изменение и удаление стилей и возвращает новое значение стиля с требуемыми изменениями.</span><span class="sxs-lookup"><span data-stu-id="36e99-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="36e99-124">См. также</span><span class="sxs-lookup"><span data-stu-id="36e99-124">See also</span></span>

- <xref:System.Windows.Forms.HtmlElement>
