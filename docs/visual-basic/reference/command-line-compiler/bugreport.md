---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: e7b4ebc58b6fe9850b92ef945cb0d715e4369efe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820915"
---
# <a name="-bugreport"></a><span data-ttu-id="9f167-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="9f167-102">-bugreport</span></span>
<span data-ttu-id="9f167-103">Создает файл, который можно использовать, если файл отчета об ошибках.</span><span class="sxs-lookup"><span data-stu-id="9f167-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f167-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f167-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f167-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="9f167-105">Arguments</span></span>  
  
|<span data-ttu-id="9f167-106">Термин</span><span class="sxs-lookup"><span data-stu-id="9f167-106">Term</span></span>|<span data-ttu-id="9f167-107">Определение</span><span class="sxs-lookup"><span data-stu-id="9f167-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="9f167-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="9f167-108">Required.</span></span> <span data-ttu-id="9f167-109">Имя файла, который будет содержать отчет об ошибках.</span><span class="sxs-lookup"><span data-stu-id="9f167-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="9f167-110">Заключите имя файла в кавычки (» «), если имя содержит пробел.</span><span class="sxs-lookup"><span data-stu-id="9f167-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f167-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="9f167-111">Remarks</span></span>  
 <span data-ttu-id="9f167-112">Добавляется следующее `file`:</span><span class="sxs-lookup"><span data-stu-id="9f167-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="9f167-113">Копия всех файлов исходного кода при компиляции.</span><span class="sxs-lookup"><span data-stu-id="9f167-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="9f167-114">Список параметров компилятора, используемых при компиляции.</span><span class="sxs-lookup"><span data-stu-id="9f167-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="9f167-115">Сведения о компилятора, среда CLR и операционной системы версии.</span><span class="sxs-lookup"><span data-stu-id="9f167-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="9f167-116">Выходные данные компилятора (если есть).</span><span class="sxs-lookup"><span data-stu-id="9f167-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="9f167-117">Описание проблемы, в которой запрашивается.</span><span class="sxs-lookup"><span data-stu-id="9f167-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="9f167-118">Описание предполагаемого способа разрешения проблемы должны быть исправлены, для которой предлагается.</span><span class="sxs-lookup"><span data-stu-id="9f167-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="9f167-119">Поскольку копия всех файлов исходного кода в `file`, может потребоваться воспроизвести предполагаемую ошибку в максимально короткой программе.</span><span class="sxs-lookup"><span data-stu-id="9f167-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f167-120">`-bugreport` Параметр создает файл, который может содержать конфиденциальные данные.</span><span class="sxs-lookup"><span data-stu-id="9f167-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="9f167-121">Это включает в себя текущее время, версия компилятора [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] версии, версия операционной системы, имя пользователя, аргументы командной строки с помощью которых компилятор был запущен, весь исходный код и двоичной форме любого связанной сборки.</span><span class="sxs-lookup"><span data-stu-id="9f167-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="9f167-122">Этот параметр может осуществляться путем указания параметров командной строки в файле Web.config на сервере с подборкой [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] приложения.</span><span class="sxs-lookup"><span data-stu-id="9f167-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="9f167-123">Чтобы избежать этого, необходимо измените файл Machine.config, чтобы запретить пользователям компиляцию на сервере.</span><span class="sxs-lookup"><span data-stu-id="9f167-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="9f167-124">Если этот параметр используется с `-errorreport:prompt`, `-errorreport:queue`, или `-errorreport:send`, и приложение сталкивается с внутренней ошибки компилятора, заполните `file` отправляется в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="9f167-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="9f167-125">Эти сведения помогут определить причину ошибки инженерам Майкрософт и помогут улучшить следующую версию Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9f167-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="9f167-126">По умолчанию никакая информация отправляется в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="9f167-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="9f167-127">Тем не менее, при компиляции приложения с помощью `-errorreport:queue`, включена по умолчанию, приложение собирает отчеты об ошибках.</span><span class="sxs-lookup"><span data-stu-id="9f167-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="9f167-128">Затем при входе в систему администратора системы отчетов об ошибках отображается всплывающее окно, администратор может пересылать в корпорацию Майкрософт отчеты о любых ошибках, произошедших с момента входа в систему.</span><span class="sxs-lookup"><span data-stu-id="9f167-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f167-129">`/bugreport` Не доступна из среды разработки Visual Studio; она доступна только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="9f167-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f167-130">Пример</span><span class="sxs-lookup"><span data-stu-id="9f167-130">Example</span></span>  
 <span data-ttu-id="9f167-131">В следующем примере компилируется `T2.vb` и помещает всю информацию, создание отчетов об ошибках в файле `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="9f167-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f167-132">См. также</span><span class="sxs-lookup"><span data-stu-id="9f167-132">See also</span></span>

- [<span data-ttu-id="9f167-133">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="9f167-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9f167-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f167-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="9f167-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="9f167-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="9f167-136">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="9f167-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="9f167-137">[Элемент trustLevel для securityPolicy (схема параметров ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9f167-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
