---
title: Повторное обучение модели
description: Узнайте, как переобучать модель в ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 552698c02a7846db588822fa68d094dece160ea0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063571"
---
# <a name="re-train-a-model"></a>Повторное обучение модели

Узнайте, как переобучать модель машинного обучения в ML.NET.

Мир и данные вокруг него меняются с постоянной скоростью. Это значит, что вместе с ними должны меняться и обновляться модели машинного обучения. ML.NET предоставляет функциональные возможности для переобучения моделей с использованием параметров обученной модели, которые служат отправной точкой для постоянного развития и позволяют не начинать каждый раз заново.  

В ML.NET можно переобучать следующие алгоритмы:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer);
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer);
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer);
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Загрузка предварительно обученной модели

Для начала загрузите обученную ранее модель в свое приложение. Дополнительные сведения о загрузке конвейеров и моделей обучения см. в соответствующей [инструкции](./consuming-model-ml-net.md).

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data prepration pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Извлечение параметров обученной ранее модели

Загрузив модель, извлеките параметры модели через свойство [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) обученной ранее модели. Обученная ранее модель была обучена с использованием модели линейной регрессии [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer), которая создает [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1), а тот, в свою очередь, выводит [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Эти параметры модели линейной регрессии содержат смещение и вес или коэффициенты обученной модели. Данные значения станут отправной точкой для переобученной модели.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Переобучение модели

Переобучение осуществляется точно так же, как обучение модели. Единственное отличие заключается в том, что метод [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*), помимо данных, принимает в качестве входных данных параметры обученной модели и использует их как отправную точку в процессе переобучения.  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
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

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a>Сравнение параметров модели

Как узнать, произошло ли переобучение? Один из способов — это сравнить параметры переобученной и исходной модели. В представленном ниже примере как сравниваются значения веса в исходной и переобученной модели, а результаты выводятся на консоль.

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

В следующей таблице показано, как могут выглядеть выходные данные. 

|До преобразования | Переобученная модель | Различие |
|---|---|---|
| 33 039,86 | 56 293,76 | –23 253,9 |
| 29 099,14 | 49 586,03 | –20 486,89 |
| 28 938,38 | 48 609,23 | –19 670,85 |
| 30 484,02 | 53 745,43 | –23 261,41 |
