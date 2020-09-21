---
title: Практическое руководство. Запись текста в файлы в каталоге "Мои документы"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bb3a9bdc44f86fbcdb3c56ee088740efdfebe95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546462"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="fdac7-102">Практическое руководство. Запись текста в файлы в каталоге "Мои документы" в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdac7-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="fdac7-103">Объект `My.Computer.FileSystem.SpecialDirectories` позволяет получить доступ к специальным каталогам, таким как каталог **Мои документы**.</span><span class="sxs-lookup"><span data-stu-id="fdac7-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="fdac7-104">Процедура</span><span class="sxs-lookup"><span data-stu-id="fdac7-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="fdac7-105">Запись новых текстовых файлов в каталог "Мои документы"</span><span class="sxs-lookup"><span data-stu-id="fdac7-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="fdac7-106">Укажите путь в свойстве `My.Computer.FileSystem.SpecialDirectories.MyDocuments`.</span><span class="sxs-lookup"><span data-stu-id="fdac7-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="fdac7-107">Используйте метод `WriteAllText` для записи текста в указанный файл.</span><span class="sxs-lookup"><span data-stu-id="fdac7-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="fdac7-108">Пример</span><span class="sxs-lookup"><span data-stu-id="fdac7-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fdac7-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="fdac7-109">Compiling the Code</span></span>  

 <span data-ttu-id="fdac7-110">Замените имя `test.txt` на имя файла, в который требуется выполнить запись.</span><span class="sxs-lookup"><span data-stu-id="fdac7-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fdac7-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="fdac7-111">Robust Programming</span></span>  

 <span data-ttu-id="fdac7-112">Этот код возвращает все исключения, которые могут произойти при записи текста в файл.</span><span class="sxs-lookup"><span data-stu-id="fdac7-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="fdac7-113">Можно уменьшить вероятность возникновения исключений с помощью элементов управления Windows Forms, таких как компоненты [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) и [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms), которые позволяют пользователям выбирать только допустимые имена файлов.</span><span class="sxs-lookup"><span data-stu-id="fdac7-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) and the [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="fdac7-114">Однако использование этих элементов управления не гарантирует полную надежность.</span><span class="sxs-lookup"><span data-stu-id="fdac7-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="fdac7-115">В период между моментом выбора пользователем файла и моментом выполнения кода файловая система может измениться.</span><span class="sxs-lookup"><span data-stu-id="fdac7-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="fdac7-116">Таким образом, при работе с файлами обработка исключений почти всегда является необходимой.</span><span class="sxs-lookup"><span data-stu-id="fdac7-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fdac7-117">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fdac7-117">.NET Framework Security</span></span>  

 <span data-ttu-id="fdac7-118">Если код выполняется в контексте частичного доверия, исключение может возникнуть из-за недостатка прав доступа.</span><span class="sxs-lookup"><span data-stu-id="fdac7-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="fdac7-119">Дополнительные сведения см. в разделе [Основы управления доступом для кода](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="fdac7-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="fdac7-120">В этом примере создается новый файл.</span><span class="sxs-lookup"><span data-stu-id="fdac7-120">This example creates a new file.</span></span> <span data-ttu-id="fdac7-121">Если приложение создает файл, оно должно иметь разрешение на создание файла в соответствующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="fdac7-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="fdac7-122">Для задания разрешений используются списки управления доступом.</span><span class="sxs-lookup"><span data-stu-id="fdac7-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="fdac7-123">Если файл уже существует, приложению требуется лишь разрешение на запись (с более низким уровнем).</span><span class="sxs-lookup"><span data-stu-id="fdac7-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="fdac7-124">Для повышения безопасности рекомендуется по возможности создавать файлы во время развертывания и предоставлять доступ на чтение только к одному файлу, а не доступ к каталогу с разрешением на создание.</span><span class="sxs-lookup"><span data-stu-id="fdac7-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="fdac7-125">По тем же соображениям рекомендуется записывать данные в пользовательские папки, а не в корневую папку или папку **Program Files**.</span><span class="sxs-lookup"><span data-stu-id="fdac7-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="fdac7-126">Дополнительные сведения см. в разделе [Общие сведения о технологии ACL](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fdac7-126">For more information, see [ACL Technology Overview](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdac7-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fdac7-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
