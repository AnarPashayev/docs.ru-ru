---
title: Практическое руководство. Загрузка файлов в элемент управления RichTextBox в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 0456190f160c555dcc8ce5553674eee2cb73db8d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086784"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c194a-102">Практическое руководство. Загрузка файлов в элемент управления RichTextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c194a-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c194a-103">Элемент управления Windows Forms <xref:System.Windows.Forms.RichTextBox> может отображать обычный текст, обычный текст в Юникоде или файл в формате RTF.</span><span class="sxs-lookup"><span data-stu-id="c194a-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="c194a-104">Для этого вызовите метод <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="c194a-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="c194a-105">Метод <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> можно также использовать для загрузки данных из потока.</span><span class="sxs-lookup"><span data-stu-id="c194a-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="c194a-106">Для получения дополнительной информации см. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="c194a-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="c194a-107">Загрузка файла в элемент управления RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c194a-107">To load a file into the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="c194a-108">Определить путь к открываемому файлу с помощью компонента <xref:System.Windows.Forms.OpenFileDialog> .</span><span class="sxs-lookup"><span data-stu-id="c194a-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="c194a-109">Дополнительные сведения см. в разделе [Общие сведения о компоненте OpenFileDialog](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c194a-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="c194a-110">Вызовите метод <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> элемента управления <xref:System.Windows.Forms.RichTextBox> , указав загружаемый файл и при необходимости тип файла.</span><span class="sxs-lookup"><span data-stu-id="c194a-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="c194a-111">В следующем примере загружаемый файл берется из свойства <xref:System.Windows.Forms.OpenFileDialog> компонента <xref:System.Windows.Forms.FileDialog.FileName%2A> .</span><span class="sxs-lookup"><span data-stu-id="c194a-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="c194a-112">Если вы вызываете метод с именем файла в качестве единственного аргумента, предполагается, что тип файла должен быть RTF.</span><span class="sxs-lookup"><span data-stu-id="c194a-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="c194a-113">Чтобы указать другой тип файла, вызовите метод со значением перечисления <xref:System.Windows.Forms.RichTextBoxStreamType> в качестве второго аргумента.</span><span class="sxs-lookup"><span data-stu-id="c194a-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="c194a-114">В следующем примере компонент <xref:System.Windows.Forms.OpenFileDialog> отображается при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="c194a-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="c194a-115">Выбранный файл открывается и отображается в элементе управления <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="c194a-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c194a-116">В этом примере предполагается, что форма содержит кнопку`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="c194a-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     <span data-ttu-id="c194a-117">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) поместите следующий код в конструктор формы для регистрации обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="c194a-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c194a-118">Для запуска этого процесса сборке может потребоваться уровень привилегий, предоставляемый классом <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c194a-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c194a-119">При выполнении в контексте частичного доверия процесс может выдавать исключение из-за недостаточных привилегий.</span><span class="sxs-lookup"><span data-stu-id="c194a-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="c194a-120">Дополнительные сведения см. в разделе [Основы управления доступом для кода](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c194a-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c194a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="c194a-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="c194a-122">Элемент управления RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c194a-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="c194a-123">Элементы управления для использования в формах Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c194a-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
