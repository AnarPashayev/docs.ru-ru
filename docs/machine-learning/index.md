---
title: Руководство по содержимому ML.NET
description: Узнайте, как создавать специализированные решения на базе искусственного интеллекта и интегрировать их в свои .NET-приложения с помощью ML.NET.
ms.date: 04/05/2019
ms.custom: seodec18
ms.openlocfilehash: de681daea5a29a121d350271ced4ccc2c0b1b533
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231335"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="e1d09-103">Руководство по содержимому ML.NET</span><span class="sxs-lookup"><span data-stu-id="e1d09-103">ML.NET Content Guide</span></span>

<span data-ttu-id="e1d09-104">В этой статье объясняются основные понятия и содержатся руководства и справочник по использованию API с ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e1d09-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="e1d09-105">Эта документация относится к предварительной версии ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e1d09-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="e1d09-106">Изложенная здесь информация может изменяться.</span><span class="sxs-lookup"><span data-stu-id="e1d09-106">Material may be subject to change.</span></span> <span data-ttu-id="e1d09-107">Дополнительные сведения см. в [обзоре ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e1d09-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="e1d09-108">Начало работы</span><span class="sxs-lookup"><span data-stu-id="e1d09-108">Get started</span></span>

<span data-ttu-id="e1d09-109">Чтобы выполнить установку и приступить к созданию в ML.NET, выполните [инструкции по началу работы](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span><span class="sxs-lookup"><span data-stu-id="e1d09-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="e1d09-110">См. дополнительные сведения об [ML.NET](what-is-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="e1d09-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="e1d09-111">См. дополнительные сведения об [обучении моделей в ML.NET](basic-concepts-model-training-in-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="e1d09-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="e1d09-112">Учебники</span><span class="sxs-lookup"><span data-stu-id="e1d09-112">Tutorials</span></span>

<span data-ttu-id="e1d09-113">[Анализ тональности с помощью модели двоичной классификации](./tutorials/sentiment-analysis.md) — показано, как создать приложение, которое определяет, является ли тональность позитивной или негативной.</span><span class="sxs-lookup"><span data-stu-id="e1d09-113">[Analyze sentiment using a binary classification model](./tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="e1d09-114">[Классификация проблем на GitHub с помощью модели многоклассовой классификации](./tutorials/github-issue-classification.md) Создание приложения, которое определяет метку области для проблемы в GitHub.</span><span class="sxs-lookup"><span data-stu-id="e1d09-114">[Classify GitHub issues using a multiclass classification model](./tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="e1d09-115">[Прогнозирование цен с помощью регрессионной модели](./tutorials/taxi-fare.md) — показано, как построить прогнозное приложение, которое использует многие факторы на основе исторических данных, чтобы определить ответ.</span><span class="sxs-lookup"><span data-stu-id="e1d09-115">[Predict prices using a regression model](./tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="e1d09-116">[Классификация цветков ириса по признакам](./tutorials/iris-clustering.md) — показано, как использовать модель кластеризации для анализа набора данных о цветках ириса.</span><span class="sxs-lookup"><span data-stu-id="e1d09-116">[Classify iris flowers by features](./tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span>

<span data-ttu-id="e1d09-117">[Создание системы рекомендации фильмов с помощью ML.NET](./tutorials/movie-recommmendation.md) — здесь показано, как создать приложение для рекомендации фильмов пользователям на основе их журнала.</span><span class="sxs-lookup"><span data-stu-id="e1d09-117">[Create a Movie Recommender with ML.NET](./tutorials/movie-recommmendation.md) shows you how to build a recommendation app to recommend movies to users based on their history.</span></span>

<span data-ttu-id="e1d09-118">[Создание классификатора пользовательских изображений ML.NET с помощью TensorFlow](./tutorials/image-classification.md) — здесь показано, как переобучить существующую модель Tensorflow для создания классификатора пользовательских изображений с помощью ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e1d09-118">[Build an ML.NET custom image classifier with TensorFlow](./tutorials/image-classification.md): demonstrates how to retrain an existing Tensorflow model to create a custom image classifier using ML.NET.</span></span>

## <a name="how-to-guide"></a><span data-ttu-id="e1d09-119">Практические руководства</span><span class="sxs-lookup"><span data-stu-id="e1d09-119">How to guide</span></span>

<span data-ttu-id="e1d09-120">[Создание приложения со списком матчей с помощью Infer.NET и вероятностного программирования](./how-to-guides/matchup-app-infer-net.md) — показано, как создать упрощенную версию приложения для сопоставления по аналогии с игрой Xbox.</span><span class="sxs-lookup"><span data-stu-id="e1d09-120">[Build a game match-up list app with Infer.NET and probabilistic programming](./how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="e1d09-121">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="e1d09-121">Resources</span></span>

<span data-ttu-id="e1d09-122">[Глоссарий по машинному обучению](./resources/glossary.md) — приведены основные термины.</span><span class="sxs-lookup"><span data-stu-id="e1d09-122">[Machine learning glossary](./resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="e1d09-123">[Задачи машинного обучения](./resources/tasks.md) — описаны задачи, такие как классификация и обнаружение аномалий.</span><span class="sxs-lookup"><span data-stu-id="e1d09-123">[Machine learning tasks](./resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="e1d09-124">[Преобразования данных](./resources/transforms.md) — описаны возможности подготовки данных в ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e1d09-124">[Data transforms](./resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>

## <a name="api-reference"></a><span data-ttu-id="e1d09-125">Справочник по интерфейсам API</span><span class="sxs-lookup"><span data-stu-id="e1d09-125">API reference</span></span>

<span data-ttu-id="e1d09-126">[Справочник по API ML.NET](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) — описаны доступные API.</span><span class="sxs-lookup"><span data-stu-id="e1d09-126">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
