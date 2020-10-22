---
title: Построитель моделей и принципы его работы
description: Сведения об использовании построителя моделей ML.NET для автоматического обучения модели машинного обучения
ms.date: 06/01/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: da6348fb5dde83827558b66b6115d681f08948db
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161144"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="261b5-103">Построитель моделей и принципы его работы</span><span class="sxs-lookup"><span data-stu-id="261b5-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="261b5-104">Построитель моделей ML.NET — это интуитивно понятное графическое расширение Visual Studio для создания, обучения и развертывания пользовательских моделей машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="261b5-105">Построитель моделей использует автоматизированное машинное обучение (AutoML) для анализа различных алгоритмов и параметров машинного обучения и выбора наиболее подходящих из них для конкретного сценария.</span><span class="sxs-lookup"><span data-stu-id="261b5-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="261b5-106">Для работы с построителем моделей не нужно быть экспертом в области машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="261b5-107">Все, что требуется, — это данные и проблема, которую нужно решить.</span><span class="sxs-lookup"><span data-stu-id="261b5-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="261b5-108">Построитель моделей генерирует код для добавления модели в приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="261b5-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Анимация: пользовательский интерфейс расширения "Построитель моделей" для Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="261b5-110">Построитель моделей в настоящее время находится на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="261b5-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="261b5-111">Сценарий</span><span class="sxs-lookup"><span data-stu-id="261b5-111">Scenario</span></span>

<span data-ttu-id="261b5-112">Построитель моделей может создавать модели машинного обучения для приложения на основе множества различных сценариев.</span><span class="sxs-lookup"><span data-stu-id="261b5-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="261b5-113">Сценарий описывает тип прогноза, который нужно сделать с использованием данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="261b5-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="261b5-114">For example:</span></span>

- <span data-ttu-id="261b5-115">прогнозирование будущего объема продаж продукта на основе исторических данных по продажам;</span><span class="sxs-lookup"><span data-stu-id="261b5-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="261b5-116">классификация тональности как положительной или отрицательной на основе отзывов клиентов;</span><span class="sxs-lookup"><span data-stu-id="261b5-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="261b5-117">определение того, является ли банковская операция мошеннической;</span><span class="sxs-lookup"><span data-stu-id="261b5-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="261b5-118">направление проблем, с которыми обращаются клиенты, на рассмотрение соответствующим сотрудникам компании.</span><span class="sxs-lookup"><span data-stu-id="261b5-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="261b5-119">Выбор подходящего сценария машинного обучения</span><span class="sxs-lookup"><span data-stu-id="261b5-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="261b5-120">В построителе моделей необходимо выбрать сценарий.</span><span class="sxs-lookup"><span data-stu-id="261b5-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="261b5-121">Тип сценария зависит от того, какой прогноз вы пытаетесь сделать.</span><span class="sxs-lookup"><span data-stu-id="261b5-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="261b5-122">Классификация текста</span><span class="sxs-lookup"><span data-stu-id="261b5-122">Text classification</span></span>

<span data-ttu-id="261b5-123">Классификация используется для разбиения данных по категориям.</span><span class="sxs-lookup"><span data-stu-id="261b5-123">Classification is used to categorize data into categories.</span></span>

![Схема с примерами двоичной классификации, включая обнаружение мошенничества, устранение рисков и блокировку приложений](media/binary-classification-examples.png)

![Примеры многоклассовой классификации, включая классификацию документов и продуктов, маршрутизацию запросов в службу поддержки и определение приоритетности клиентских проблем](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="261b5-126">Прогнозирование значений</span><span class="sxs-lookup"><span data-stu-id="261b5-126">Value prediction</span></span>

<span data-ttu-id="261b5-127">Регрессия служит для прогнозирования числовых значений.</span><span class="sxs-lookup"><span data-stu-id="261b5-127">Regression is used to predict numbers.</span></span>

![Схема с примерами регрессии, включая прогнозирование цен, прогнозирование продаж и прогнозное обслуживание](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="261b5-129">Классификация изображений</span><span class="sxs-lookup"><span data-stu-id="261b5-129">Image classification</span></span>

<span data-ttu-id="261b5-130">Классификация изображений помогает идентифицировать изображения разных категорий.</span><span class="sxs-lookup"><span data-stu-id="261b5-130">Image classification is used to identify images of different categories.</span></span> <span data-ttu-id="261b5-131">Например, различные виды рельефа, животных или производственного брака.</span><span class="sxs-lookup"><span data-stu-id="261b5-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="261b5-132">Вы можете использовать сценарий классификации, если у вас есть набор изображений и вы хотите классифицировать изображения по различным категориям.</span><span class="sxs-lookup"><span data-stu-id="261b5-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="object-detection"></a><span data-ttu-id="261b5-133">Обнаружение объектов</span><span class="sxs-lookup"><span data-stu-id="261b5-133">Object detection</span></span>

<span data-ttu-id="261b5-134">Обнаружение объектов используется для поиска и классификации сущностей на изображениях по категориям.</span><span class="sxs-lookup"><span data-stu-id="261b5-134">Object detection is used to locate and categorize entities within images.</span></span>  <span data-ttu-id="261b5-135">Например, на изображениях можно находить и идентифицировать людей и автомобили.</span><span class="sxs-lookup"><span data-stu-id="261b5-135">For example, locating and identifying cars and people in an image.</span></span>

<span data-ttu-id="261b5-136">Обнаружение объектов можно использовать, если изображения содержат несколько объектов разных типов.</span><span class="sxs-lookup"><span data-stu-id="261b5-136">You can use object detection when images contain multiple objects of different types.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="261b5-137">Рекомендация</span><span class="sxs-lookup"><span data-stu-id="261b5-137">Recommendation</span></span>

<span data-ttu-id="261b5-138">В сценарии рекомендации прогнозируется список предлагаемых элементов для конкретного пользователя на основе схожести с понравившимися, а также не понравившимися публикациями других пользователей.</span><span class="sxs-lookup"><span data-stu-id="261b5-138">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="261b5-139">Сценарий рекомендаций можно использовать, когда у вас есть набор пользователей и набор "продуктов", таких как элементы для покупки, фильмы, книги или телепередачи, наряду с набором пользовательских "оценок" этих продуктов.</span><span class="sxs-lookup"><span data-stu-id="261b5-139">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="261b5-140">Среда</span><span class="sxs-lookup"><span data-stu-id="261b5-140">Environment</span></span>

<span data-ttu-id="261b5-141">В зависимости от сценария, модель машинного обучения можно обучить локально на компьютере или в облаке в Azure.</span><span class="sxs-lookup"><span data-stu-id="261b5-141">You can train your machine learning model locally on your machine or in the cloud on Azure, depending on the scenario.</span></span>

<span data-ttu-id="261b5-142">При локальном обучении вы работаете в пределах ограничений ресурсов компьютера (ЦП, память и диск).</span><span class="sxs-lookup"><span data-stu-id="261b5-142">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="261b5-143">При обучении в облаке ресурсы можно масштабировать в соответствии с потребностями вашего сценария, особенно для больших наборов данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-143">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="261b5-144">Локальное обучение на ЦП поддерживается для всех сценариев, за исключением обнаружения объектов.</span><span class="sxs-lookup"><span data-stu-id="261b5-144">Local CPU training is supported for all scenarios except Object Detection.</span></span>

<span data-ttu-id="261b5-145">Локальное обучение на графическом процессоре поддерживается для классификации изображений.</span><span class="sxs-lookup"><span data-stu-id="261b5-145">Local GPU training is supported for Image Classification.</span></span>

<span data-ttu-id="261b5-146">Обучение в Azure поддерживается для классификации изображений и обнаружения объектов.</span><span class="sxs-lookup"><span data-stu-id="261b5-146">Azure training is supported for Image Classification and Object Detection.</span></span>

## <a name="data"></a><span data-ttu-id="261b5-147">Данные</span><span class="sxs-lookup"><span data-stu-id="261b5-147">Data</span></span>

<span data-ttu-id="261b5-148">После выбора сценария построитель моделей попросит вас предоставить набор данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="261b5-149">Данные используются для обучения, оценки и выбора оптимальной модели для сценария.</span><span class="sxs-lookup"><span data-stu-id="261b5-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Схема, демонстрирующая этапы работы построителя моделей](media/model-builder-steps.png)

<span data-ttu-id="261b5-151">Построитель моделей поддерживает наборы данных в форматах TSV, CSV, TXT, а также в формате базы данных SQL.</span><span class="sxs-lookup"><span data-stu-id="261b5-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="261b5-152">При использовании TXT-файла добавьте в него строку заголовка и разделите столбцы с помощью символов `,`, `;` или `/t`.</span><span class="sxs-lookup"><span data-stu-id="261b5-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="261b5-153">При использовании набора данных, состоящего из изображений, поддерживаются файлы с такими расширениями: `.jpg` и `.png`.</span><span class="sxs-lookup"><span data-stu-id="261b5-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="261b5-154">Дополнительные сведения см. в статье [Загрузка данных для обучения в построитель моделей](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="261b5-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="261b5-155">Выбор результата для прогнозирования (метка)</span><span class="sxs-lookup"><span data-stu-id="261b5-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="261b5-156">Набор данных — это таблица, строки которой содержат образцы для обучения, а столбцы — атрибуты.</span><span class="sxs-lookup"><span data-stu-id="261b5-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="261b5-157">В каждой строке есть:</span><span class="sxs-lookup"><span data-stu-id="261b5-157">Each row has:</span></span>

- <span data-ttu-id="261b5-158">**метка** (атрибут, который нужно спрогнозировать);</span><span class="sxs-lookup"><span data-stu-id="261b5-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="261b5-159">**признаки** (атрибуты, исходя из которых прогнозируется метка).</span><span class="sxs-lookup"><span data-stu-id="261b5-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="261b5-160">В сценарии прогнозирования цен на недвижимость признаками могут быть:</span><span class="sxs-lookup"><span data-stu-id="261b5-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="261b5-161">площадь дома;</span><span class="sxs-lookup"><span data-stu-id="261b5-161">the square footage of the house</span></span>
- <span data-ttu-id="261b5-162">количество спален и ванных комнат;</span><span class="sxs-lookup"><span data-stu-id="261b5-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="261b5-163">почтовый индекс.</span><span class="sxs-lookup"><span data-stu-id="261b5-163">the zip code</span></span>

<span data-ttu-id="261b5-164">Метка — это историческая цена на дом данной площади, с данным количеством спален и ванных комнат, а также почтовым индексом.</span><span class="sxs-lookup"><span data-stu-id="261b5-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Таблица цен на недвижимость, содержащая признаки (площадь, количество комнат, почтовый индекс) и метку (цена)](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="261b5-166">Примеры наборов данных</span><span class="sxs-lookup"><span data-stu-id="261b5-166">Example datasets</span></span>

<span data-ttu-id="261b5-167">Если у вас нет собственного набора данных, можно воспользоваться одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="261b5-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="261b5-168">Сценарий</span><span class="sxs-lookup"><span data-stu-id="261b5-168">Scenario</span></span>|<span data-ttu-id="261b5-169">Пример</span><span class="sxs-lookup"><span data-stu-id="261b5-169">Example</span></span>|<span data-ttu-id="261b5-170">Данные</span><span class="sxs-lookup"><span data-stu-id="261b5-170">Data</span></span>|<span data-ttu-id="261b5-171">Метка</span><span class="sxs-lookup"><span data-stu-id="261b5-171">Label</span></span>|<span data-ttu-id="261b5-172">Функции</span><span class="sxs-lookup"><span data-stu-id="261b5-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="261b5-173">Классификация</span><span class="sxs-lookup"><span data-stu-id="261b5-173">Classification</span></span>|<span data-ttu-id="261b5-174">Прогнозирование аномалий продаж</span><span class="sxs-lookup"><span data-stu-id="261b5-174">Predict sales anomalies</span></span>|[<span data-ttu-id="261b5-175">данные по продажам продуктов</span><span class="sxs-lookup"><span data-stu-id="261b5-175">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="261b5-176">Продажи продукта</span><span class="sxs-lookup"><span data-stu-id="261b5-176">Product Sales</span></span>|<span data-ttu-id="261b5-177">Месяц</span><span class="sxs-lookup"><span data-stu-id="261b5-177">Month</span></span>|
||<span data-ttu-id="261b5-178">Прогнозирование тональности комментариев веб-сайта</span><span class="sxs-lookup"><span data-stu-id="261b5-178">Predict sentiment of website comments</span></span>|[<span data-ttu-id="261b5-179">данные по комментариям на веб-сайте</span><span class="sxs-lookup"><span data-stu-id="261b5-179">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="261b5-180">Метка (0 — отрицательная тональность, 1 — положительная)</span><span class="sxs-lookup"><span data-stu-id="261b5-180">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="261b5-181">Комментарий, год</span><span class="sxs-lookup"><span data-stu-id="261b5-181">Comment, Year</span></span>|
||<span data-ttu-id="261b5-182">Прогнозирование мошеннических операций с кредитной картой</span><span class="sxs-lookup"><span data-stu-id="261b5-182">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="261b5-183">данные по кредитным картам</span><span class="sxs-lookup"><span data-stu-id="261b5-183">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CCFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="261b5-184">Класс (1 — мошенничество, 0 — нет)</span><span class="sxs-lookup"><span data-stu-id="261b5-184">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="261b5-185">Сумма, V1–V28 (анонимизированные признаки)</span><span class="sxs-lookup"><span data-stu-id="261b5-185">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="261b5-186">Прогнозирование типа проблемы в репозитории GitHub</span><span class="sxs-lookup"><span data-stu-id="261b5-186">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="261b5-187">Данные по проблемам на GitHub</span><span class="sxs-lookup"><span data-stu-id="261b5-187">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="261b5-188">Область</span><span class="sxs-lookup"><span data-stu-id="261b5-188">Area</span></span>|<span data-ttu-id="261b5-189">Название, описание</span><span class="sxs-lookup"><span data-stu-id="261b5-189">Title, Description</span></span>|
|<span data-ttu-id="261b5-190">Прогнозирование значений</span><span class="sxs-lookup"><span data-stu-id="261b5-190">Value prediction</span></span>|<span data-ttu-id="261b5-191">Прогнозирование платы за такси</span><span class="sxs-lookup"><span data-stu-id="261b5-191">Predict taxi fare price</span></span>|[<span data-ttu-id="261b5-192">данные по платам за такси</span><span class="sxs-lookup"><span data-stu-id="261b5-192">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="261b5-193">Плата</span><span class="sxs-lookup"><span data-stu-id="261b5-193">Fare</span></span>|<span data-ttu-id="261b5-194">Время поездки, расстояние</span><span class="sxs-lookup"><span data-stu-id="261b5-194">Trip time, distance</span></span>|
|<span data-ttu-id="261b5-195">Классификация изображений</span><span class="sxs-lookup"><span data-stu-id="261b5-195">Image classification</span></span>|<span data-ttu-id="261b5-196">Прогнозирование категории, к которой относится цветок</span><span class="sxs-lookup"><span data-stu-id="261b5-196">Predict the category of a flower</span></span> |[<span data-ttu-id="261b5-197">изображения цветов</span><span class="sxs-lookup"><span data-stu-id="261b5-197">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="261b5-198">Вид цветов: маргаритки, одуванчики, розы, подсолнухи, тюльпаны</span><span class="sxs-lookup"><span data-stu-id="261b5-198">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="261b5-199">Данные изображения</span><span class="sxs-lookup"><span data-stu-id="261b5-199">The image data itself</span></span>|
|<span data-ttu-id="261b5-200">Рекомендация</span><span class="sxs-lookup"><span data-stu-id="261b5-200">Recommendation</span></span>|<span data-ttu-id="261b5-201">Прогнозирование фильмов, которые понравятся пользователям</span><span class="sxs-lookup"><span data-stu-id="261b5-201">Predict movies that someone will like</span></span>|[<span data-ttu-id="261b5-202">рейтинги фильмов</span><span class="sxs-lookup"><span data-stu-id="261b5-202">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="261b5-203">пользователи, фильмы</span><span class="sxs-lookup"><span data-stu-id="261b5-203">Users, Movies</span></span>|<span data-ttu-id="261b5-204">Рейтинги</span><span class="sxs-lookup"><span data-stu-id="261b5-204">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="261b5-205">Обучение</span><span class="sxs-lookup"><span data-stu-id="261b5-205">Train</span></span>

<span data-ttu-id="261b5-206">После выбора сценария, среды, данных и метки Model Builder обучает модель.</span><span class="sxs-lookup"><span data-stu-id="261b5-206">Once you select your scenario, environment, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="261b5-207">Сведения об обучении</span><span class="sxs-lookup"><span data-stu-id="261b5-207">What is training?</span></span>

<span data-ttu-id="261b5-208">Обучение — это автоматический процесс, посредством которого построитель моделей учит модель отвечать на вопросы в рамках сценария.</span><span class="sxs-lookup"><span data-stu-id="261b5-208">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="261b5-209">После обучения модель может делать прогнозы на основе новых входных данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-209">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="261b5-210">Например, если модель прогнозирует цены на недвижимость и на рынке появляется новый дом, она может спрогнозировать цену его продажи.</span><span class="sxs-lookup"><span data-stu-id="261b5-210">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="261b5-211">Так как построитель моделей использует автоматизированное машинное обучение (AutoML), во время обучения вводить данные или производить настройку не нужно.</span><span class="sxs-lookup"><span data-stu-id="261b5-211">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="261b5-212">Требуемая длительность обучения</span><span class="sxs-lookup"><span data-stu-id="261b5-212">How long should I train for?</span></span>

<span data-ttu-id="261b5-213">С помощью AutoML построитель моделей изучает несколько моделей, определяя самую эффективную.</span><span class="sxs-lookup"><span data-stu-id="261b5-213">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="261b5-214">Более длительное время обучения позволяет AutoML исследовать больше моделей с более широким диапазоном параметров.</span><span class="sxs-lookup"><span data-stu-id="261b5-214">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="261b5-215">В приведенной ниже таблице указано обобщенное среднее время, необходимое для получения хорошей эффективности для набора примеров наборов данных на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="261b5-215">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="261b5-216">Размер набора данных</span><span class="sxs-lookup"><span data-stu-id="261b5-216">Dataset size</span></span>|<span data-ttu-id="261b5-217">Среднее время обучения</span><span class="sxs-lookup"><span data-stu-id="261b5-217">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="261b5-218">0–10 МБ</span><span class="sxs-lookup"><span data-stu-id="261b5-218">0 - 10 MB</span></span>|<span data-ttu-id="261b5-219">10 с</span><span class="sxs-lookup"><span data-stu-id="261b5-219">10 sec</span></span>|
|<span data-ttu-id="261b5-220">10–100 МБ</span><span class="sxs-lookup"><span data-stu-id="261b5-220">10 - 100 MB</span></span>|<span data-ttu-id="261b5-221">10 мин</span><span class="sxs-lookup"><span data-stu-id="261b5-221">10 min</span></span>|
|<span data-ttu-id="261b5-222">100–500 МБ</span><span class="sxs-lookup"><span data-stu-id="261b5-222">100 - 500 MB</span></span>|<span data-ttu-id="261b5-223">30 мин</span><span class="sxs-lookup"><span data-stu-id="261b5-223">30 min</span></span>|
|<span data-ttu-id="261b5-224">500 МБ — 1 ГБ</span><span class="sxs-lookup"><span data-stu-id="261b5-224">500 - 1 GB</span></span>|<span data-ttu-id="261b5-225">60 мин</span><span class="sxs-lookup"><span data-stu-id="261b5-225">60 min</span></span>|
|<span data-ttu-id="261b5-226">Более 1 ГБ</span><span class="sxs-lookup"><span data-stu-id="261b5-226">1 GB+</span></span>|<span data-ttu-id="261b5-227">Более 3 часов</span><span class="sxs-lookup"><span data-stu-id="261b5-227">3+ hours</span></span>|

<span data-ttu-id="261b5-228">Это ориентировочные числа.</span><span class="sxs-lookup"><span data-stu-id="261b5-228">These numbers are a guide only.</span></span> <span data-ttu-id="261b5-229">Точная продолжительность обучения зависит от:</span><span class="sxs-lookup"><span data-stu-id="261b5-229">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="261b5-230">количества признаков (столбцов), используемых в качестве входных данных для модели;</span><span class="sxs-lookup"><span data-stu-id="261b5-230">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="261b5-231">типа столбцов;</span><span class="sxs-lookup"><span data-stu-id="261b5-231">the type of columns</span></span>
- <span data-ttu-id="261b5-232">задачи машинного обучения;</span><span class="sxs-lookup"><span data-stu-id="261b5-232">the ML task</span></span>
- <span data-ttu-id="261b5-233">производительности ЦП, диска и памяти компьютера, используемого для обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-233">the CPU, disk, and memory performance of the machine used for training</span></span>

<span data-ttu-id="261b5-234">Обычно рекомендуется использовать более 100 строк, так как наборы данных меньшего размера могут не дать никаких результатов, и обучение может занять значительно больше времени.</span><span class="sxs-lookup"><span data-stu-id="261b5-234">It's generally advised that you use more than 100 rows as datasets with less than that may not produce any results and may take a significantly longer time to train.</span></span>

## <a name="evaluate"></a><span data-ttu-id="261b5-235">Оценка</span><span class="sxs-lookup"><span data-stu-id="261b5-235">Evaluate</span></span>

<span data-ttu-id="261b5-236">Оценка — это процесс измерения эффективности модели.</span><span class="sxs-lookup"><span data-stu-id="261b5-236">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="261b5-237">Построитель моделей использует обученную модель для составления прогнозов на основе новых данных с последующим измерением их точности.</span><span class="sxs-lookup"><span data-stu-id="261b5-237">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="261b5-238">Построитель моделей разделяет обучающие данные на набор для обучения и тестовый набор.</span><span class="sxs-lookup"><span data-stu-id="261b5-238">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="261b5-239">Обучающие данные (80 %) служат для обучения модели, а тестовые (20 %) резервируются для ее оценки.</span><span class="sxs-lookup"><span data-stu-id="261b5-239">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="261b5-240">Как определить эффективность модели?</span><span class="sxs-lookup"><span data-stu-id="261b5-240">How do I understand my model performance?</span></span>

<span data-ttu-id="261b5-241">Сценарий сопоставляется с задачей машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-241">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="261b5-242">Каждая задача машинного обучения имеет собственный набор метрик оценки.</span><span class="sxs-lookup"><span data-stu-id="261b5-242">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="261b5-243">Прогнозирование значений</span><span class="sxs-lookup"><span data-stu-id="261b5-243">Value prediction</span></span>

<span data-ttu-id="261b5-244">Метрика по умолчанию для проблем прогнозирования значений — RSquared, где допустимо значение в диапазоне от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="261b5-244">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="261b5-245">1 — наилучшее из возможных значений. Чем ближе значение коэффициента детерминации к 1, тем выше эффективность вашей модели.</span><span class="sxs-lookup"><span data-stu-id="261b5-245">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="261b5-246">Другие метрики, такие как абсолютная потеря, квадратичная потеря и среднеквадратичная потеря, являются дополнительными. Их можно использовать для анализа модели и сравнения ее с другими моделями прогнозирования значений.</span><span class="sxs-lookup"><span data-stu-id="261b5-246">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="261b5-247">Классификация (2 категории)</span><span class="sxs-lookup"><span data-stu-id="261b5-247">Classification (2 categories)</span></span>

<span data-ttu-id="261b5-248">Метрика по умолчанию для задач классификации — точность.</span><span class="sxs-lookup"><span data-stu-id="261b5-248">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="261b5-249">Точность — это доля правильных прогнозов, которые модель делает на основе тестового набора данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-249">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="261b5-250">Чем ближе она к 100 % или 1,0, тем лучше.</span><span class="sxs-lookup"><span data-stu-id="261b5-250">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="261b5-251">Чтобы модель считалась приемлемой, другие метрики, например площадь под кривой, которая представляет собой отношение доли истинно положительных результатов к доле ложноположительных результатов, должны превышать 0,50.</span><span class="sxs-lookup"><span data-stu-id="261b5-251">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="261b5-252">Дополнительные метрики, такие как показатель F1, можно использовать для контроля баланса между точностью и полнотой.</span><span class="sxs-lookup"><span data-stu-id="261b5-252">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="261b5-253">Классификация (3 и более категорий)</span><span class="sxs-lookup"><span data-stu-id="261b5-253">Classification (3+ categories)</span></span>

<span data-ttu-id="261b5-254">Метрика по умолчанию для многоклассовой классификации — микроточность.</span><span class="sxs-lookup"><span data-stu-id="261b5-254">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="261b5-255">Чем ближе значение микроточности к 100 % или 1,0, тем лучше.</span><span class="sxs-lookup"><span data-stu-id="261b5-255">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="261b5-256">Еще одна важная метрика для многоклассовой классификации — макроточность. Подобно микроточности, чем ближе ее значение к 1,0, тем лучше.</span><span class="sxs-lookup"><span data-stu-id="261b5-256">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="261b5-257">Ниже приведены лучшие определения этих двух типов точности:</span><span class="sxs-lookup"><span data-stu-id="261b5-257">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="261b5-258">Микроточность — как часто входящий запрос передается подходящей команде сотрудников?</span><span class="sxs-lookup"><span data-stu-id="261b5-258">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="261b5-259">Макроточность — как часто входящий запрос подходит для команды в среднем случае?</span><span class="sxs-lookup"><span data-stu-id="261b5-259">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="261b5-260">Дополнительные сведения о метриках оценки</span><span class="sxs-lookup"><span data-stu-id="261b5-260">More information on evaluation metrics</span></span>

<span data-ttu-id="261b5-261">Дополнительные сведения см. в статье [Метрики оценки модели](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="261b5-261">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="261b5-262">Улучшение</span><span class="sxs-lookup"><span data-stu-id="261b5-262">Improve</span></span>

<span data-ttu-id="261b5-263">Если точность модели недостаточно высока, можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="261b5-263">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="261b5-264">Увеличить время обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-264">Train for a longer period of time.</span></span> <span data-ttu-id="261b5-265">Чем дольше длится обучение, тем больше алгоритмов и параметров может опробовать система машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="261b5-265">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="261b5-266">Добавить больше данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-266">Add more data.</span></span> <span data-ttu-id="261b5-267">Иногда объем данных недостаточен для обучения высококачественной модели машинного обучения. Это особенно справедливо для наборов данных с небольшим количеством примеров.</span><span class="sxs-lookup"><span data-stu-id="261b5-267">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.This is especially true with datasets that have a small number of examples.</span></span>

- <span data-ttu-id="261b5-268">Сбалансировать данные.</span><span class="sxs-lookup"><span data-stu-id="261b5-268">Balance your data.</span></span> <span data-ttu-id="261b5-269">Для задач классификации обучающий набор должен быть сбалансирован по всем категориям.</span><span class="sxs-lookup"><span data-stu-id="261b5-269">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="261b5-270">Например, если имеются четыре класса для 100 образцов, причем первые два класса (тег1 и тег2) используются для 90 записей, а другие два (тег3 и тег4) — для остальных 10 записей, несбалансированность данных может сказаться на правильности прогнозирования классов тег3 и тег4.</span><span class="sxs-lookup"><span data-stu-id="261b5-270">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="261b5-271">Код</span><span class="sxs-lookup"><span data-stu-id="261b5-271">Code</span></span>

<span data-ttu-id="261b5-272">После этапа оценки построитель моделей предоставляет файл модели и код, с помощью которого можно добавить модель в свое приложение.</span><span class="sxs-lookup"><span data-stu-id="261b5-272">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="261b5-273">Модели ML.NET сохраняются как ZIP-файлы.</span><span class="sxs-lookup"><span data-stu-id="261b5-273">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="261b5-274">Код для загрузки и использования модели добавляется в решение как новый проект.</span><span class="sxs-lookup"><span data-stu-id="261b5-274">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="261b5-275">Кроме того, построитель моделей добавляет для примера консольное приложение, которое можно запустить, чтобы увидеть модель в действии.</span><span class="sxs-lookup"><span data-stu-id="261b5-275">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="261b5-276">Построитель моделей также выводит код, использовавшийся для создания модели, чтобы можно было понять, как именно она формировалась.</span><span class="sxs-lookup"><span data-stu-id="261b5-276">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="261b5-277">Код обучения модели можно использовать для повторного обучения на основе новых данных.</span><span class="sxs-lookup"><span data-stu-id="261b5-277">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="261b5-278">Что дальше?</span><span class="sxs-lookup"><span data-stu-id="261b5-278">What's next?</span></span>

<span data-ttu-id="261b5-279">[Установите](how-to-guides/install-model-builder.md) расширение "Построитель моделей" для Visual Studio</span><span class="sxs-lookup"><span data-stu-id="261b5-279">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="261b5-280">Попробуйте [сценарий прогнозирования цен или любой сценарий регрессии](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="261b5-280">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
