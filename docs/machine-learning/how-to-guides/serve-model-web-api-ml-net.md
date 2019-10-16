---
title: Развертывание модели в веб-API ASP.NET Core
description: Использование модели машинного обучения ML.NET для анализа тональности через Интернет с помощью веб-API ASP.NET Core
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 42f8d51f2547cd6f3240a05420b2da10b7cf52e3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179396"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="1ee0a-103">Развертывание модели в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ee0a-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="1ee0a-104">Узнайте, как использовать предварительно обученную модель машинного обучения ML.NET через интернет с помощью веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="1ee0a-105">Обслуживание модели через веб-API позволяет формировать прогнозы с помощью стандартных методов HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="1ee0a-106">Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ee0a-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="1ee0a-107">Prerequisites</span></span>

- <span data-ttu-id="1ee0a-108">[Visual Studio 2017 15.6 или более поздней версии](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="1ee0a-109">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-109">Powershell.</span></span>
- <span data-ttu-id="1ee0a-110">Предварительно обученная модель.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-110">Pre-trained model.</span></span> <span data-ttu-id="1ee0a-111">Используйте [учебник по анализу тональности ML.NET](../tutorials/sentiment-analysis.md), чтобы создать собственную модель, или скачайте эту [предварительно обученную модель машинного обучения для анализа тональности](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="1ee0a-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="1ee0a-112">Создание проекта веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ee0a-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="1ee0a-113">Откройте Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="1ee0a-114">В меню выберите **Файл > Новый > Проект**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="1ee0a-115">В диалоговом окне "Новый проект" щелкните узел **Visual C#** , а затем — **Веб**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="1ee0a-116">Затем, выберите шаблон проекта **Веб-приложение ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="1ee0a-117">В текстовое поле **Имя** введите SentimentAnalysisWebAPI и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="1ee0a-118">В окне с разными типами проектов ASP.NET Core выберите **API** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="1ee0a-119">Создайте каталог с именем *MLModels* в папке проекта, чтобы сохранить предварительно созданные файлы модели машинного обучения:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="1ee0a-120">В обозревателе решений щелкните проект правой кнопкой мыши и выберите "Добавить" > "Новая папка".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="1ee0a-121">Введите MLModels и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="1ee0a-122">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1ee0a-123">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1ee0a-124">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.ML**, выберите из списка этот пакет и нажмите кнопку "Установить".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="1ee0a-125">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**. Затем нажмите кнопку **Принимаю** в диалоговом окне "Принятие условий лицензионного соглашения", если вы согласны с условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="1ee0a-126">Установите **пакет NuGet для Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="1ee0a-127">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1ee0a-128">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Extensions.ML**, выберите из списка этот пакет и нажмите кнопку "Установить".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="1ee0a-129">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**. Затем нажмите кнопку **Принимаю** в диалоговом окне "Принятие условий лицензионного соглашения", если вы согласны с условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="1ee0a-130">Добавление модели в проект веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ee0a-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="1ee0a-131">Скопируйте предварительно созданную модель в каталог *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="1ee0a-132">В обозревателе решений щелкните правой кнопкой мыши ZIP-файл модели и выберите пункт "Свойства".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="1ee0a-133">В разделе "Дополнительно" для параметра "Копировать в выходной каталог" установите значение "Копировать более позднюю версию".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="1ee0a-134">Создание моделей данных</span><span class="sxs-lookup"><span data-stu-id="1ee0a-134">Create data models</span></span>

<span data-ttu-id="1ee0a-135">Вам потребуется создать несколько классов для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="1ee0a-136">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="1ee0a-137">Создайте каталог с именем *DataModels* в папке проекта, чтобы сохранить в нем модели данных:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="1ee0a-138">В обозревателе решений щелкните проект правой кнопкой мыши и выберите "Добавить" > "Новая папка".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="1ee0a-139">Введите DataModels и нажмите клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="1ee0a-140">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите "Добавить" > "Новый элемент".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="1ee0a-141">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="1ee0a-142">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-142">Then, select the **Add** button.</span></span> <span data-ttu-id="1ee0a-143">Файл *SentimentData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="1ee0a-144">Добавьте в начало файла *SentimentData.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="1ee0a-145">Удалите из файла **SentimentData.cs** существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="1ee0a-146">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="1ee0a-147">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="1ee0a-148">Теперь нажмите кнопку "Добавить".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-148">Then, select the Add button.</span></span> <span data-ttu-id="1ee0a-149">В редакторе кода откроется файл *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="1ee0a-150">Добавьте в начало файла *SentimentPrediction.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="1ee0a-151">Удалите из файла *SentimentPrediction.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="1ee0a-152">Тип`SentimentPrediction` наследуется от типа `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="1ee0a-153">Это упрощает просмотр исходных данных в свойстве `SentimentText`, а также выходных данных модели.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="1ee0a-154">Регистрация класса PredictionEnginePool для использования в приложении</span><span class="sxs-lookup"><span data-stu-id="1ee0a-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="1ee0a-155">Для формирования одного прогноза необходимо создать [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="1ee0a-155">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="1ee0a-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="1ee0a-157">Кроме того, необходимо создать его экземпляр везде, где он понадобится в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-157">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="1ee0a-158">По мере увеличения размера приложения этот процесс может стать неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-158">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="1ee0a-159">Для улучшенной производительности и потокобезопасности используйте сочетание внедрения зависимостей и службы `PredictionEnginePool`, которое создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-159">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="1ee0a-160">См. дополнительные сведения о [внедрении зависимостей в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="1ee0a-160">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="1ee0a-161">Откройте класс *Startup.cs* и добавьте в начало файла следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-161">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="1ee0a-162">Добавьте в метод *ConfigureServices* следующий код:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-162">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    }
    ```

<span data-ttu-id="1ee0a-163">Вкратце, этот код инициализирует объекты и службы автоматически для использования в дальнейшем по запросу приложения, вместо того чтобы вы делали это вручную.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-163">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span> 

<span data-ttu-id="1ee0a-164">Модели машинного обучения не являются статическими.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-164">Machine learning models are not static.</span></span> <span data-ttu-id="1ee0a-165">По мере появления новых данных для обучения модель переобучается и развертывается повторно.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-165">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="1ee0a-166">Одним из способов получения последней версии модели в приложении является повторное развертывание всего приложения.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-166">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="1ee0a-167">Однако это приводит к простою приложения.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-167">However, this introduces application downtime.</span></span> <span data-ttu-id="1ee0a-168">Служба `PredictionEnginePool` предоставляет механизм перезагрузки обновленной модели без отключения приложения.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-168">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span> 

<span data-ttu-id="1ee0a-169">Задайте для параметра `watchForChanges` значение `true`. В таком случае `PredictionEnginePool` запустит объект [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher), который прослушивает уведомления об изменениях файловой системы и вызывает события при изменении файла.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-169">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="1ee0a-170">При наличии изменений `PredictionEnginePool` автоматически перезагружает модель.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-170">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="1ee0a-171">Модель определяется параметром `modelName`, поэтому при изменении может быть перезагружено несколько моделей на одно приложение.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-171">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span> 

> [!TIP]
> <span data-ttu-id="1ee0a-172">Кроме того, можно использовать метод `FromUri` при работе с моделями, сохраненными удаленно.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-172">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="1ee0a-173">Вместо наблюдения за событиями изменения файлов `FromUri` опрашивает удаленное расположение на предмет изменений.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-173">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="1ee0a-174">Интервал опроса по умолчанию равен 5 минутам.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-174">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="1ee0a-175">Вы можете увеличить или уменьшить интервал опроса в зависимости от требований вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-175">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="1ee0a-176">В приведенном ниже примере кода `PredictionEnginePool` опрашивает модель, сохраненную по указанному универсальному коду ресурса (URI), каждую минуту.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-176">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>    
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel", 
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip", 
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="1ee0a-177">Создание контроллера прогнозирования</span><span class="sxs-lookup"><span data-stu-id="1ee0a-177">Create Predict controller</span></span>

<span data-ttu-id="1ee0a-178">Для обработки входящих HTTP-запросов создайте контроллер.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-178">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="1ee0a-179">В обозревателе решений щелкните правой кнопкой мыши папку *Контроллеры* и выберите **Добавить > Контроллер**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-179">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="1ee0a-180">В диалоговом окне **Добавление нового элемента** щелкните **Пустой контроллер API** и нажмите **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-180">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="1ee0a-181">В запросе измените поле **Имя контроллера** на *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-181">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="1ee0a-182">Теперь нажмите кнопку "Добавить".</span><span class="sxs-lookup"><span data-stu-id="1ee0a-182">Then, select the Add button.</span></span> <span data-ttu-id="1ee0a-183">Файл *PredictController.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-183">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="1ee0a-184">Добавьте в начало файла *PredictController.cs* следующий оператор using.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-184">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="1ee0a-185">Удалите из файла *PredictController.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-185">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="1ee0a-186">Этот код назначает класс `PredictionEnginePool`, передав его в конструктор контроллера, который можно получить путем внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-186">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="1ee0a-187">Затем метод `Post` контроллера `Predict` использует `PredictionEnginePool` для формирования прогнозов с помощью модели `SentimentAnalysisModel`, зарегистрированной в классе `Startup`, и возвращает результаты пользователю в случае успеха.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-187">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="1ee0a-188">Тестирование веб-API на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="1ee0a-188">Test web API locally</span></span>

<span data-ttu-id="1ee0a-189">Завершив настройку параметров, протестируйте приложение:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-189">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="1ee0a-190">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-190">Run the application.</span></span>
1. <span data-ttu-id="1ee0a-191">Откройте PowerShell и введите следующий код, где PORT — это порт, через который приложение ожидает передачи денных.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-191">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="1ee0a-192">В случае успешного выполнения результат должен выглядеть, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="1ee0a-192">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="1ee0a-193">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1ee0a-193">Congratulations!</span></span> <span data-ttu-id="1ee0a-194">Вы успешно использовали модель для прогнозирования через Интернет с помощью веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ee0a-194">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1ee0a-195">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="1ee0a-195">Next Steps</span></span>

- [<span data-ttu-id="1ee0a-196">Развертывание в Azure</span><span class="sxs-lookup"><span data-stu-id="1ee0a-196">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
