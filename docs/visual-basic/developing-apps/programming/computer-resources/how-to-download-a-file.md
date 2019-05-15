---
title: Практическое руководство. Загрузка файла в Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 2beab73bde30a11ed9803723dce5fb4c3392fce7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662748"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="a4e19-102">Практическое руководство. Загрузка файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4e19-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="a4e19-103">Метод <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> можно использовать для скачивания удаленного файла и сохранения его в определенном месте.</span><span class="sxs-lookup"><span data-stu-id="a4e19-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="a4e19-104">Если для параметра `ShowUI` установлено значение `True`, отображается диалоговое окно, показывающее ход загрузки и позволяющее пользователю отменить операцию.</span><span class="sxs-lookup"><span data-stu-id="a4e19-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="a4e19-105">По умолчанию существующие файлы с тем же именем не перезаписываются. Если требуется перезаписывать существующие файлы, установите для параметра `overwrite` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="a4e19-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="a4e19-106">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="a4e19-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a4e19-107">Недопустимое имя диска (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a4e19-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="a4e19-108">Не была предоставлена необходимая аутентификация (<xref:System.UnauthorizedAccessException> или <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a4e19-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="a4e19-109">Сервер не отвечает в пределах указанного `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="a4e19-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
- <span data-ttu-id="a4e19-110">Запрос отклонен веб-сайтом (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="a4e19-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4e19-111">По имени файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="a4e19-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="a4e19-112">Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4e19-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="a4e19-113">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="a4e19-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="a4e19-114">Содержимое файла может отличаться от ожидаемого, поэтому может не удаться прочесть файл с помощью методов чтения.</span><span class="sxs-lookup"><span data-stu-id="a4e19-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="a4e19-115">Загрузка файла</span><span class="sxs-lookup"><span data-stu-id="a4e19-115">To download a file</span></span>  
  
- <span data-ttu-id="a4e19-116">Используйте метод `DownloadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI и задав расположение для сохранения файла.</span><span class="sxs-lookup"><span data-stu-id="a4e19-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="a4e19-117">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="a4e19-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="a4e19-118">Загрузка файла с указанием времени ожидания</span><span class="sxs-lookup"><span data-stu-id="a4e19-118">To download a file, specifying a time-out interval</span></span>  
  
- <span data-ttu-id="a4e19-119">Используйте метод `DownloadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI, задав расположение для сохранения файла и интервал времени ожидания в миллисекундах (значение по умолчанию 1000).</span><span class="sxs-lookup"><span data-stu-id="a4e19-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="a4e19-120">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents` с указанием интервала ожидания 500 миллисекунд:</span><span class="sxs-lookup"><span data-stu-id="a4e19-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="a4e19-121">Загрузка файла с указанием имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="a4e19-121">To download a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="a4e19-122">Используйте метод `DownLoadFile`, чтобы скачать файл, указав расположение конечного файла в виде строки или URI и задав расположение для сохранения файла, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="a4e19-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="a4e19-123">В этом примере выполняется загрузка файла `WineList.txt` из `http://www.cohowinery.com/downloads` и его сохранение в `C:\Documents and Settings\All Users\Documents` с именем пользователя `anonymous` и пустым паролем.</span><span class="sxs-lookup"><span data-stu-id="a4e19-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a4e19-124">Протокол FTP, используемый методом `DownLoadFile`, отправляет данные, включая пароли, в формате обычного текста и не должен использоваться для передачи важных сведений.</span><span class="sxs-lookup"><span data-stu-id="a4e19-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e19-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a4e19-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="a4e19-126">Практическое руководство. Передача файла</span><span class="sxs-lookup"><span data-stu-id="a4e19-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="a4e19-127">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="a4e19-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
