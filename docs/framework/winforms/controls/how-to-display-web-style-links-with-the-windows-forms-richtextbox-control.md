---
title: Практическое руководство. Отображение ссылок веб-типа с помощью элемента управления RichTextBox в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: faaa48051c80b6dfd330f15f72a38297ff2d1b9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941587"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="ab651-102">Практическое руководство. Отображение ссылок веб-типа с помощью элемента управления RichTextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab651-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="ab651-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> веб-ссылок может отображать элемент управления цветом и подчеркиванием.</span><span class="sxs-lookup"><span data-stu-id="ab651-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="ab651-104">Можно написать код, который открывает окно браузера, веб-узлом, указанный в тексте ссылки, при щелчке ссылки.</span><span class="sxs-lookup"><span data-stu-id="ab651-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="ab651-105">Чтобы связать веб-страницу с элементом управления RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ab651-105">To link to a Web page with the RichTextBox control</span></span>  
  
1. <span data-ttu-id="ab651-106">Задайте <xref:System.Windows.Forms.RichTextBox.Text%2A> свойство на строку, которая содержит допустимый URL-адрес (например, "http://www.microsoft.com/«).</span><span class="sxs-lookup"><span data-stu-id="ab651-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2. <span data-ttu-id="ab651-107">Убедитесь, что <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> свойству `true` (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="ab651-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3. <span data-ttu-id="ab651-108">Создать новый глобальный экземпляр <xref:System.Diagnostics.Process> объекта.</span><span class="sxs-lookup"><span data-stu-id="ab651-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4. <span data-ttu-id="ab651-109">Написать обработчик событий для <xref:System.Windows.Forms.RichTextBox.LinkClicked> событий, который отправляет браузер требуемый текст.</span><span class="sxs-lookup"><span data-stu-id="ab651-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="ab651-110">В следующем примере <xref:System.Windows.Forms.RichTextBox.LinkClicked> событий открывает экземпляр Internet Explorer на URL-адрес, указанный в <xref:System.Windows.Forms.RichTextBox.Text%2A> свойство <xref:System.Windows.Forms.RichTextBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="ab651-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ab651-111">В этом примере предполагается, что форма <xref:System.Windows.Forms.RichTextBox> элемента управления.</span><span class="sxs-lookup"><span data-stu-id="ab651-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ab651-112">В вызывающем <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> метод, вы столкнетесь <xref:System.Security.SecurityException> исключение, если код выполняется в контексте частичного доверия из-за недостатка прав.</span><span class="sxs-lookup"><span data-stu-id="ab651-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="ab651-113">Дополнительные сведения см. в разделе [Основы управления доступом для кода](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ab651-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     <span data-ttu-id="ab651-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Необходимо инициализировать процесс `p`, что можно сделать, включив в конструктор формы следующую инструкцию:</span><span class="sxs-lookup"><span data-stu-id="ab651-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="ab651-115">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) поместите следующий код в конструктор формы для регистрации обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="ab651-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     <span data-ttu-id="ab651-116">Важно, чтобы немедленно остановить процесс, который вы создали после завершения работы с ним.</span><span class="sxs-lookup"><span data-stu-id="ab651-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="ab651-117">Ссылка на код, представленный выше, код, чтобы остановить процесс может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ab651-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ab651-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ab651-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="ab651-119">Элемент управления RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ab651-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="ab651-120">Элементы управления для использования в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab651-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
