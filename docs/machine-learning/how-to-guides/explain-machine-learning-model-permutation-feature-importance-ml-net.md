---
title: Объяснение прогнозов модели с помощью функции PFI
description: Сведения об определении важности признаков моделей с помощью средства Permutation Feature Importance в ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 2f444508990a902a1c61b72b1be2263d8d93ba70
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065647"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="b7acc-103">Объяснение прогнозов модели с помощью функции PFI</span><span class="sxs-lookup"><span data-stu-id="b7acc-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="b7acc-104">Узнайте, как объяснять прогнозы модели машинного обучения ML.NET, учитывая влияние различных компонентов на прогнозы с помощью функции PFI (Permutation Feature Importance — важность компонентов перестановки).</span><span class="sxs-lookup"><span data-stu-id="b7acc-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="b7acc-105">Модели машинного обучения часто представляются черными ящиками, которые принимают входные данные и создают выходные данные.</span><span class="sxs-lookup"><span data-stu-id="b7acc-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="b7acc-106">Промежуточные этапы или взаимодействие между компонентами, которые влияют на выходные данные, распознаются редко.</span><span class="sxs-lookup"><span data-stu-id="b7acc-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="b7acc-107">Машинное обучение проникает во все аспекты нашей повседневной жизни, такие как здравоохранение, а значит, очень важно понимать, почему модель машинного обучения принимает именно те решения, которые она принимает.</span><span class="sxs-lookup"><span data-stu-id="b7acc-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="b7acc-108">Например, если диагностика осуществляется на основе модели машинного обучения, у медицинских работников должен быть способ изучить факторы, которые на нее повлияли.</span><span class="sxs-lookup"><span data-stu-id="b7acc-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="b7acc-109">Правильная диагностика намного повышает шансы пациента на быстрое выздоровление.</span><span class="sxs-lookup"><span data-stu-id="b7acc-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="b7acc-110">Таким образом, чем объяснение модели лучше, тем увереннее медицинские работники будут принимать или отклонять принятые моделью решения.</span><span class="sxs-lookup"><span data-stu-id="b7acc-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="b7acc-111">Для объяснения моделей применяются различные приемы, одной из которых является PFI.</span><span class="sxs-lookup"><span data-stu-id="b7acc-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="b7acc-112">PFI — это прием, которые используется для объяснения моделей классификации и регрессии и основан на работе [Бреймана *Random Forests* (Случайные леса)](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(см. раздел 10).</span><span class="sxs-lookup"><span data-stu-id="b7acc-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="b7acc-113">В общем смысле он случайным образом тасует весь набор данных по одному компоненту за раз и рассчитывает, на сколько снижается метрика эффективности, отражающая интерес.</span><span class="sxs-lookup"><span data-stu-id="b7acc-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="b7acc-114">Чем больше изменение, тем важнее компонент.</span><span class="sxs-lookup"><span data-stu-id="b7acc-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="b7acc-115">Выделив самые важные компоненты, сборщики модели могут сосредоточиться на работе с подмножеством более значимых компонентов и таким образом уменьшить шум и время обучения.</span><span class="sxs-lookup"><span data-stu-id="b7acc-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b7acc-116">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="b7acc-116">Load the data</span></span>

<span data-ttu-id="b7acc-117">Компоненты набора данных, которые используются в этом примере, перечислены в столбцах 1–12.</span><span class="sxs-lookup"><span data-stu-id="b7acc-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="b7acc-118">Цель — спрогнозировать `Price`.</span><span class="sxs-lookup"><span data-stu-id="b7acc-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="b7acc-119">Столбец</span><span class="sxs-lookup"><span data-stu-id="b7acc-119">Column</span></span> | <span data-ttu-id="b7acc-120">Функция</span><span class="sxs-lookup"><span data-stu-id="b7acc-120">Feature</span></span> | <span data-ttu-id="b7acc-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b7acc-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="b7acc-122">1</span><span class="sxs-lookup"><span data-stu-id="b7acc-122">1</span></span> | <span data-ttu-id="b7acc-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="b7acc-123">CrimeRate</span></span> | <span data-ttu-id="b7acc-124">Уровень преступности на душу населения</span><span class="sxs-lookup"><span data-stu-id="b7acc-124">Per capita crime rate</span></span>
| <span data-ttu-id="b7acc-125">2</span><span class="sxs-lookup"><span data-stu-id="b7acc-125">2</span></span> | <span data-ttu-id="b7acc-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="b7acc-126">ResidentialZones</span></span> | <span data-ttu-id="b7acc-127">Жилые районы в городе</span><span class="sxs-lookup"><span data-stu-id="b7acc-127">Residential zones in town</span></span>
| <span data-ttu-id="b7acc-128">3</span><span class="sxs-lookup"><span data-stu-id="b7acc-128">3</span></span> | <span data-ttu-id="b7acc-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="b7acc-129">CommercialZones</span></span> | <span data-ttu-id="b7acc-130">Нежилые районы в городе</span><span class="sxs-lookup"><span data-stu-id="b7acc-130">Non-residential zones in town</span></span>
| <span data-ttu-id="b7acc-131">4</span><span class="sxs-lookup"><span data-stu-id="b7acc-131">4</span></span> | <span data-ttu-id="b7acc-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="b7acc-132">NearWater</span></span> | <span data-ttu-id="b7acc-133">Близость к водоему</span><span class="sxs-lookup"><span data-stu-id="b7acc-133">Proximity to body of water</span></span>
| <span data-ttu-id="b7acc-134">5</span><span class="sxs-lookup"><span data-stu-id="b7acc-134">5</span></span> | <span data-ttu-id="b7acc-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="b7acc-135">ToxicWasteLevels</span></span> | <span data-ttu-id="b7acc-136">Уровень токсичности (PPM)</span><span class="sxs-lookup"><span data-stu-id="b7acc-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="b7acc-137">6</span><span class="sxs-lookup"><span data-stu-id="b7acc-137">6</span></span> | <span data-ttu-id="b7acc-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="b7acc-138">AverageRoomNumber</span></span> | <span data-ttu-id="b7acc-139">Среднее количество комнат в доме</span><span class="sxs-lookup"><span data-stu-id="b7acc-139">Average number of rooms in house</span></span>
| <span data-ttu-id="b7acc-140">7</span><span class="sxs-lookup"><span data-stu-id="b7acc-140">7</span></span> | <span data-ttu-id="b7acc-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="b7acc-141">HomeAge</span></span> | <span data-ttu-id="b7acc-142">Возраст дома</span><span class="sxs-lookup"><span data-stu-id="b7acc-142">Age of home</span></span>
| <span data-ttu-id="b7acc-143">8</span><span class="sxs-lookup"><span data-stu-id="b7acc-143">8</span></span> | <span data-ttu-id="b7acc-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="b7acc-144">BusinessCenterDistance</span></span> | <span data-ttu-id="b7acc-145">Расстояние до ближайшего делового района</span><span class="sxs-lookup"><span data-stu-id="b7acc-145">Distance to nearest business district</span></span>
| <span data-ttu-id="b7acc-146">9</span><span class="sxs-lookup"><span data-stu-id="b7acc-146">9</span></span> | <span data-ttu-id="b7acc-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="b7acc-147">HighwayAccess</span></span> | <span data-ttu-id="b7acc-148">Близость к автомагистралям</span><span class="sxs-lookup"><span data-stu-id="b7acc-148">Proximity to highways</span></span>
| <span data-ttu-id="b7acc-149">10</span><span class="sxs-lookup"><span data-stu-id="b7acc-149">10</span></span> | <span data-ttu-id="b7acc-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="b7acc-150">TaxRate</span></span> | <span data-ttu-id="b7acc-151">Ставка налога на имущество</span><span class="sxs-lookup"><span data-stu-id="b7acc-151">Property tax rate</span></span>
| <span data-ttu-id="b7acc-152">11</span><span class="sxs-lookup"><span data-stu-id="b7acc-152">11</span></span> | <span data-ttu-id="b7acc-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="b7acc-153">StudentTeacherRatio</span></span> | <span data-ttu-id="b7acc-154">Соотношение учащихся и учителей</span><span class="sxs-lookup"><span data-stu-id="b7acc-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="b7acc-155">12</span><span class="sxs-lookup"><span data-stu-id="b7acc-155">12</span></span> | <span data-ttu-id="b7acc-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="b7acc-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="b7acc-157">Процент населения, живущего за чертой бедности</span><span class="sxs-lookup"><span data-stu-id="b7acc-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="b7acc-158">13</span><span class="sxs-lookup"><span data-stu-id="b7acc-158">13</span></span> | <span data-ttu-id="b7acc-159">Price</span><span class="sxs-lookup"><span data-stu-id="b7acc-159">Price</span></span> | <span data-ttu-id="b7acc-160">Цена на дом</span><span class="sxs-lookup"><span data-stu-id="b7acc-160">Price of the home</span></span>

<span data-ttu-id="b7acc-161">Пример набора данных:</span><span class="sxs-lookup"><span data-stu-id="b7acc-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="b7acc-162">Данные в этом примере можно моделировать с помощью класса, например, `HousingPriceData`:</span><span class="sxs-lookup"><span data-stu-id="b7acc-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

<span data-ttu-id="b7acc-163">Загрузите данные в [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="b7acc-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b7acc-164">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="b7acc-164">Train the model</span></span>

<span data-ttu-id="b7acc-165">Код в приведенном ниже примере иллюстрирует процесс обучения модели линейной регрессии для прогнозирования цен на дома.</span><span class="sxs-lookup"><span data-stu-id="b7acc-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames = 
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="b7acc-166">Объяснение модели с помощью функции PFI</span><span class="sxs-lookup"><span data-stu-id="b7acc-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="b7acc-167">В ML.NET используйте метод [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) для решения соответствующей задачи.</span><span class="sxs-lookup"><span data-stu-id="b7acc-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="b7acc-168">В результате применения метода [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) в проверочном наборе данных создается [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) из объектов [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics).</span><span class="sxs-lookup"><span data-stu-id="b7acc-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="b7acc-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) предоставляет сводные статистические данные, такие как среднее и стандартное отклонение, для нескольких значений параметра [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics), количество которых равно числу перестановок, которое определяет параметр `permutationCount`.</span><span class="sxs-lookup"><span data-stu-id="b7acc-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="b7acc-170">Важность, или в данном случае среднее абсолютное снижение метрики R-квадрат, рассчитанное методом [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions), можно отсортировать по убыванию.</span><span class="sxs-lookup"><span data-stu-id="b7acc-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

<span data-ttu-id="b7acc-171">При печати значений для каждого параметра в `featureImportanceMetrics` выдается результат представленного ниже вида.</span><span class="sxs-lookup"><span data-stu-id="b7acc-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="b7acc-172">У вас результаты будут другими, поскольку эти значения зависят от предоставленных данных.</span><span class="sxs-lookup"><span data-stu-id="b7acc-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="b7acc-173">Функция</span><span class="sxs-lookup"><span data-stu-id="b7acc-173">Feature</span></span> | <span data-ttu-id="b7acc-174">Изменение в R-квадрат</span><span class="sxs-lookup"><span data-stu-id="b7acc-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="b7acc-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="b7acc-175">HighwayAccess</span></span>       |   <span data-ttu-id="b7acc-176">–0,042731</span><span class="sxs-lookup"><span data-stu-id="b7acc-176">-0.042731</span></span>
<span data-ttu-id="b7acc-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="b7acc-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="b7acc-178">–0,012730</span><span class="sxs-lookup"><span data-stu-id="b7acc-178">-0.012730</span></span>
<span data-ttu-id="b7acc-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="b7acc-179">BusinessCenterDistance</span></span>| <span data-ttu-id="b7acc-180">–0,010491</span><span class="sxs-lookup"><span data-stu-id="b7acc-180">-0.010491</span></span>
<span data-ttu-id="b7acc-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="b7acc-181">TaxRate</span></span>             |   <span data-ttu-id="b7acc-182">–0,008545</span><span class="sxs-lookup"><span data-stu-id="b7acc-182">-0.008545</span></span>
<span data-ttu-id="b7acc-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="b7acc-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="b7acc-184">–0,003949</span><span class="sxs-lookup"><span data-stu-id="b7acc-184">-0.003949</span></span>
<span data-ttu-id="b7acc-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="b7acc-185">CrimeRate</span></span>           |   <span data-ttu-id="b7acc-186">–0,003665</span><span class="sxs-lookup"><span data-stu-id="b7acc-186">-0.003665</span></span>
<span data-ttu-id="b7acc-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="b7acc-187">CommercialZones</span></span>     |   <span data-ttu-id="b7acc-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="b7acc-188">0.002749</span></span>
<span data-ttu-id="b7acc-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="b7acc-189">HomeAge</span></span>             |   <span data-ttu-id="b7acc-190">–0,002426</span><span class="sxs-lookup"><span data-stu-id="b7acc-190">-0.002426</span></span>
<span data-ttu-id="b7acc-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="b7acc-191">ResidentialZones</span></span>    |   <span data-ttu-id="b7acc-192">–0,002319</span><span class="sxs-lookup"><span data-stu-id="b7acc-192">-0.002319</span></span>
<span data-ttu-id="b7acc-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="b7acc-193">NearWater</span></span>           |   <span data-ttu-id="b7acc-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="b7acc-194">0.000203</span></span>
<span data-ttu-id="b7acc-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="b7acc-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="b7acc-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="b7acc-196">0.000031</span></span>
<span data-ttu-id="b7acc-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="b7acc-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="b7acc-198">–0,000019</span><span class="sxs-lookup"><span data-stu-id="b7acc-198">-0.000019</span></span>

<span data-ttu-id="b7acc-199">Рассмотрим пять самых важных компонентов для этого набора данных. Цена на дом, спрогнозированная этой моделью, зависит от его близости к автомагистралям, соотношения учащихся и учителей в окрестных школах, близости к основным центрам трудоустройства, ставки налога на имущество и среднего количества комнат.</span><span class="sxs-lookup"><span data-stu-id="b7acc-199">Taking a look at the the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
