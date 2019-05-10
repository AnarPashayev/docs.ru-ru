---
title: Практическое руководство. Сохранение файлов с помощью элемента управления RichTextBox в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 9a4f5a98c9fea9658d9d9a400faa773b78a12f3a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638319"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="422fb-102">Практическое руководство. Сохранение файлов с помощью элемента управления RichTextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="422fb-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="422fb-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> управления может записывать сведения, которые отображаются в одном из следующих форматов:</span><span class="sxs-lookup"><span data-stu-id="422fb-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
- <span data-ttu-id="422fb-104">Обычный текст</span><span class="sxs-lookup"><span data-stu-id="422fb-104">Plain text</span></span>  
  
- <span data-ttu-id="422fb-105">Текст в Юникоде</span><span class="sxs-lookup"><span data-stu-id="422fb-105">Unicode plain text</span></span>  
  
- <span data-ttu-id="422fb-106">Rich Text Format (RTF)</span><span class="sxs-lookup"><span data-stu-id="422fb-106">Rich-Text Format (RTF)</span></span>  
  
- <span data-ttu-id="422fb-107">Формат RTF с пробелами вместо объектов OLE</span><span class="sxs-lookup"><span data-stu-id="422fb-107">RTF with spaces in place of OLE objects</span></span>  
  
- <span data-ttu-id="422fb-108">Обычный текст с текстовым представлением объектов OLE</span><span class="sxs-lookup"><span data-stu-id="422fb-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="422fb-109">Чтобы сохранить файл, вызовите <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="422fb-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="422fb-110">Можно также использовать **SaveFile** метод для сохранения данных в поток.</span><span class="sxs-lookup"><span data-stu-id="422fb-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="422fb-111">Дополнительные сведения см. в разделе <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="422fb-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="422fb-112">Чтобы сохранить содержимое элемента управления в файл</span><span class="sxs-lookup"><span data-stu-id="422fb-112">To save the contents of the control to a file</span></span>  
  
1. <span data-ttu-id="422fb-113">Определите путь к файлу должен быть сохранен.</span><span class="sxs-lookup"><span data-stu-id="422fb-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="422fb-114">Для этого в реальном приложении обычно используется <xref:System.Windows.Forms.SaveFileDialog> компонента.</span><span class="sxs-lookup"><span data-stu-id="422fb-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="422fb-115">Дополнительные сведения см. в разделе [Общие сведения о компоненте SaveFileDialog](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="422fb-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="422fb-116">Вызовите <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> метод <xref:System.Windows.Forms.RichTextBox> управления, указав имя файла для сохранения и при необходимости тип файла.</span><span class="sxs-lookup"><span data-stu-id="422fb-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="422fb-117">Если вызвать метод с именем файла в качестве единственного аргумента, файл будет сохранен как RTF.</span><span class="sxs-lookup"><span data-stu-id="422fb-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="422fb-118">Чтобы указать другой тип файла, вызовите метод со значением перечисления <xref:System.Windows.Forms.RichTextBoxStreamType> в качестве второго аргумента.</span><span class="sxs-lookup"><span data-stu-id="422fb-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="422fb-119">В приведенном ниже примере путь задан для — расположение файла RTF- **Мои документы** папки.</span><span class="sxs-lookup"><span data-stu-id="422fb-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="422fb-120">Это расположение используется в том случае, так как можно предположить, что большинство компьютеров под управлением ОС Windows будет включать эту папку.</span><span class="sxs-lookup"><span data-stu-id="422fb-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="422fb-121">Эта папка также пользователи со систему с минимальным уровнем доступа могут безопасно запускать приложение.</span><span class="sxs-lookup"><span data-stu-id="422fb-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="422fb-122">В приведенном ниже примере предполагается, что форма <xref:System.Windows.Forms.RichTextBox> управления уже добавлен.</span><span class="sxs-lookup"><span data-stu-id="422fb-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="422fb-123">В этом примере создается файл (если файл отсутствует).</span><span class="sxs-lookup"><span data-stu-id="422fb-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="422fb-124">Если приложению требуется для создания файла, что ему необходимо иметь доступ для папки.</span><span class="sxs-lookup"><span data-stu-id="422fb-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="422fb-125">Для задания разрешений используются списки управления доступом.</span><span class="sxs-lookup"><span data-stu-id="422fb-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="422fb-126">Если файл уже существует, приложению требуется только доступ на запись, более низким уровнем.</span><span class="sxs-lookup"><span data-stu-id="422fb-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="422fb-127">Где это возможно, безопаснее создать файл во время развертывания и только предоставить доступ на чтение к одному файлу, чем на доступ к папке.</span><span class="sxs-lookup"><span data-stu-id="422fb-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="422fb-128">По тем же соображениям рекомендуется записывать данные в пользовательские папки, а не в коревую папку или папку Program Files.</span><span class="sxs-lookup"><span data-stu-id="422fb-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422fb-129">См. также</span><span class="sxs-lookup"><span data-stu-id="422fb-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="422fb-130">Элемент управления RichTextBox</span><span class="sxs-lookup"><span data-stu-id="422fb-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="422fb-131">Элементы управления для использования в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="422fb-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
