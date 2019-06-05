---
title: Учебник. Прогнозирование цен с помощью регрессии
description: В этом учебнике описано, как с помощью ML.NET создать модель регрессии для прогнозирования цен, в частности платы за проезд в такси по Нью-Йорку.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377792"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="b6790-103">Учебник. Прогнозирование цен с помощью регрессии с ML.NET</span><span class="sxs-lookup"><span data-stu-id="b6790-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="b6790-104">В этом учебнике показано, как создать [модель регрессии](../resources/glossary.md#regression) с помощью ML.NET, чтобы прогнозировать цены, в частности плату за проезд в такси по Нью-Йорку.</span><span class="sxs-lookup"><span data-stu-id="b6790-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="b6790-105">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="b6790-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b6790-106">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="b6790-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="b6790-107">Загрузка и преобразование данных</span><span class="sxs-lookup"><span data-stu-id="b6790-107">Load and transform the data</span></span>
> * <span data-ttu-id="b6790-108">Выбор алгоритма обучения</span><span class="sxs-lookup"><span data-stu-id="b6790-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b6790-109">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="b6790-109">Train the model</span></span>
> * <span data-ttu-id="b6790-110">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="b6790-110">Evaluate the model</span></span>
> * <span data-ttu-id="b6790-111">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="b6790-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6790-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b6790-112">Prerequisites</span></span>

* <span data-ttu-id="b6790-113">[Visual Studio 2017 15.6 или более поздней версии](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="b6790-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b6790-114">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="b6790-114">Create a console application</span></span>

1. <span data-ttu-id="b6790-115">Создайте **консольное приложение .NET Core** с именем TaxiFarePrediction.</span><span class="sxs-lookup"><span data-stu-id="b6790-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="b6790-116">Создайте каталог с именем *Data* в проекте для хранения набора данных и файлов модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="b6790-117">Установите пакет NuGet для **Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b6790-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="b6790-118">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b6790-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b6790-119">Выберите в качестве источника пакета "nuget.org", откройте вкладку **Обзор**, найдите **Microsoft.ML**, выберите пакет в списке и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="b6790-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b6790-120">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="b6790-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="b6790-121">Сделайте то же самое для пакета NuGet **Microsoft.ML.FastTree**.</span><span class="sxs-lookup"><span data-stu-id="b6790-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b6790-122">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="b6790-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="b6790-123">Скачайте наборы данных [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) и [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv), сохранив их в созданной на предыдущем шаге папке *Data*.</span><span class="sxs-lookup"><span data-stu-id="b6790-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="b6790-124">Эти наборы данных используются для обучения модели машинного обучения и последующей оценки точности этой модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="b6790-125">Эти наборы данных взяты из [наборов данных NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="b6790-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="b6790-126">В **обозревателе решений** щелкните правой кнопкой мыши каждый из файлов \*.csv и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="b6790-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="b6790-127">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="b6790-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="b6790-128">Откройте набор данных **taxi-fare-train.csv** и просмотрите заголовки столбцов в первой строке.</span><span class="sxs-lookup"><span data-stu-id="b6790-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="b6790-129">Теперь изучите каждый из столбцов.</span><span class="sxs-lookup"><span data-stu-id="b6790-129">Take a look at each of the columns.</span></span> <span data-ttu-id="b6790-130">Разберитесь, какие данные в них хранятся, и определите, какие столбцы являются **признаками**, а в каком содержится **метка**.</span><span class="sxs-lookup"><span data-stu-id="b6790-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="b6790-131">`label` — это столбец, который необходимо спрогнозировать.</span><span class="sxs-lookup"><span data-stu-id="b6790-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="b6790-132">Определены `Features`входные данные, которые вы предоставляете модели для прогнозирования `Label`.</span><span class="sxs-lookup"><span data-stu-id="b6790-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="b6790-133">Предоставленный набор данных содержит следующие столбцы:</span><span class="sxs-lookup"><span data-stu-id="b6790-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="b6790-134">**vendor_id:** идентификатор поставщика услуг такси — это признак.</span><span class="sxs-lookup"><span data-stu-id="b6790-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="b6790-135">**rate_code:** тип тарифа для поездки на такси — это признак.</span><span class="sxs-lookup"><span data-stu-id="b6790-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="b6790-136">**passenger_count:** число пассажиров в поездке — это признак.</span><span class="sxs-lookup"><span data-stu-id="b6790-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="b6790-137">**trip_time_in_secs:** время, затраченное на поездку.</span><span class="sxs-lookup"><span data-stu-id="b6790-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="b6790-138">Вам требуется спрогнозировать плату за одну поездку до того, как поездка будет завершена.</span><span class="sxs-lookup"><span data-stu-id="b6790-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="b6790-139">На этот момент вам неизвестна продолжительность поездки.</span><span class="sxs-lookup"><span data-stu-id="b6790-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="b6790-140">Таким образом, продолжительность поездки не является признаком и соответствующий столбец следует исключить из модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="b6790-141">**trip_distance:** расстояние поездки — это признак.</span><span class="sxs-lookup"><span data-stu-id="b6790-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="b6790-142">**payment_type:** метод оплаты (наличные или кредитная карта) — это признак.</span><span class="sxs-lookup"><span data-stu-id="b6790-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="b6790-143">**fare_amount:** общая сумма, уплаченная за поездку на такси, — это метка.</span><span class="sxs-lookup"><span data-stu-id="b6790-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="b6790-144">Создание классов данных</span><span class="sxs-lookup"><span data-stu-id="b6790-144">Create data classes</span></span>

<span data-ttu-id="b6790-145">Создайте классы для входных данных и прогнозов:</span><span class="sxs-lookup"><span data-stu-id="b6790-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b6790-146">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="b6790-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b6790-147">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="b6790-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="b6790-148">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="b6790-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b6790-149">Добавьте следующие директивы `using` в новый файл.</span><span class="sxs-lookup"><span data-stu-id="b6790-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="b6790-150">Удалите из файла *TaxiTrip.cs* существующее определение класса и добавьте следующий код с двумя классами `TaxiTrip` и `TaxiTripFarePrediction`:</span><span class="sxs-lookup"><span data-stu-id="b6790-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="b6790-151">Класс `TaxiTrip` содержит входные данные и определения для каждого из столбцов в этом наборе данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="b6790-152">Используйте атрибут <xref:Microsoft.ML.Data.LoadColumnAttribute>, чтобы указать индексы исходных столбцов в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="b6790-153">Класс `TaxiTripFarePrediction` представляет результаты прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="b6790-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="b6790-154">Он содержит одно поле типа float `FareAmount`, к которому применен атрибут `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b6790-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="b6790-155">В случае задачи регрессии столбец **Оценка** содержит прогнозируемые значения метки.</span><span class="sxs-lookup"><span data-stu-id="b6790-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="b6790-156">Используйте тип `float` для представления значений с плавающей запятой в классах данных ввода и прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="b6790-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="b6790-157">Определение путей к данным и модели</span><span class="sxs-lookup"><span data-stu-id="b6790-157">Define data and model paths</span></span>

<span data-ttu-id="b6790-158">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b6790-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="b6790-159">Необходимо создать три поля, которые будут содержать пути к файлам с наборами данных и к файлу для сохранения модели:</span><span class="sxs-lookup"><span data-stu-id="b6790-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="b6790-160">`_trainDataPath` содержит путь к файлу с набором данных, используемым для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="b6790-161">`_testDataPath` содержит путь к файлу с набором данных, используемым для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="b6790-162">`_modelPath` содержит путь к файлу для сохранения обучаемой модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="b6790-163">Добавьте следующий код прямо перед методом `Main`, чтобы указать эти пути и переменную `_textLoader`:</span><span class="sxs-lookup"><span data-stu-id="b6790-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="b6790-164">Все операции ML.NET запускаются в [классе MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="b6790-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="b6790-165">Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="b6790-166">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b6790-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="b6790-167">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="b6790-167">Initialize variables in Main</span></span>

<span data-ttu-id="b6790-168">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="b6790-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="b6790-169">В качестве следующей строки кода в методе `Main` добавьте приведенный ниже код, чтобы вызвать метод `Train`:</span><span class="sxs-lookup"><span data-stu-id="b6790-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="b6790-170">Метод `Train()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="b6790-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="b6790-171">загрузка данных;</span><span class="sxs-lookup"><span data-stu-id="b6790-171">Loads the data.</span></span>
* <span data-ttu-id="b6790-172">извлечение и преобразование данных;</span><span class="sxs-lookup"><span data-stu-id="b6790-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="b6790-173">обучение модели;</span><span class="sxs-lookup"><span data-stu-id="b6790-173">Trains the model.</span></span>
* <span data-ttu-id="b6790-174">возвращение модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-174">Returns the model.</span></span>

<span data-ttu-id="b6790-175">Метод `Train` обучает модель.</span><span class="sxs-lookup"><span data-stu-id="b6790-175">The `Train` method trains the model.</span></span> <span data-ttu-id="b6790-176">Создайте этот метод сразу под `Main`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="b6790-177">Загрузка и преобразование данных</span><span class="sxs-lookup"><span data-stu-id="b6790-177">Load and transform data</span></span>

<span data-ttu-id="b6790-178">ML.NET использует [класс IDataView](xref:Microsoft.ML.IDataView) как гибкий и эффективный способ описания числовых или текстовых табличных данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="b6790-179">`IDataView` может загружать данные из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="b6790-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="b6790-180">Добавьте следующий код в первую строку метода `Train()`:</span><span class="sxs-lookup"><span data-stu-id="b6790-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="b6790-181">Так как вам нужно спрогнозировать плату за такси, столбец `FareAmount` является меткой `Label`, которую вы будете прогнозировать (выходные данные модели). Используйте класс преобразования `CopyColumnsEstimator`, чтобы скопировать `FareAmount`, и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="b6790-182">Алгоритм, который обучает модель, принимает **числовые** признаки, поэтому значения категориальных данных (`VendorId`, `RateCode` и `PaymentType`) нужно преобразовать в числа (`VendorIdEncoded`, `RateCodeEncoded` и `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="b6790-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="b6790-183">Для этого используйте класс преобразования [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer), который присваивает разные числовые значения ключа разным значениям в каждом из столбцов, и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="b6790-184">Последний шаг на этапе подготовки данных заключается в объединении всех столбцов признаков в столбце **Features** с помощью класса преобразования `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="b6790-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="b6790-185">По умолчанию алгоритм обучения обрабатывает только признаки, представленные в столбце **Features**.</span><span class="sxs-lookup"><span data-stu-id="b6790-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="b6790-186">Добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b6790-187">Выбор алгоритма обучения</span><span class="sxs-lookup"><span data-stu-id="b6790-187">Choose a learning algorithm</span></span>

<span data-ttu-id="b6790-188">Задача заключается в прогнозировании стоимости поездки в такси в Нью-Йорке.</span><span class="sxs-lookup"><span data-stu-id="b6790-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="b6790-189">На первый взгляд может показаться, что плата зависит только от расстояния.</span><span class="sxs-lookup"><span data-stu-id="b6790-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="b6790-190">Но службы такси в Нью-Йорке изменяют плату с учетом еще нескольких факторов, таких как наличие дополнительных пассажиров или оплата кредитной картой вместо наличных.</span><span class="sxs-lookup"><span data-stu-id="b6790-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="b6790-191">Вы хотите спрогнозировать стоимость, которая является реальным значением, зависящим от других факторов в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="b6790-192">Для этого нужно выбрать задачу машинного обучения [регрессия](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="b6790-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="b6790-193">Добавьте задачу машинного обучения [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) к определениям преобразований данных, добавив в `Train()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="b6790-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="b6790-194">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="b6790-194">Train the model</span></span>

<span data-ttu-id="b6790-195">Согласуйте модель с учебным `dataview` и получите обученную модель, добавив в метод `Train()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="b6790-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="b6790-196">Метод [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель путем преобразования набора данных и применения обучения.</span><span class="sxs-lookup"><span data-stu-id="b6790-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="b6790-197">Возвратите обученную модель с помощью следующей строки кода в методе `Train()`:</span><span class="sxs-lookup"><span data-stu-id="b6790-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="b6790-198">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="b6790-198">Evaluate the model</span></span>

<span data-ttu-id="b6790-199">Затем оцените эффективность модели с помощью тестовых данных для контроля качества и проверки.</span><span class="sxs-lookup"><span data-stu-id="b6790-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="b6790-200">Создайте метод `Evaluate()` сразу после `Train()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="b6790-201">Метод `Evaluate` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="b6790-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="b6790-202">загрузка тестового набора данных;</span><span class="sxs-lookup"><span data-stu-id="b6790-202">Loads the test dataset.</span></span>
* <span data-ttu-id="b6790-203">создание средства оценки регрессии;</span><span class="sxs-lookup"><span data-stu-id="b6790-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="b6790-204">оценка модели и создание метрик;</span><span class="sxs-lookup"><span data-stu-id="b6790-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="b6790-205">отображение метрик.</span><span class="sxs-lookup"><span data-stu-id="b6790-205">Displays the metrics.</span></span>

<span data-ttu-id="b6790-206">Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `Train`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="b6790-207">Загрузите тестовый набор данных с помощью метода [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A).</span><span class="sxs-lookup"><span data-stu-id="b6790-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="b6790-208">Оцените модель с помощью этого набора данных для проверки ее качества, добавив следующий код в метод `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="b6790-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="b6790-209">Затем преобразуйте данные `Test`, добавив следующий код для `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="b6790-209">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="b6790-210">Метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) осуществляет прогнозирование для входных строк тестового набора данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="b6790-211">Метод `RegressionContext.Evaluate` вычисляет метрики качества для `PredictionModel` на основе указанного набора данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="b6790-212">Возвращает объект <xref:Microsoft.ML.Data.RegressionMetrics>, который содержит общие метрики, вычисляемые с помощью средств оценки регрессии.</span><span class="sxs-lookup"><span data-stu-id="b6790-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="b6790-213">Чтобы отобразить их для оценки качества модели, сначала метрики необходимо получить.</span><span class="sxs-lookup"><span data-stu-id="b6790-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="b6790-214">Добавьте в следующую строку метода `Evaluate` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="b6790-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="b6790-215">После получения прогноза метод [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает метрики эффективности модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="b6790-216">Добавьте следующий код, чтобы оценить модель и создать для нее метрики оценки:</span><span class="sxs-lookup"><span data-stu-id="b6790-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="b6790-217">Также в качестве метрики для оценки регрессионных моделей используется [коэффициент детерминации](../resources/glossary.md#coefficient-of-determination).</span><span class="sxs-lookup"><span data-stu-id="b6790-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="b6790-218">Коэффициент детерминации может иметь значения в диапазоне от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="b6790-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="b6790-219">Чем ближе его значение к 1, тем лучше модель.</span><span class="sxs-lookup"><span data-stu-id="b6790-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="b6790-220">Чтобы отображать значение коэффициента детерминации, добавьте следующий код в метод `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="b6790-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="b6790-221">[Среднеквадратичное отклонение](../resources/glossary.md##root-of-mean-squared-error-rmse) является одной из метрик, используемых для оценки регрессионной модели.</span><span class="sxs-lookup"><span data-stu-id="b6790-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="b6790-222">Чем ниже это отклонение, тем лучше модель.</span><span class="sxs-lookup"><span data-stu-id="b6790-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="b6790-223">Чтобы отображать значение среднеквадратичного отклонения, добавьте следующий код в метод `Evaluate`:</span><span class="sxs-lookup"><span data-stu-id="b6790-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b6790-224">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="b6790-224">Use the model for predictions</span></span>

<span data-ttu-id="b6790-225">Создайте метод `TestSinglePrediction` сразу после метода `Evaluate`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="b6790-226">Метод `TestSinglePrediction` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="b6790-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="b6790-227">создание отдельного комментария тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="b6790-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="b6790-228">прогнозирование суммы оплаты на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="b6790-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="b6790-229">объединение тестовых данных и прогнозов для создания отчетов;</span><span class="sxs-lookup"><span data-stu-id="b6790-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="b6790-230">отображение результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="b6790-230">Displays the predicted results.</span></span>

<span data-ttu-id="b6790-231">Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `Evaluate`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="b6790-232">Для прогнозирования цены используйте `PredictionEngine`, добавив в `TestSinglePrediction()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="b6790-233">[Класс PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий передать один экземпляр данных и осуществить прогнозирование на его основе.</span><span class="sxs-lookup"><span data-stu-id="b6790-233">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="b6790-234">Для этого руководства в этом классе используется один тестовый проход.</span><span class="sxs-lookup"><span data-stu-id="b6790-234">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="b6790-235">Позже можно добавить другие сценарии и поэкспериментировать с этой моделью.</span><span class="sxs-lookup"><span data-stu-id="b6790-235">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="b6790-236">Добавьте поездку для проверки прогнозирования стоимости обученной моделью с помощью метода `TestSinglePrediction()`, создав экземпляр `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="b6790-236">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="b6790-237">Затем спрогнозируйте стоимость на основе отдельного экземпляра данных о поездке на такси и передайте ее в `PredictionEngine`, добавив следующие строки кода в метод `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="b6790-237">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="b6790-238">Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одному экземпляру данных.</span><span class="sxs-lookup"><span data-stu-id="b6790-238">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="b6790-239">Чтобы отобразить прогнозируемую плату за указанную поездку, добавьте в метод `TestSinglePrediction` следующий код:</span><span class="sxs-lookup"><span data-stu-id="b6790-239">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="b6790-240">Запустите программу, чтобы узнать прогноз платы за такси для тестового примера.</span><span class="sxs-lookup"><span data-stu-id="b6790-240">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="b6790-241">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="b6790-241">Congratulations!</span></span> <span data-ttu-id="b6790-242">Вы успешно создали модель машинного обучения для прогнозирования платы за проезд в такси, оценили ее точность и использовали ее для получения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="b6790-242">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="b6790-243">Исходный код для этого руководства можно найти в репозитории GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="b6790-243">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6790-244">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="b6790-244">Next steps</span></span>

<span data-ttu-id="b6790-245">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="b6790-245">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b6790-246">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="b6790-246">Prepare and understand the data</span></span>
> * <span data-ttu-id="b6790-247">Создание конвейера обучения</span><span class="sxs-lookup"><span data-stu-id="b6790-247">Create a learning pipeline</span></span>
> * <span data-ttu-id="b6790-248">Загрузка и преобразование данных</span><span class="sxs-lookup"><span data-stu-id="b6790-248">Load and transform the data</span></span>
> * <span data-ttu-id="b6790-249">Выбор алгоритма обучения</span><span class="sxs-lookup"><span data-stu-id="b6790-249">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b6790-250">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="b6790-250">Train the model</span></span>
> * <span data-ttu-id="b6790-251">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="b6790-251">Evaluate the model</span></span>
> * <span data-ttu-id="b6790-252">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="b6790-252">Use the model for predictions</span></span>

<span data-ttu-id="b6790-253">Переходите к следующему руководству.</span><span class="sxs-lookup"><span data-stu-id="b6790-253">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6790-254">Кластеризация ирисов Фишера</span><span class="sxs-lookup"><span data-stu-id="b6790-254">Iris clustering</span></span>](iris-clustering.md)
