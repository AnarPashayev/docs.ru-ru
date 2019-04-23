---
title: Практическое руководство. Асинхронная загрузка звука в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 1d710f1e6d3b208365d5b1eb2524fbeeaa673c2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185761"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="f4b61-102">Практическое руководство. Асинхронная загрузка звука в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4b61-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="f4b61-103">В примере кода ниже производится асинхронная загрузка звука по URL-адресу, после чего он воспроизводится в новом потоке.</span><span class="sxs-lookup"><span data-stu-id="f4b61-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4b61-104">Пример</span><span class="sxs-lookup"><span data-stu-id="f4b61-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4b61-105">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="f4b61-105">Compiling the Code</span></span>  
 <span data-ttu-id="f4b61-106">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="f4b61-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f4b61-107">ссылки на сборки System и System.Windows.Forms;</span><span class="sxs-lookup"><span data-stu-id="f4b61-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="f4b61-108">замена имени файла `"http://www.tailspintoys.com/sounds/stop.wav"` на допустимое имя файла.</span><span class="sxs-lookup"><span data-stu-id="f4b61-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="f4b61-109">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f4b61-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f4b61-110">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="f4b61-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f4b61-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="f4b61-111">Robust Programming</span></span>  
 <span data-ttu-id="f4b61-112">Операции с файлами должны быть включены в соответствующие блоки обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="f4b61-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="f4b61-113">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="f4b61-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f4b61-114">Недопустимое имя пути</span><span class="sxs-lookup"><span data-stu-id="f4b61-114">The path name is malformed.</span></span> <span data-ttu-id="f4b61-115">(например, путь содержит недопустимые символы или состоит только из пробелов (класс <xref:System.ArgumentException>)).</span><span class="sxs-lookup"><span data-stu-id="f4b61-115">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f4b61-116">Путь доступен только для чтения (класс <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f4b61-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f4b61-117">Имя пути — `Nothing` (класс <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f4b61-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f4b61-118">Указано слишком длинное имя пути (класс <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f4b61-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f4b61-119">Недопустимый путь (класс <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f4b61-119">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f4b61-120">Путь содержит только двоеточие (":") (класс <xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f4b61-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f4b61-121">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f4b61-121">.NET Framework Security</span></span>  
 <span data-ttu-id="f4b61-122">По имени файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="f4b61-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f4b61-123">Например, файл с именем `Form1.vb` может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f4b61-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="f4b61-124">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="f4b61-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b61-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f4b61-125">See also</span></span>

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="f4b61-126">Практическое руководство. Воспроизведение звука в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4b61-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
