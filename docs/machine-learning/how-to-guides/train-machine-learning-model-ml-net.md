---
title: Обучение и оценка модели
description: Из этой статьи вы узнаете, как создавать модели машинного обучения, собирать метрики и измерять производительность с помощью ML.NET. Модель машинного обучения выполняет обнаружение шаблонов в данных обучения для создания прогнозов на основе новых данных.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523859"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="81f28-104">Обучение и оценка модели</span><span class="sxs-lookup"><span data-stu-id="81f28-104">Train and evaluate a model</span></span>

<span data-ttu-id="81f28-105">Из этой статьи вы узнаете, как создавать модели машинного обучения, собирать метрики и измерять производительность с помощью ML.NET.</span><span class="sxs-lookup"><span data-stu-id="81f28-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="81f28-106">Несмотря на то что код в этом примере обучает модель регрессии, те же принципы действуют и в большинстве других алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="81f28-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="81f28-107">Разделение данных на обучающий и проверочный наборы</span><span class="sxs-lookup"><span data-stu-id="81f28-107">Split data for training and testing</span></span>

<span data-ttu-id="81f28-108">Цель модели машинного обучения — обнаружить закономерности в обучающих данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="81f28-109">Эти закономерности используются для создания прогнозов на основе новых данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="81f28-110">Можно моделировать данные с помощью класса, например `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="81f28-110">The data can be modeled by a class like `HousingData`.</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="81f28-111">Используйте следующие данные, которые загружаются в [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="81f28-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

<span data-ttu-id="81f28-112">Разделите данные на обучающий и проверочный наборы с помощью метода [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A).</span><span class="sxs-lookup"><span data-stu-id="81f28-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the data into train and test sets.</span></span> <span data-ttu-id="81f28-113">В результате появится объект [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData), содержащий два члена [`IDataView`](xref:Microsoft.ML.IDataView) — один для обучающего набора данных, другой для проверочного.</span><span class="sxs-lookup"><span data-stu-id="81f28-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="81f28-114">Распределение данных определяется параметром `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="81f28-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="81f28-115">В приведенном ниже фрагменте кода для проверочного набора удерживаются 20 процентов исходных данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="81f28-116">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="81f28-116">Prepare the data</span></span>

<span data-ttu-id="81f28-117">Перед обучением модели машинного обучения данные необходимо подвергнуть предварительной обработке.</span><span class="sxs-lookup"><span data-stu-id="81f28-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="81f28-118">Дополнительные сведения о подготовке данных см. в [инструкции по подготовке данных](prepare-data-ml-net.md), а также в [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="81f28-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="81f28-119">Алгоритмы ML.NET имеют ограничения на типы входных столбцов.</span><span class="sxs-lookup"><span data-stu-id="81f28-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="81f28-120">Кроме того, если значения не указаны, в качестве имен входных и выходных столбцов используются значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81f28-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="81f28-121">Работа с ожидаемыми типами столбцов</span><span class="sxs-lookup"><span data-stu-id="81f28-121">Working with expected column types</span></span>

<span data-ttu-id="81f28-122">Алгоритмы машинного обучения в ML.NET в качестве входных данных ожидают вектор с плавающей запятой известного размера.</span><span class="sxs-lookup"><span data-stu-id="81f28-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="81f28-123">Если все данные уже переведены в числовой формат и предназначены для одновременной обработки (пиксели изображения), примените к модели данных атрибут [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute).</span><span class="sxs-lookup"><span data-stu-id="81f28-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="81f28-124">Если не все данные являются числовыми, а вы хотите к каждому столбцу применить отдельное преобразование данных, используйте метод [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) после обработки каждого столбца — в результате все отдельные столбцы будут объединены в единый вектор компонентов, который будет выходными данными нового столбца.</span><span class="sxs-lookup"><span data-stu-id="81f28-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="81f28-125">В следующем фрагменте кода столбцы `Size` и `HistoricalPrices` объединены в один вектор компонентов, который служит выходными данными для нового столбца с именем `Features`.</span><span class="sxs-lookup"><span data-stu-id="81f28-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="81f28-126">Поскольку нет разницы в масштабах, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) применяется к столбцу `Features` для нормализации данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="81f28-127">Работа с именами столбцов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="81f28-127">Working with default column names</span></span>

<span data-ttu-id="81f28-128">Если имена столбцов не указаны, алгоритмы ML.NET используют имена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81f28-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="81f28-129">Все инструкторы имеют параметр с именем `featureColumnName` для входных данных, алгоритма, а там, где это применимо, еще и параметр с именем `labelColumnName` для ожидаемого значения.</span><span class="sxs-lookup"><span data-stu-id="81f28-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="81f28-130">По умолчанию используются значения `Features` и `Label` соответственно.</span><span class="sxs-lookup"><span data-stu-id="81f28-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="81f28-131">Если во время предварительной обработки используется метод [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A), который создает столбец с именем `Features`, имя столбца компонентов в параметрах алгоритма указывать необязательно, поскольку он уже существует в предварительно обработанных данных `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="81f28-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="81f28-132">Столбец меток — `CurrentPrice`, но в связи с тем, что атрибут [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) используется в модели данных, ML.NET переименовывает столбец `CurrentPrice` в `Label` и таким образом устраняет необходимость предоставлять параметр `labelColumnName` для средства оценки алгоритма машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="81f28-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="81f28-133">Если вы не хотите использовать имена столбцов по умолчанию, передайте имена столбцов компонентов и меток в виде параметров при определении средства оценки алгоритма машинного обучения, как показано в следующем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="81f28-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a><span data-ttu-id="81f28-134">Кэширование данных</span><span class="sxs-lookup"><span data-stu-id="81f28-134">Caching data</span></span>

<span data-ttu-id="81f28-135">По умолчанию при обработке данных их загрузка или потоковая передача осуществляется отложенным образом. Это означает, что во время обучения алгоритмы обучения могут несколько раз загружать данные с диска и выполнять их итерацию.</span><span class="sxs-lookup"><span data-stu-id="81f28-135">By default, when data is processed, it is lazily loaded or streamed which means that trainers may load the data from disk and iterate over it multiple times during training.</span></span> <span data-ttu-id="81f28-136">Поэтому чтобы сократить количество загрузок данных с диска, рекомендуется кэшировать помещаемые в память наборы данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-136">Therefore, caching is recommended for datasets that fit into memory to reduce the number of times data is loaded from disk.</span></span> <span data-ttu-id="81f28-137">Кэширование выполняется как часть [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) с помощью [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A).</span><span class="sxs-lookup"><span data-stu-id="81f28-137">Caching is done as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) by using [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A).</span></span>

<span data-ttu-id="81f28-138">Рекомендуется использовать [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) до алгоритмов обучения в конвейере.</span><span class="sxs-lookup"><span data-stu-id="81f28-138">It's recommended to use [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before any trainers in the pipeline.</span></span>

<span data-ttu-id="81f28-139">Используя следующий класс [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) для добавления метода [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) перед классом [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer), алгоритм обучения кэширует результаты предыдущих средств оценки для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="81f28-139">Using the following [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601), adding [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) trainer caches the results of the previous estimators for later use by the trainer.</span></span>

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="81f28-140">Обучение модели машинного обучения</span><span class="sxs-lookup"><span data-stu-id="81f28-140">Train the machine learning model</span></span>

<span data-ttu-id="81f28-141">Когда данные пройдут предварительную обработку, используйте метод [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) для обучения модели машинного обучения с алгоритмом регрессии [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).</span><span class="sxs-lookup"><span data-stu-id="81f28-141">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="81f28-142">Извлечение параметров модели</span><span class="sxs-lookup"><span data-stu-id="81f28-142">Extract model parameters</span></span>

<span data-ttu-id="81f28-143">После обучения модели извлеките полученные [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) для проверки или повторного обучения.</span><span class="sxs-lookup"><span data-stu-id="81f28-143">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or retraining.</span></span> <span data-ttu-id="81f28-144">[`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) предоставляют смещение и полученные коэффициенты или вес обученной модели.</span><span class="sxs-lookup"><span data-stu-id="81f28-144">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="81f28-145">Другие модели включают параметры, характерные для их задач.</span><span class="sxs-lookup"><span data-stu-id="81f28-145">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="81f28-146">Например, [алгоритм K-средних](xref:Microsoft.ML.Trainers.KMeansTrainer) помещает данные в кластер на основе центроидов, а [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) содержит свойство, в котором хранятся полученные центроиды.</span><span class="sxs-lookup"><span data-stu-id="81f28-146">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="81f28-147">Чтобы узнать больше, изучите [`Microsoft.ML.Trainers`документацию по API](xref:Microsoft.ML.Trainers) и выполните поиск классов, в именах которых есть `ModelParameters`.</span><span class="sxs-lookup"><span data-stu-id="81f28-147">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="81f28-148">Оценка качества модели</span><span class="sxs-lookup"><span data-stu-id="81f28-148">Evaluate model quality</span></span>

<span data-ttu-id="81f28-149">Чтобы выбрать наиболее эффективную модель, необходимо оценить ее производительность на основе проверочных данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-149">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="81f28-150">Для измерения различных метрик обученной модели используйте метод [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A).</span><span class="sxs-lookup"><span data-stu-id="81f28-150">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="81f28-151">Метод `Evaluate` создает различные метрики в зависимости от того, на каком компьютере выполнялась задача машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="81f28-151">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="81f28-152">Чтобы узнать больше, изучите [`Microsoft.ML.Data`документацию по API](xref:Microsoft.ML.Data) и выполните поиск классов, в именах которых есть `Metrics`.</span><span class="sxs-lookup"><span data-stu-id="81f28-152">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="81f28-153">В приведенном выше фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="81f28-153">In the previous code sample:</span></span>

1. <span data-ttu-id="81f28-154">Проверочный набор данных подвергается предварительной обработке с использованием предварительно заданных преобразований для подготовки данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-154">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="81f28-155">В обученной модели машинного обучения формируются прогнозы на основе проверочных данных.</span><span class="sxs-lookup"><span data-stu-id="81f28-155">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="81f28-156">В методе `Evaluate` значения в столбцу `CurrentPrice` проверочного набора данных сравниваются со столбцом `Score`, куда сохраняются новые полученные прогнозы, и рассчитываются метрики модели регрессии, одна из которых, R-квадрат, хранится в переменной `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="81f28-156">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="81f28-157">В этом небольшом примере из-за ограниченного объема данных значение R-квадрат не попадает в диапазон от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="81f28-157">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="81f28-158">В реальной ситуации его значение должно быть в диапазоне от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="81f28-158">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
