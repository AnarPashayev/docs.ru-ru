---
title: Учебник. Анализ комментариев на веб-сайте — двоичная классификация
description: В этом руководстве показано, как создать консольное приложение .NET Core, которое классифицирует мнения, выраженные в комментариях с веб-сайта, и предпринимает соответствующие действия. Двоичный классификатор тональности использует C# в Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 2dc4d68eb6a3aa5890e4d091e33c4624d79317e9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238376"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="4bf8f-104">Учебник. Анализ мнений пользователей в комментариях с веб-сайта с помощью двоичной классификации в ML.NET</span><span class="sxs-lookup"><span data-stu-id="4bf8f-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="4bf8f-105">В этом руководстве показано, как создать консольное приложение .NET Core, которое классифицирует мнения, выраженные в комментариях с веб-сайта, и предпринимает соответствующие действия.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="4bf8f-106">Двоичный классификатор тональности использует C# в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="4bf8f-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4bf8f-108">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="4bf8f-108">Create a console application</span></span>
> * <span data-ttu-id="4bf8f-109">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-109">Prepare data</span></span>
> * <span data-ttu-id="4bf8f-110">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-110">Load the data</span></span>
> * <span data-ttu-id="4bf8f-111">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-111">Build and train the model</span></span>
> * <span data-ttu-id="4bf8f-112">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-112">Evaluate the model</span></span>
> * <span data-ttu-id="4bf8f-113">Использование модели для прогноза</span><span class="sxs-lookup"><span data-stu-id="4bf8f-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="4bf8f-114">Просмотр результатов</span><span class="sxs-lookup"><span data-stu-id="4bf8f-114">See the results</span></span>

<span data-ttu-id="4bf8f-115">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4bf8f-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4bf8f-116">Prerequisites</span></span>

* <span data-ttu-id="4bf8f-117">[Visual Studio 2017 15.6 или более поздней версии](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="4bf8f-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="4bf8f-118">[Набор данных — предложения с меткой тональности UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP-файл)</span><span class="sxs-lookup"><span data-stu-id="4bf8f-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4bf8f-119">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="4bf8f-119">Create a console application</span></span>

1. <span data-ttu-id="4bf8f-120">Создайте **консольное приложение .NET Core** с именем SentimentAnalysis.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="4bf8f-121">Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="4bf8f-122">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="4bf8f-123">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4bf8f-124">Выберите nuget.org в качестве источника пакета, а затем выберите вкладку **Обзор**. Найдите **Microsoft.ML**, выберите пакет и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="4bf8f-125">Продолжите установку, соглашаясь с условиями лицензии для выбранного пакета.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="4bf8f-126">Сделайте то же самое для пакета **Microsoft.ML.FastTree** в NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="4bf8f-127">подготавливать данные;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="4bf8f-128">Наборы данных в этом руководстве взяты из статьи From Group to Individual Labels using Deep Features ("Переход от групповых меток к индивидуальным при помощи глубинных признаков"), Котциас (Kotzias) и</span><span class="sxs-lookup"><span data-stu-id="4bf8f-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="4bf8f-129">др.,</span><span class="sxs-lookup"><span data-stu-id="4bf8f-129">al,.</span></span> <span data-ttu-id="4bf8f-130">KDD 2015, и размещены в репозитории машинного обучения UCI Д. Дуа (D. Dua) и Э. Карра Танискиду (E. Karra Taniskidou) (2017).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="4bf8f-131">UCI Machine Learning Repository (Репозиторий машинного обучения UCI) [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="4bf8f-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="4bf8f-132">Ирвайн, Калифорния: Калифорнийский университет, Школа информационных технологий и компьютерных наук.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="4bf8f-133">Скачайте [ZIP-файл набора данных предложений с меткой тональности UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) и извлеките его содержимое.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="4bf8f-134">Скопируйте файл `yelp_labelled.txt` в созданный каталог *Data*.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="4bf8f-135">В обозревателе решений щелкните правой кнопкой мыши файл `yelp_labeled.txt` и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="4bf8f-136">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="4bf8f-137">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="4bf8f-137">Create classes and define paths</span></span>

1. <span data-ttu-id="4bf8f-138">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="4bf8f-139">Создайте два глобальных поля для хранения пути к файлу недавно скачанного набора данных и пути к файлу сохраненной модели:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="4bf8f-140">`_dataPath` содержит путь к набору данных, используемому для обучения модели;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="4bf8f-141">`_modelPath` содержит путь, по которому сохраняется обученная модель.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="4bf8f-142">Добавьте следующий код в строке справа выше метода `Main` для указания пути:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="4bf8f-143">Затем создайте классы для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="4bf8f-144">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="4bf8f-145">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="4bf8f-146">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="4bf8f-147">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="4bf8f-148">Файл *SentimentData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="4bf8f-149">Добавьте следующий оператор `using` в начало файла *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="4bf8f-150">Удалите из файла *SentimentData.cs* существующее определение класса и добавьте следующий код с двумя классами `SentimentData` и `SentimentPrediction`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="4bf8f-151">Как вы подготовили данные</span><span class="sxs-lookup"><span data-stu-id="4bf8f-151">How the data was prepared</span></span>
<span data-ttu-id="4bf8f-152">Класс входного набора данных, `SentimentData`, имеет `string` для комментариев пользователя (`SentimentText`) и `bool` (`Sentiment`) значение 1 (положительная) или 0 (отрицательная) для определения тональности.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="4bf8f-153">Оба поля имеют атрибуты [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29), которые описывают порядок файла данных каждого поля.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="4bf8f-154">Кроме того, свойство `Sentiment` имеет атрибут[ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A), чтобы обозначить его как поле `Label`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="4bf8f-155">В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="4bf8f-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="4bf8f-156">SentimentText</span></span>                         |<span data-ttu-id="4bf8f-157">Тональность (метка)</span><span class="sxs-lookup"><span data-stu-id="4bf8f-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="4bf8f-158">Официантка немного медленная.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="4bf8f-159">0</span><span class="sxs-lookup"><span data-stu-id="4bf8f-159">0</span></span>     |
|<span data-ttu-id="4bf8f-160">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-160">Crust is not good.</span></span>                    |    <span data-ttu-id="4bf8f-161">0</span><span class="sxs-lookup"><span data-stu-id="4bf8f-161">0</span></span>     |
|<span data-ttu-id="4bf8f-162">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="4bf8f-163">1</span><span class="sxs-lookup"><span data-stu-id="4bf8f-163">1</span></span>     |
|<span data-ttu-id="4bf8f-164">Обслуживание очень быстрое.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-164">Service was very prompt.</span></span>              |    <span data-ttu-id="4bf8f-165">1</span><span class="sxs-lookup"><span data-stu-id="4bf8f-165">1</span></span>     |

<span data-ttu-id="4bf8f-166">`SentimentPrediction` — этот класс прогноза используется после обучения модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-166">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="4bf8f-167">Он наследует от `SentimentData` таким образом, чтобы входные данные `SentimentText` могли отображаться вместе с выходными данными прогноза.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-167">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="4bf8f-168">Логическое значение `Prediction` является значением, которое модель прогнозирует при предоставлении новых входных данных `SentimentText`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-168">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="4bf8f-169">Класс выходных данных `SentimentPrediction` содержит два свойства, вычисляемые в модели: `Score` — необработанная оценка, вычисляемая в модели, и `Probability` — оценка, откалиброванная по вероятности того, что текст имеет положительную тональность.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-169">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="4bf8f-170">В этом учебнике самым важным свойством является `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-170">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="4bf8f-171">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-171">Load the data</span></span>
<span data-ttu-id="4bf8f-172">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-172">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="4bf8f-173">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-173">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="4bf8f-174">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-174">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="4bf8f-175">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для всех операций ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-175">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="4bf8f-176">Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-176">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4bf8f-177">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-177">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="4bf8f-178">Необходимо подготовить приложение и затем загружать данные.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="4bf8f-179">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную mlContext:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="4bf8f-180">Добавьте в следующую строку метода `Main()` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="4bf8f-181">Создайте метод `LoadData()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="4bf8f-182">Метод `LoadData()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-182">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="4bf8f-183">загрузка данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-183">Loads the data.</span></span>
    * <span data-ttu-id="4bf8f-184">Разделяет скачанный набор данных на наборы данных для обучения и тестирования.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-184">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="4bf8f-185">Возвращает два набора данных — для обучения и для тестирования.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="4bf8f-186">Добавьте следующий код в первую строку метода `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="4bf8f-187">Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="4bf8f-188">Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="4bf8f-189">Разделение набора данных для обучения и тестирования модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="4bf8f-190">При подготовке модели можно использовать часть набора данных для обучения, а другую часть — для проверки точности модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="4bf8f-191">Чтобы разделить скачанные данные на необходимые наборы данных, добавьте код в следующей строке метода `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="4bf8f-192">Приведенный выше код использует метод [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A), чтобы разделить загруженный набор данных на учебный и проверочный наборы данных, и возвращает их в класс [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="4bf8f-193">Укажите процент тестовых данных с помощью параметра `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="4bf8f-194">Значение по умолчанию — 10 %, но в этом случае лучше использовать 20 % для оценки большего объема данных.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="4bf8f-195">Верните `splitDataView` в конце метода `LoadData()`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="4bf8f-196">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-196">Build and train the model</span></span>

1. <span data-ttu-id="4bf8f-197">В следующей строке кода в методе `Main()` добавьте приведенный ниже вызов метода `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="4bf8f-198">Метод `BuildAndTrainModel()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="4bf8f-199">извлечение и преобразование данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-199">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="4bf8f-200">обучение модели;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-200">Trains the model.</span></span>
    * <span data-ttu-id="4bf8f-201">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-201">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="4bf8f-202">возвращение модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-202">Returns the model.</span></span>

2. <span data-ttu-id="4bf8f-203">Создайте метод `BuildAndTrainModel()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="4bf8f-204">Извлечение и преобразование данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-204">Extract and transform the data</span></span>

1. <span data-ttu-id="4bf8f-205">Добавьте следующую строку кода для вызова `FeaturizeText`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="4bf8f-206">Метод `FeaturizeText()` в приведенном выше коде преобразует текстовый столбец (`SentimentText`) в числовой столбец типа ключа `Features`, который используется алгоритмом машинного обучения: он добавляет его как новый столбец набора данных:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="4bf8f-207">SentimentText</span><span class="sxs-lookup"><span data-stu-id="4bf8f-207">SentimentText</span></span>                         |<span data-ttu-id="4bf8f-208">Тональность</span><span class="sxs-lookup"><span data-stu-id="4bf8f-208">Sentiment</span></span> |<span data-ttu-id="4bf8f-209">Функции</span><span class="sxs-lookup"><span data-stu-id="4bf8f-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="4bf8f-210">Официантка немного медленная.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="4bf8f-211">0</span><span class="sxs-lookup"><span data-stu-id="4bf8f-211">0</span></span>     |<span data-ttu-id="4bf8f-212">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="4bf8f-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="4bf8f-213">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-213">Crust is not good.</span></span>                    |    <span data-ttu-id="4bf8f-214">0</span><span class="sxs-lookup"><span data-stu-id="4bf8f-214">0</span></span>     |<span data-ttu-id="4bf8f-215">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="4bf8f-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="4bf8f-216">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="4bf8f-217">1</span><span class="sxs-lookup"><span data-stu-id="4bf8f-217">1</span></span>     |<span data-ttu-id="4bf8f-218">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="4bf8f-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="4bf8f-219">Обслуживание очень быстрое.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-219">Service was very prompt.</span></span>              |    <span data-ttu-id="4bf8f-220">1</span><span class="sxs-lookup"><span data-stu-id="4bf8f-220">1</span></span>     |<span data-ttu-id="4bf8f-221">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="4bf8f-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="4bf8f-222">Добавление алгоритма обучения</span><span class="sxs-lookup"><span data-stu-id="4bf8f-222">Add a learning algorithm</span></span>

<span data-ttu-id="4bf8f-223">Это приложение использует алгоритм классификации, который классифицирует элементы или строки данных.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="4bf8f-224">Приложение классифицирует комментарии веб-сайта как положительные или отрицательные, поэтому это задача двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="4bf8f-225">Добавьте задачу машинного обучения к определениям преобразований данных, добавив следующее в следующей строке кода в `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="4bf8f-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) — ваш алгоритм обучения классификации.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="4bf8f-227">Он добавляется в `estimator` и принимает `SentimentText` с присвоенными признаками (`Features`) и входные параметры `Label`, чтобы пройти обучение по историческим данным.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="4bf8f-228">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-228">Train the model</span></span>

<span data-ttu-id="4bf8f-229">Обучите модель на основе данных `splitTrainSet` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="4bf8f-230">Метод [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель путем преобразования набора данных и применения обучения.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="4bf8f-231">Возврат обученной модели для оценки</span><span class="sxs-lookup"><span data-stu-id="4bf8f-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="4bf8f-232">Выполните возврат модели в конце метода `BuildAndTrainModel()`.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="4bf8f-233">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-233">Evaluate the model</span></span>

<span data-ttu-id="4bf8f-234">После обучения модели с помощью проверочных данных производится валидация производительности модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-234">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="4bf8f-235">Создайте метод `Evaluate()` сразу после `BuildAndTrainModel()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="4bf8f-236">Метод `Evaluate()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-236">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="4bf8f-237">загрузка тестового набора данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-237">Loads the test dataset.</span></span>
    * <span data-ttu-id="4bf8f-238">создание средства оценки BinaryClassification;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-238">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="4bf8f-239">оценка модели и создание метрик;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-239">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="4bf8f-240">отображение метрик.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-240">Displays the metrics.</span></span>

2. <span data-ttu-id="4bf8f-241">Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `BuildAndTrainModel()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="4bf8f-242">Преобразуйте данные `splitTestSet`, добавив в метод `Evaluate()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="4bf8f-243">Предыдущий код использует метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A), чтобы сделать прогнозы для нескольких входных строк тестового набора данных.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="4bf8f-244">Оцените модель, добавив в метод `Evaluate()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="4bf8f-245">После получения прогноза (`predictions`) метод [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает объект [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) как метрики эффективности модели.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="4bf8f-246">Отображение метрик для проверки модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="4bf8f-247">Воспользуйтесь приведенным ниже кодом, чтобы отобразить метрики.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="4bf8f-248">Метрика `Accuracy` возвращает точность модели — это доля правильных прогнозов в тестовом наборе.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="4bf8f-249">Метрика `AreaUnderRocCurve` показывает уверенность модели в правильности классификации с положительными и отрицательными классами.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="4bf8f-250">Значение `AreaUnderRocCurve` должно быть максимально близким к единице.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="4bf8f-251">Метрика `F1Score` содержит F1-оценку модели, который является мерой баланса между [точностью](../resources/glossary.md#precision) и [полнотой](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="4bf8f-252">Значение `F1Score` должно быть максимально близким к единице.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="4bf8f-253">Прогнозировать результаты для тестовых данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="4bf8f-254">Создайте метод `UseModelWithSingleItem()` сразу после метода `Evaluate()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="4bf8f-255">Метод `UseModelWithSingleItem()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="4bf8f-256">создание отдельного комментария тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-256">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="4bf8f-257">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-257">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="4bf8f-258">объединение тестовых данных и прогнозов для создания отчетов;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-258">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="4bf8f-259">отображение результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="4bf8f-260">Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `Evaluate()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="4bf8f-261">Давайте добавим следующий код в качестве первой строки в методе `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-261">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="4bf8f-262">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий передать один экземпляр данных и осуществить прогнозирование на его основе.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="4bf8f-263">Добавьте комментарий для проверки прогнозирования обученной модели в методе `UseModelWithSingleItem()`, создав экземпляр `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-263">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="4bf8f-264">Передать тестовые комментарии в `Prediction Engine`, добавив следующие строки кода в метод `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-264">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="4bf8f-265">Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одной строке данных.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-265">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="4bf8f-266">Выведите `SentimentText` и соответствующий прогноз тональности, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-266">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="4bf8f-267">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="4bf8f-267">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="4bf8f-268">Развертывание и прогнозирование элементов пакета</span><span class="sxs-lookup"><span data-stu-id="4bf8f-268">Deploy and predict batch items</span></span>

1. <span data-ttu-id="4bf8f-269">Создайте метод `UseModelWithBatchItems()` сразу после метода `UseModelWithSingleItem()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-269">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="4bf8f-270">Метод `UseModelWithBatchItems()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-270">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="4bf8f-271">создание пакетных тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-271">Creates batch test data.</span></span>
    * <span data-ttu-id="4bf8f-272">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-272">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="4bf8f-273">объединение тестовых данных и прогнозов для создания отчетов;</span><span class="sxs-lookup"><span data-stu-id="4bf8f-273">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="4bf8f-274">отображение результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-274">Displays the predicted results.</span></span>

2. <span data-ttu-id="4bf8f-275">Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `UseModelWithSingleItem()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-275">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="4bf8f-276">Добавьте новые комментарии, чтобы проверить прогнозы обученной модели, в метод `UseModelWithBatchItems()`:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-276">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="4bf8f-277">Предсказание тональности на основе комментариев</span><span class="sxs-lookup"><span data-stu-id="4bf8f-277">Predict comment sentiment</span></span>

<span data-ttu-id="4bf8f-278">Использование модели для прогнозирования тональности комментариев с помощью метода [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A):</span><span class="sxs-lookup"><span data-stu-id="4bf8f-278">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="4bf8f-279">Объедините и отобразите прогнозы</span><span class="sxs-lookup"><span data-stu-id="4bf8f-279">Combine and display the predictions</span></span>

<span data-ttu-id="4bf8f-280">Создайте заголовок для результатов с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-280">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="4bf8f-281">Так как `SentimentPrediction` наследуется от `SentimentData`, `Transform()` метод заполняет `SentimentText` прогнозируемыми полями.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-281">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="4bf8f-282">В ходе обработки ML.NET каждый компонент добавляет столбцы, что упрощает отображение результатов:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-282">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="4bf8f-283">Результаты</span><span class="sxs-lookup"><span data-stu-id="4bf8f-283">Results</span></span>

<span data-ttu-id="4bf8f-284">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-284">Your results should be similar to the following.</span></span> <span data-ttu-id="4bf8f-285">Во время обработки отображаются сообщения.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-285">During processing, messages are displayed.</span></span> <span data-ttu-id="4bf8f-286">Вы можете видеть предупреждения или обработанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-286">You may see warnings, or processing messages.</span></span> <span data-ttu-id="4bf8f-287">Для удобства они удалены из следующих результатов.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-287">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="4bf8f-288">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="4bf8f-288">Congratulations!</span></span> <span data-ttu-id="4bf8f-289">Вы успешно создали модель машинного обучения для классификации и прогнозирования тональности сообщений.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-289">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="4bf8f-290">Построение успешных моделей — итеративный процесс.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-290">Building successful models is an iterative process.</span></span> <span data-ttu-id="4bf8f-291">Изначально эта модель имеет низкое качество, так как в руководстве используются небольшие наборы данных для быстрого обучения.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-291">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="4bf8f-292">Если вам требуется модель более высокого качества, можно попытаться улучшить ее, использовав более крупные наборы данных для обучения или выбрав другие алгоритмы обучения с разными [гиперпараметрами](../resources/glossary.md##hyperparameter) для каждого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="4bf8f-292">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="4bf8f-293">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="4bf8f-293">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4bf8f-294">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="4bf8f-294">Next steps</span></span>

<span data-ttu-id="4bf8f-295">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-295">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4bf8f-296">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="4bf8f-296">Create a console application</span></span>
> * <span data-ttu-id="4bf8f-297">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-297">Prepare data</span></span>
> * <span data-ttu-id="4bf8f-298">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="4bf8f-298">Load the data</span></span>
> * <span data-ttu-id="4bf8f-299">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-299">Build and train the model</span></span>
> * <span data-ttu-id="4bf8f-300">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="4bf8f-300">Evaluate the model</span></span>
> * <span data-ttu-id="4bf8f-301">Использование модели для прогноза</span><span class="sxs-lookup"><span data-stu-id="4bf8f-301">Use the model to make a prediction</span></span>
> * <span data-ttu-id="4bf8f-302">Просмотр результатов</span><span class="sxs-lookup"><span data-stu-id="4bf8f-302">See the results</span></span>

<span data-ttu-id="4bf8f-303">Переходите к следующему руководству:</span><span class="sxs-lookup"><span data-stu-id="4bf8f-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4bf8f-304">Классификация задач</span><span class="sxs-lookup"><span data-stu-id="4bf8f-304">Issue Classification</span></span>](github-issue-classification.md)
