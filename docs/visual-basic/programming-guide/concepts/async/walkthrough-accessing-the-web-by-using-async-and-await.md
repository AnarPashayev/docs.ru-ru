---
title: Пошаговое руководство. Доступ к Интернету с использованием Async и Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 7f9b71bc76e8d17cf2fb6714070b4439265d1fda
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335905"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="f94fe-102">Пошаговое руководство. Доступ к Интернету с использованием Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="f94fe-103">Возможности Async и Await упрощают создание асинхронных программ.</span><span class="sxs-lookup"><span data-stu-id="f94fe-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="f94fe-104">Можно написать асинхронный код, который выглядит как синхронный, и позволить компилятору обрабатывать трудные функции обратного вызова и продолжения, которые обычно включает асинхронный код.</span><span class="sxs-lookup"><span data-stu-id="f94fe-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="f94fe-105">Дополнительные сведения о возможности Async см. в разделе [асинхронное программирование с использованием Async и Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f94fe-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="f94fe-106">Это пошаговое руководство начинается с создания синхронного приложения Windows Presentation Foundation (WPF), которое суммирует число байтов в списке веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="f94fe-107">Затем в рамках руководства приложение преобразуется в асинхронное решение с помощью новых возможностей.</span><span class="sxs-lookup"><span data-stu-id="f94fe-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="f94fe-108">Если вы не хотите создавать приложение самостоятельно, можно загрузить «пример Async: Доступ к Пошаговое руководство (C# и Visual Basic)» из [примеры кода от разработчиков](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="f94fe-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="f94fe-109">В этом пошаговом руководстве выполняются следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="f94fe-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="f94fe-110">Создание приложения WPF</span><span class="sxs-lookup"><span data-stu-id="f94fe-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="f94fe-111">Разработка простого окна MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="f94fe-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="f94fe-112">Добавление ссылки</span><span class="sxs-lookup"><span data-stu-id="f94fe-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="f94fe-113">Добавление необходимых операторов Imports</span><span class="sxs-lookup"><span data-stu-id="f94fe-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="f94fe-114">Создание синхронного приложения</span><span class="sxs-lookup"><span data-stu-id="f94fe-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="f94fe-115">Тестирование синхронного решения</span><span class="sxs-lookup"><span data-stu-id="f94fe-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="f94fe-116">Преобразование GetURLContents в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="f94fe-117">Преобразование SumPageSizes в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="f94fe-118">Преобразование startButton_Click в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="f94fe-119">Тестирование асинхронного решения</span><span class="sxs-lookup"><span data-stu-id="f94fe-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="f94fe-120">Замена GetURLContentsAsync методом .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f94fe-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="f94fe-121">Пример</span><span class="sxs-lookup"><span data-stu-id="f94fe-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="f94fe-122">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="f94fe-122">Prerequisites</span></span>  
 <span data-ttu-id="f94fe-123">На компьютере должна быть установлена среда Visual Studio 2012 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f94fe-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="f94fe-124">Дополнительные сведения см. на [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="f94fe-124">For more information, see the [Microsoft website](https://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
### <a name="CreateWPFApp"></a> <span data-ttu-id="f94fe-125">Создание приложения WPF</span><span class="sxs-lookup"><span data-stu-id="f94fe-125">To create a WPF application</span></span>  
  
1. <span data-ttu-id="f94fe-126">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f94fe-126">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="f94fe-127">В строке меню выберите **Файл**, **Создать**, **Проект**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="f94fe-128">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="f94fe-128">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="f94fe-129">В **установленные шаблоны** области, выберите Visual Basic, а затем выберите **приложение WPF** в списке типов проектов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="f94fe-130">В текстовом поле **Имя** введите `AsyncExampleWPF` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="f94fe-131">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="f94fe-131">The new project appears in **Solution Explorer**.</span></span>  
  
## <a name="BKMK_DesignWPFMainWin"></a>   
### <a name="MainWindow"></a> <span data-ttu-id="f94fe-132">Разработка простого окна MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="f94fe-132">To design a simple WPF MainWindow</span></span>  
  
1. <span data-ttu-id="f94fe-133">В редакторе кода Visual Studio перейдите на вкладку **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="f94fe-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2. <span data-ttu-id="f94fe-134">Если окно **Панель элементов** не отображается, в меню **Вид** выберите пункт **Панель элементов**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3. <span data-ttu-id="f94fe-135">Добавьте элементы управления **Button** и **TextBox** в окно **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4. <span data-ttu-id="f94fe-136">Выделите элемент управления **TextBox** и в окне **Свойства** задайте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="f94fe-137">Задайте для свойства **Имя** значение `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="f94fe-138">Задайте для свойства **Высота** значение 250.</span><span class="sxs-lookup"><span data-stu-id="f94fe-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="f94fe-139">Задайте для свойства **Ширина** значение 500.</span><span class="sxs-lookup"><span data-stu-id="f94fe-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="f94fe-140">На вкладке **Текст** укажите моноширинный шрифт, например Lucida Console или Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="f94fe-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5. <span data-ttu-id="f94fe-141">Выделите элемент управления **Button** и в окне **Свойства** задайте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="f94fe-142">Задайте для свойства **Имя** значение `startButton`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="f94fe-143">Измените значение свойства **Содержимое** с **Button** на **Start**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6. <span data-ttu-id="f94fe-144">Поместите текстовое поле и кнопку так, чтобы оба элемента управления отображались в окне **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="f94fe-145">Дополнительные сведения о конструкторе XAML WPF см. в разделе [Создание пользовательского интерфейса с помощью конструктора XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f94fe-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
## <a name="BKMK_AddReference"></a>   
### <a name="AddRef"></a> <span data-ttu-id="f94fe-146">Добавление ссылки</span><span class="sxs-lookup"><span data-stu-id="f94fe-146">To add a reference</span></span>  
  
1. <span data-ttu-id="f94fe-147">В **обозревателе решений** выделите имя проекта.</span><span class="sxs-lookup"><span data-stu-id="f94fe-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2. <span data-ttu-id="f94fe-148">В строке меню выберите **Проект**, **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="f94fe-149">Откроется диалоговое окно **Диспетчер ссылок**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-149">The **Reference Manager** dialog box appears.</span></span>  
  
3. <span data-ttu-id="f94fe-150">Вверху диалогового окна убедитесь в том, что проект предназначен для платформы .NET Framework 4.5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f94fe-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4. <span data-ttu-id="f94fe-151">В области **Сборки** выберите **Платформа**, если этот вариант еще не выбран.</span><span class="sxs-lookup"><span data-stu-id="f94fe-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5. <span data-ttu-id="f94fe-152">В списке имен установите флажок **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6. <span data-ttu-id="f94fe-153">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="f94fe-153">Choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="BKMK_AddStatesandDirs"></a>   
### <a name="ImportsState"></a> <span data-ttu-id="f94fe-154">Добавление необходимых операторов Imports</span><span class="sxs-lookup"><span data-stu-id="f94fe-154">To add necessary Imports statements</span></span>  
  
1. <span data-ttu-id="f94fe-155">В **обозревателе решений**, откройте контекстное меню для MainWindow.xaml.vb и затем выберите **Просмотр кода**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2. <span data-ttu-id="f94fe-156">Добавьте следующий `Imports` инструкций в верхней части файла кода, если они еще не существуют.</span><span class="sxs-lookup"><span data-stu-id="f94fe-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
## <a name="BKMK_CreatSynchApp"></a>   
### <a name="synchronous"></a> <span data-ttu-id="f94fe-157">Создание синхронного приложения</span><span class="sxs-lookup"><span data-stu-id="f94fe-157">To create a synchronous application</span></span>  
  
1. <span data-ttu-id="f94fe-158">В окне конструктора для MainWindow.xaml дважды щелкните **запустить** кнопку, чтобы создать `startButton_Click` обработчик событий в файле MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="f94fe-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2. <span data-ttu-id="f94fe-159">В файле MainWindow.xaml.vb, скопируйте следующий код в текст `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="f94fe-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="f94fe-160">Код вызывает метод, который управляет приложением `SumPageSizes` и выводит на экран сообщение, когда элемент управления возвращается к `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3. <span data-ttu-id="f94fe-161">Код для синхронного решения содержит следующие четыре метода:</span><span class="sxs-lookup"><span data-stu-id="f94fe-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   `SumPageSizes`<span data-ttu-id="f94fe-162">, который получает список URL-адреса веб-странице из `SetUpURLList` , а затем вызывает `GetURLContents` и `DisplayResults` для обработки каждого URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="f94fe-162">, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   `SetUpURLList`<span data-ttu-id="f94fe-163">, который создает и возвращает список веб-адреса.</span><span class="sxs-lookup"><span data-stu-id="f94fe-163">, which makes and returns a list of web addresses.</span></span>  
  
    -   `GetURLContents`<span data-ttu-id="f94fe-164">, который загружает содержимое каждого веб-сайта и возвращает содержимое в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-164">, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   `DisplayResults`<span data-ttu-id="f94fe-165">, отображающий число байтов в массиве байтов для каждого URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="f94fe-165">, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="f94fe-166">Скопируйте следующие четыре метода, а затем вставьте их в разделе `startButton_Click` обработчик событий в файле MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="f94fe-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
## <a name="BKMK_TestSynchSol"></a>   
### <a name="testSynch"></a> <span data-ttu-id="f94fe-167">Тестирование синхронного решения</span><span class="sxs-lookup"><span data-stu-id="f94fe-167">To test the synchronous solution</span></span>  
  
1. <span data-ttu-id="f94fe-168">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="f94fe-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="f94fe-169">Программа должна выдать результаты, похожие на следующий список.</span><span class="sxs-lookup"><span data-stu-id="f94fe-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     <span data-ttu-id="f94fe-170">Обратите внимание, что вывод результатов на экран занимает несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="f94fe-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="f94fe-171">В течение этого времени поток пользовательского интерфейса заблокирован, пока он ожидает загрузку запрошенных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="f94fe-172">Соответственно, после нажатия кнопки **Start** окно нельзя перемещать, разворачивать, сворачивать или даже закрывать.</span><span class="sxs-lookup"><span data-stu-id="f94fe-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="f94fe-173">Эти действия будут завершаться сбоем, пока не появятся результаты подсчета.</span><span class="sxs-lookup"><span data-stu-id="f94fe-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="f94fe-174">Если веб-сайт не отвечает, вы не можете определить, на каком сайте произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="f94fe-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="f94fe-175">Трудно даже остановить ожидание и закрыть программу.</span><span class="sxs-lookup"><span data-stu-id="f94fe-175">It is difficult even to stop waiting and close the program.</span></span>  
  
## <a name="BKMK_ConvertGtBtArr"></a>   
### <a name="GetURLContents"></a> <span data-ttu-id="f94fe-176">Преобразование GetURLContents в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1. <span data-ttu-id="f94fe-177">Чтобы преобразовать синхронное решение в асинхронное, лучше всего начать с метода `GetURLContents`, поскольку вызовы метода <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> и метода <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> выполняются, когда приложение подключается к Интернету.</span><span class="sxs-lookup"><span data-stu-id="f94fe-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="f94fe-178">Платформа .NET Framework упрощает преобразование путем предоставления асинхронных версий этих методов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="f94fe-179">Дополнительные сведения о методах, которые используются в `GetURLContents`, см. в разделе <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f94fe-180">По мере выполнения шагов в этом пошаговом руководстве возникают различные ошибки компилятора.</span><span class="sxs-lookup"><span data-stu-id="f94fe-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="f94fe-181">Их можно игнорировать и продолжить процедуры пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="f94fe-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="f94fe-182">Измените метод, который вызывается в третьей строке `GetURLContents` из `GetResponse`, асинхронным методом <xref:System.Net.WebRequest.GetResponseAsync%2A>, основанным на задачах.</span><span class="sxs-lookup"><span data-stu-id="f94fe-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2. `GetResponseAsync` <span data-ttu-id="f94fe-183">Возвращает <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-183">returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f94fe-184">В этом случае *переменная, возвращаемая задачей*, `TResult`, имеет тип <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="f94fe-185">Задача является обещанием создать фактический объект `WebResponse` после загрузки запрошенных данных и выполнения задачи до завершения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="f94fe-186">Для получения `WebResponse` значения из задачи, применить [Await](../../../../visual-basic/language-reference/operators/await-operator.md) оператор для вызова `GetResponseAsync`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="f94fe-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="f94fe-187">Оператор `Await` приостанавливает выполнение текущего метода `GetURLContents`, пока не будет завершена ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="f94fe-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="f94fe-188">На это время управление возвращается вызывающему объекту текущего метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="f94fe-189">В этом примере текущим методом является `GetURLContents`, а вызывающим объектом — `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="f94fe-190">После завершения задачи создается обещанный объект `WebResponse` в качестве значения ожидаемой задачи, который присваивается переменной `response`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="f94fe-191">Предыдущий оператор можно разделить на следующие два оператора для уточнения выполняемых операций.</span><span class="sxs-lookup"><span data-stu-id="f94fe-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="f94fe-192">Вызов `webReq.GetResponseAsync` возвращает `Task(Of WebResponse)` или `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="f94fe-193">Затем `Await` оператор применяется к задаче для получения `WebResponse` значение.</span><span class="sxs-lookup"><span data-stu-id="f94fe-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="f94fe-194">Если асинхронный метод выполняет какие-то действия, это не зависит от выполнения задачи, метод может продолжать свои действия между выполнениями этих двух операторов: после вызова асинхронного метода и перед применением оператора await.</span><span class="sxs-lookup"><span data-stu-id="f94fe-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="f94fe-195">Примеры см. в разделах [Практическое руководство. Параллельное выполнение нескольких веб-запросов с использованием Async и Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) и [как: Расширение Async пошагового руководства с использованием метода Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f94fe-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3. <span data-ttu-id="f94fe-196">Из-за добавления оператора `Await` в предыдущем шаге возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="f94fe-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="f94fe-197">Оператор может использоваться только в методах, которые помечены атрибутом [Async](../../../../visual-basic/language-reference/modifiers/async.md) модификатор.</span><span class="sxs-lookup"><span data-stu-id="f94fe-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f94fe-198">Пропустите ошибку, повторяя действия по замене вызова `CopyTo` вызовом метода `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="f94fe-199">Измените имя метода, вызывающего <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="f94fe-200">Метод `CopyTo` или `CopyToAsync` копирует байты в свой аргумент `content` и не возвращает осмысленное значение.</span><span class="sxs-lookup"><span data-stu-id="f94fe-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="f94fe-201">В синхронной версии вызов метода `CopyTo` — это просто оператор, который не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="f94fe-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="f94fe-202">Асинхронная версия — `CopyToAsync` — возвращает <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f94fe-203">Задача работает как Task(void) и позволяет ожидать метод.</span><span class="sxs-lookup"><span data-stu-id="f94fe-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="f94fe-204">Примените `Await` или `await` к вызову `CopyToAsync`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="f94fe-205">Предыдущий оператор сокращает две следующие строки кода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4. <span data-ttu-id="f94fe-206">Все, что остается сделать в `GetURLContents`, — это изменить подпись метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="f94fe-207">Можно использовать `Await` оператор только в методах, которые помечены атрибутом [Async](../../../../visual-basic/language-reference/modifiers/async.md) модификатор.</span><span class="sxs-lookup"><span data-stu-id="f94fe-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f94fe-208">Добавьте модификатор, чтобы пометить метод как *асинхронный*, как показано в приведенном ниже примере кода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5. <span data-ttu-id="f94fe-209">Тип возвращаемого значения асинхронного метода может быть только <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f94fe-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f94fe-210">В Visual Basic метод должен являться функцией `Function`, возвращающей `Task` или `Task(Of T)`, либо он должен быть `Sub`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="f94fe-211">Как правило `Sub` метод используется только в асинхронном обработчике событий, где `Sub` является обязательным.</span><span class="sxs-lookup"><span data-stu-id="f94fe-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="f94fe-212">В других случаях используется `Task(T)` Если завершенный метод имеет [возвращают](../../../../visual-basic/language-reference/statements/return-statement.md) инструкцию, которая возвращает значение типа T, или использовании `Task` Если завершенный метод не возвращает осмысленное значение.</span><span class="sxs-lookup"><span data-stu-id="f94fe-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="f94fe-213">Дополнительные сведения см. в разделе [асинхронные типы возвращаемых значений (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f94fe-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="f94fe-214">Метод `GetURLContents` имеет оператор return, который возвращает массив байтов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="f94fe-215">Таким образом, тип возвращаемого значения асинхронной версии — Task(T), где T — массив байтов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="f94fe-216">Внесите следующие изменения в подпись метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="f94fe-217">Измените тип возвращаемого значения на `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="f94fe-218">По соглашению об именовании асинхронные методы имеют имена, заканчивающиеся на Async, поэтому переименуйте метод в `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="f94fe-219">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="f94fe-220">После внесения этих изменений преобразование `GetURLContents` в асинхронный метод завершено.</span><span class="sxs-lookup"><span data-stu-id="f94fe-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
## <a name="BKMK_ConvertSumPagSzs"></a>   
### <a name="SumPageSizes"></a> <span data-ttu-id="f94fe-221">Преобразование SumPageSizes в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1. <span data-ttu-id="f94fe-222">Повторите шаги из предыдущей процедуры для `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="f94fe-223">Во-первых, преобразуйте вызов метода `GetURLContents` в вызов асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="f94fe-224">Измените имя вызываемого метода с `GetURLContents` на `GetURLContentsAsync`, если это еще не сделано.</span><span class="sxs-lookup"><span data-stu-id="f94fe-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="f94fe-225">Примените оператор `Await` к задаче, возвращаемой методом `GetURLContentsAsync`, для получения значения байтового массива.</span><span class="sxs-lookup"><span data-stu-id="f94fe-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="f94fe-226">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="f94fe-227">Предыдущее назначение сокращает две следующие строки кода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2. <span data-ttu-id="f94fe-228">Внесите следующие изменения в подпись метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="f94fe-229">Пометьте метод модификатором `Async`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-229">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="f94fe-230">Добавьте в имя метода Async.</span><span class="sxs-lookup"><span data-stu-id="f94fe-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="f94fe-231">В этот раз нет возвращаемой переменной задачи T, поскольку `SumPageSizesAsync` не возвращает значение для T. (В этом методе нет оператора `Return`.) Тем не менее метод должен возвращать `Task`, чтобы для него можно было задать ожидание.</span><span class="sxs-lookup"><span data-stu-id="f94fe-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="f94fe-232">Таким образом, измените тип метода из `Sub` для `Function`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="f94fe-233">Тип значения, возвращаемого функцией, — `Task`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="f94fe-234">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="f94fe-235">Преобразование `SumPageSizes` в `SumPageSizesAsync` завершено.</span><span class="sxs-lookup"><span data-stu-id="f94fe-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
## <a name="BKMK_Cnvrtbttn1"></a>   
### <a name="startButton"></a> <span data-ttu-id="f94fe-236">Преобразование startButton_Click в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="f94fe-236">To convert startButton_Click to an asynchronous method</span></span>  
  
1. <span data-ttu-id="f94fe-237">В обработчике событий измените имя вызываемого метода с `SumPageSizes` на `SumPageSizesAsync`, если это еще не сделано.</span><span class="sxs-lookup"><span data-stu-id="f94fe-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2. <span data-ttu-id="f94fe-238">Поскольку `SumPageSizesAsync` является асинхронным методом, измените код в обработчике событий для ожидания результата.</span><span class="sxs-lookup"><span data-stu-id="f94fe-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="f94fe-239">Вызов `SumPageSizesAsync` отражает вызов `CopyToAsync` в `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="f94fe-240">Вызов возвращает `Task`, а не `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="f94fe-241">Как и в предыдущих процедурах, вызов можно преобразовать, используя один или два оператора.</span><span class="sxs-lookup"><span data-stu-id="f94fe-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="f94fe-242">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3. <span data-ttu-id="f94fe-243">Чтобы предотвратить случайное повторное введение операции, добавьте следующий оператор в верхней части `startButton_Click`, чтобы отключить кнопку **Start**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="f94fe-244">Можно снова включить кнопку в конце обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="f94fe-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="f94fe-245">Дополнительные сведения о повторном входе см. в разделе [обработка повторного входа в асинхронных приложениях (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f94fe-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4. <span data-ttu-id="f94fe-246">Наконец, добавьте модификатор `Async` в объявление, чтобы обработчик событий мог ожидать `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="f94fe-247">Как правило, имена обработчиков событий не изменяются.</span><span class="sxs-lookup"><span data-stu-id="f94fe-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="f94fe-248">Тип возвращаемого значения не изменяется на `Task` поскольку обработчики событий должны быть `Sub` процедуры в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f94fe-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="f94fe-249">Преобразование проекта из синхронного в асинхронный завершено.</span><span class="sxs-lookup"><span data-stu-id="f94fe-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
## <a name="BKMK_testAsynchSolution"></a>   
### <a name="testAsynch"></a> <span data-ttu-id="f94fe-250">Тестирование асинхронного решения</span><span class="sxs-lookup"><span data-stu-id="f94fe-250">To test the asynchronous solution</span></span>  
  
1. <span data-ttu-id="f94fe-251">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="f94fe-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2. <span data-ttu-id="f94fe-252">Появившиеся результаты должны напоминать результаты синхронного решения.</span><span class="sxs-lookup"><span data-stu-id="f94fe-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="f94fe-253">Однако имеются следующие различия.</span><span class="sxs-lookup"><span data-stu-id="f94fe-253">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="f94fe-254">Все результаты не отображаются одновременно после завершения обработки.</span><span class="sxs-lookup"><span data-stu-id="f94fe-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="f94fe-255">Например, обе программы содержат строку в `startButton_Click`, которая очищает текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="f94fe-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="f94fe-256">Ее цель состоит в том, чтобы очистить текстовое поле между запусками при нажатии кнопки **Start** во второй раз после появления одного набора результатов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="f94fe-257">В синхронной версии текстовое поле очищается перед отображением данных во второй раз, после завершения загрузки и высвобождения потока пользовательского интерфейса для выполнения других операций.</span><span class="sxs-lookup"><span data-stu-id="f94fe-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="f94fe-258">В асинхронной версии текстовое поле очищается сразу же после нажатия кнопки **Start**.</span><span class="sxs-lookup"><span data-stu-id="f94fe-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="f94fe-259">И что самое главное, поток пользовательского интерфейса не блокируется во время загрузки.</span><span class="sxs-lookup"><span data-stu-id="f94fe-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="f94fe-260">Можно перемещать окно или изменять его размер во время загрузки, подсчета и отображения веб-ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f94fe-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="f94fe-261">Если один из веб-сайтов работает медленно или не отвечает, можно отменить операцию, нажав кнопку **Закрыть** (красный крестик в правом верхнем углу окна).</span><span class="sxs-lookup"><span data-stu-id="f94fe-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
## <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
### <a name="GetURLContentsAsync"></a> <span data-ttu-id="f94fe-262">Замена GetURLContentsAsync методом .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f94fe-262">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1. <span data-ttu-id="f94fe-263">Платформа .NET Framework 4.5 предоставляет много асинхронных методов, которые вы можете использовать.</span><span class="sxs-lookup"><span data-stu-id="f94fe-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="f94fe-264">Один из них, метод <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> <xref:System.Net.Http.HttpClient>, выполняет именно те операции, которые требуются для данного пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="f94fe-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="f94fe-265">Его можно использовать вместо метода `GetURLContentsAsync`, созданного в предыдущей процедуре.</span><span class="sxs-lookup"><span data-stu-id="f94fe-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="f94fe-266">Первым шагом является создание объекта `HttpClient` в методе `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="f94fe-267">Добавьте следующее объявление в начале метода.</span><span class="sxs-lookup"><span data-stu-id="f94fe-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2. <span data-ttu-id="f94fe-268">В `SumPageSizesAsync,` замените вызов метода `GetURLContentsAsync` вызовом метода `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3. <span data-ttu-id="f94fe-269">Удалите или прокомментируйте метод `GetURLContentsAsync`, который вы написали.</span><span class="sxs-lookup"><span data-stu-id="f94fe-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4. <span data-ttu-id="f94fe-270">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="f94fe-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="f94fe-271">Поведение этой версии проекта должно соответствовать поведению, которое описывается в процедуре "Тестирование асинхронного решения"; при этом с вашей стороны требуется даже меньше усилий.</span><span class="sxs-lookup"><span data-stu-id="f94fe-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
## <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="f94fe-272">Пример</span><span class="sxs-lookup"><span data-stu-id="f94fe-272">Example</span></span>  
 <span data-ttu-id="f94fe-273">Следующий код содержит полный пример преобразования решения из синхронного в асинхронное с помощью написанного вами асинхронного метода `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="f94fe-274">Обратите внимание, что он очень напоминает исходное синхронное решение.</span><span class="sxs-lookup"><span data-stu-id="f94fe-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="f94fe-275">Следующий код содержит полный пример решения, использующего метод `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="f94fe-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="f94fe-276">См. также</span><span class="sxs-lookup"><span data-stu-id="f94fe-276">See also</span></span>

- [<span data-ttu-id="f94fe-277">Пример асинхронности. Доступ к Пошаговое руководство (C# и Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="f94fe-278">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="f94fe-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="f94fe-279">Async</span><span class="sxs-lookup"><span data-stu-id="f94fe-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="f94fe-280">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f94fe-281">Асинхронные типы возвращаемых значений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="f94fe-282">Асинхронное программирование на основе задач (TAP)</span><span class="sxs-lookup"><span data-stu-id="f94fe-282">Task-based Asynchronous Programming (TAP)</span></span>](https://go.microsoft.com/fwlink/?LinkId=204847)
- [<span data-ttu-id="f94fe-283">Практическое руководство. Расширение Async пошагового руководства с использованием метода Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="f94fe-284">Практическое руководство. Параллельное выполнение нескольких веб-запросов с использованием Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f94fe-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
