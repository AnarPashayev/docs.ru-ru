---
title: Отслеживание SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559354"
---
# <a name="sql-tracking"></a><span data-ttu-id="163da-102">Отслеживание SQL</span><span class="sxs-lookup"><span data-stu-id="163da-102">SQL tracking</span></span>

<span data-ttu-id="163da-103">В этом примере демонстрируется написание пользовательского участника отслеживания SQL, записывающего записи отслеживания в базу данных SQL.</span><span class="sxs-lookup"><span data-stu-id="163da-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="163da-104">Windows Workflow Foundation (WF) обеспечивает отслеживание рабочих процессов, чтобы получить сведения о выполнении экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="163da-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="163da-105">Среда выполнения отслеживания выдает записи отслеживания рабочего процесса в ходе его выполнения.</span><span class="sxs-lookup"><span data-stu-id="163da-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="163da-106">Дополнительные сведения об отслеживании рабочих процессов см. в разделе [Отслеживание и трассировка рабочих процессов](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="163da-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="163da-107">Использование примера</span><span class="sxs-lookup"><span data-stu-id="163da-107">Use the sample</span></span>

1. <span data-ttu-id="163da-108">Убедитесь, что на компьютере установлен SQL Server 2008, SQL Server 2008 Express или более новая версия.</span><span class="sxs-lookup"><span data-stu-id="163da-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="163da-109">Скрипты, упакованные в состав образца, предполагают использование экземпляра SQL Express на локальном компьютере пользователя.</span><span class="sxs-lookup"><span data-stu-id="163da-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="163da-110">Если вы работаете с другим экземпляром, до запуска образца следует внести изменения в скрипты, относящиеся к базе данных.</span><span class="sxs-lookup"><span data-stu-id="163da-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="163da-111">Создание базы данных отслеживания на SQL Server посредством запуска команды Trackingsetup.cmd в каталоге скриптов (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="163da-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="163da-112">Создает базу данных с именем TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="163da-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="163da-113">Этот скрипт создает базу данных на экземпляре SQL Express по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="163da-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="163da-114">Если установку необходимо произвести на другом экземпляре базы данных, внесите изменения в скрипт Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="163da-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="163da-115">Откройте Склтраккингсампле. sln в Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="163da-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="163da-116">Нажмите клавиши **CTRL** + **SHIFT** + **B** , чтобы построить решение.</span><span class="sxs-lookup"><span data-stu-id="163da-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="163da-117">Нажмите клавишу **F5** для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="163da-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="163da-118">Откроется окно браузера со списком каталогов для приложения.</span><span class="sxs-lookup"><span data-stu-id="163da-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="163da-119">Щелкните файл StockPriceService.xamlx в браузере.</span><span class="sxs-lookup"><span data-stu-id="163da-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="163da-120">В браузере отображается страница StockPriceService, содержащая адрес WSDL локальной службы.</span><span class="sxs-lookup"><span data-stu-id="163da-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="163da-121">Скопируйте этот адрес.</span><span class="sxs-lookup"><span data-stu-id="163da-121">Copy this address.</span></span>

   <span data-ttu-id="163da-122">Пример адреса WSDL локальной службы — `http://localhost:65193/StockPriceService.xamlx?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="163da-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="163da-123">С помощью проводника запустите тестовый клиент WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="163da-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="163da-124">Он находится в *каталоге Microsoft Visual Studio 10.0 \ Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="163da-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="163da-125">В тестовом клиенте WCF щелкните меню **файл** и выберите **Добавить службу**.</span><span class="sxs-lookup"><span data-stu-id="163da-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="163da-126">Вставьте в текстовое поле адрес локальной службы.</span><span class="sxs-lookup"><span data-stu-id="163da-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="163da-127">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="163da-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="163da-128">В тестовом клиенте WCF дважды щелкните **жетстоккприце**.</span><span class="sxs-lookup"><span data-stu-id="163da-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="163da-129">Откроется `GetStockPrice` операция, которая принимает один параметр, введите значение `Contoso` и нажмите кнопку **вызвать**.</span><span class="sxs-lookup"><span data-stu-id="163da-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="163da-130">Выданные записи отслеживания будут записаны в базу данных SQL.</span><span class="sxs-lookup"><span data-stu-id="163da-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="163da-131">Чтобы просмотреть записи отслеживания, откройте базу данных TrackingSample в среде SQL Management Studio и перейдите в раздел просмотра таблиц.</span><span class="sxs-lookup"><span data-stu-id="163da-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="163da-132">Применение запроса select для таблиц выводит соответствующие данные записей отслеживания, хранимых в соответствующих таблицах.</span><span class="sxs-lookup"><span data-stu-id="163da-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="163da-133">Дополнительные сведения о SQL Server Management Studio см. в разделе [введение SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="163da-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="163da-134">Скачайте SQL Server Management Studio [здесь](https://aka.ms/ssmsfullsetup).</span><span class="sxs-lookup"><span data-stu-id="163da-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="163da-135">Удаление образца</span><span class="sxs-lookup"><span data-stu-id="163da-135">Uninstall the sample</span></span>

1. <span data-ttu-id="163da-136">Запустите сценарий Сетраккингклеануп. cmd в каталоге примеров (*\вф\басик\траккинг\склтраккинг*).</span><span class="sxs-lookup"><span data-stu-id="163da-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="163da-137">Скрипт Trackingcleanup.cmd пытается удалить базу данных, хранящуюся в SQL Express вашего локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="163da-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="163da-138">При использовании другого экземпляра сервера SQL следует внести изменения в скрипт Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="163da-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="163da-139">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="163da-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="163da-140">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="163da-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="163da-141">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="163da-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="163da-142">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="163da-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="163da-143">См. также</span><span class="sxs-lookup"><span data-stu-id="163da-143">See also</span></span>

- <span data-ttu-id="163da-144">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="163da-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
