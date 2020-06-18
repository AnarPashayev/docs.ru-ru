---
title: Практическое руководство. Добавление кавычек в строку
description: Сведения о том, как вставлять кавычки в текстовую строку. Кроме того, научитесь использовать поле Quote в качестве константы.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 08a3e2ab5662cbbf7825890ab430fddcd7b4a9ce
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903627"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="34bc5-104">Практическое руководство. Добавление кавычек в строку (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="34bc5-104">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="34bc5-105">Бывает, что в строку текста нужно вставить кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="34bc5-105">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="34bc5-106">Пример:</span><span class="sxs-lookup"><span data-stu-id="34bc5-106">For example:</span></span>  
  
 <span data-ttu-id="34bc5-107">Она сказала: "Ты этого заслуживаешь!"</span><span class="sxs-lookup"><span data-stu-id="34bc5-107">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="34bc5-108">В качестве альтернативы можно также использовать <xref:Microsoft.VisualBasic.ControlChars.Quote> поле как константу.</span><span class="sxs-lookup"><span data-stu-id="34bc5-108">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="34bc5-109">Вставка кавычек в строку в коде</span><span class="sxs-lookup"><span data-stu-id="34bc5-109">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="34bc5-110">В Visual Basic вставьте две кавычки в строку в качестве внедренной кавычки.</span><span class="sxs-lookup"><span data-stu-id="34bc5-110">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="34bc5-111">В Visual C# и Visual C++ Вставьте escape-последовательность \\ "как внедренную кавычку.</span><span class="sxs-lookup"><span data-stu-id="34bc5-111">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="34bc5-112">Например, для создания представленной выше строки используйте следующий код.</span><span class="sxs-lookup"><span data-stu-id="34bc5-112">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="34bc5-113">-или-</span><span class="sxs-lookup"><span data-stu-id="34bc5-113">-or-</span></span>  
  
2. <span data-ttu-id="34bc5-114">Вставьте для получения кавычки символ ASCII или Юникод.</span><span class="sxs-lookup"><span data-stu-id="34bc5-114">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="34bc5-115">В Visual Basic используйте символ ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="34bc5-115">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="34bc5-116">В Visual C# используйте символ Юникода (\u0022).</span><span class="sxs-lookup"><span data-stu-id="34bc5-116">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="34bc5-117">В данном примере использовать \u0022 нельзя, поскольку нельзя использовать универсальное имя символа, обозначающее символ в базовом наборе символов.</span><span class="sxs-lookup"><span data-stu-id="34bc5-117">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="34bc5-118">В противном случае вы получите C3851.</span><span class="sxs-lookup"><span data-stu-id="34bc5-118">Otherwise, you produce C3851.</span></span> <span data-ttu-id="34bc5-119">Дополнительные сведения см. в разделе [Ошибка компилятора C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="34bc5-119">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="34bc5-120">-или-</span><span class="sxs-lookup"><span data-stu-id="34bc5-120">-or-</span></span>  
  
3. <span data-ttu-id="34bc5-121">Также можно определить для символа константу и при необходимости использовать ее.</span><span class="sxs-lookup"><span data-stu-id="34bc5-121">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34bc5-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="34bc5-122">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="34bc5-123">Общие сведения об элементе управления TextBox</span><span class="sxs-lookup"><span data-stu-id="34bc5-123">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="34bc5-124">Практическое руководство. Управление положением курсора в элементе управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34bc5-124">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="34bc5-125">Практическое руководство. Создание текстового поля для ввода пароля с помощью элемента управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34bc5-125">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="34bc5-126">Практическое руководство. Создание текстового поля только для чтения</span><span class="sxs-lookup"><span data-stu-id="34bc5-126">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="34bc5-127">Практическое руководство. Выделение текста в элементе управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34bc5-127">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="34bc5-128">Практическое руководство. Многострочные элементы управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34bc5-128">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="34bc5-129">Элемент управления TextBox</span><span class="sxs-lookup"><span data-stu-id="34bc5-129">TextBox Control</span></span>](textbox-control-windows-forms.md)
