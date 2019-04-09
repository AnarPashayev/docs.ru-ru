---
title: Практическое руководство. Выбор принтера, подключенного к компьютеру пользователя, в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: bebb879020e6e45e77f109bf9c377b7322d5e8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184032"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="d08a6-102">Практическое руководство. Выбор принтера, подключенного к компьютеру пользователя, в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d08a6-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="d08a6-103">Часто для печати пользователям требуется выбрать принтер, отличный от используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d08a6-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="d08a6-104">С помощью компонента <xref:System.Windows.Forms.PrintDialog> можно разрешить пользователям выбрать один из установленных принтеров.</span><span class="sxs-lookup"><span data-stu-id="d08a6-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="d08a6-105">Компонент <xref:System.Windows.Forms.PrintDialog> позволяет зафиксировать <xref:System.Windows.Forms.DialogResult> компонента <xref:System.Windows.Forms.PrintDialog> и использовать его для выбора принтера.</span><span class="sxs-lookup"><span data-stu-id="d08a6-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="d08a6-106">В следующей процедуре выбирается текстовый файл для печати на принтер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d08a6-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="d08a6-107">После этого создается экземпляр класса <xref:System.Windows.Forms.PrintDialog> .</span><span class="sxs-lookup"><span data-stu-id="d08a6-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="d08a6-108">Выбор принтера и печать файла</span><span class="sxs-lookup"><span data-stu-id="d08a6-108">To choose a printer and then print a file</span></span>  
  
1.  <span data-ttu-id="d08a6-109">Выберите принтер для использования с помощью <xref:System.Windows.Forms.PrintDialog> компонента.</span><span class="sxs-lookup"><span data-stu-id="d08a6-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="d08a6-110">В следующем примере кода обрабатываются два события.</span><span class="sxs-lookup"><span data-stu-id="d08a6-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="d08a6-111">В первом <xref:System.Windows.Forms.Button> элемента управления <xref:System.Windows.Forms.Control.Click> событий, <xref:System.Windows.Forms.PrintDialog> создается экземпляр класса, а выбранный пользователем принтер фиксируется в <xref:System.Windows.Forms.DialogResult> свойство.</span><span class="sxs-lookup"><span data-stu-id="d08a6-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="d08a6-112">Во втором событии <xref:System.Drawing.Printing.PrintDocument.PrintPage> событие <xref:System.Drawing.Printing.PrintDocument> компонент, образец документа распечатывается на указанном принтере.</span><span class="sxs-lookup"><span data-stu-id="d08a6-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="d08a6-113">(Visual C# и [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) поместите следующий код в конструктор формы для регистрации обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="d08a6-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d08a6-114">См. также</span><span class="sxs-lookup"><span data-stu-id="d08a6-114">See also</span></span>

- [<span data-ttu-id="d08a6-115">Поддержка печати в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d08a6-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
