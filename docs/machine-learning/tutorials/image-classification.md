---
title: Учебник. Создание модели классификации изображений ML.NET на основе предварительно обученной модели TensorFlow
description: Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET. Модель TensorFlow была обучена для классификации изображений по тысячам категорий. Модель ML.NET использует передачу обучения, чтобы классифицировать изображения по меньшему количеству более широких категорий.
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 28d8c18721bd353e961284935758a87679c8c8e0
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353693"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="a1a31-105">Учебник. Создание модели классификации изображений ML.NET на основе предварительно обученной модели TensorFlow</span><span class="sxs-lookup"><span data-stu-id="a1a31-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="a1a31-106">Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1a31-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="a1a31-107">Модель TensorFlow была обучена для классификации изображений по тысячам категорий.</span><span class="sxs-lookup"><span data-stu-id="a1a31-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="a1a31-108">Модель ML.NET использует часть модели TensorFlow в своем конвейере для обучения модели, классифицирующей изображения по 3-м категориям.</span><span class="sxs-lookup"><span data-stu-id="a1a31-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="a1a31-109">Обучение модели для [классификации изображений](https://en.wikipedia.org/wiki/Outline_of_object_recognition) с нуля предусматривает настройку нескольких миллионов параметров, а также использование огромных объемов помеченных данных обучения и вычислительных ресурсов (сотни часов работы GPU).</span><span class="sxs-lookup"><span data-stu-id="a1a31-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="a1a31-110">Хотя передача обучения не настолько эффективна, как обучение пользовательской модели с нуля, этот подход позволяет значительно ускорить соответствующий процесс с использованием всего нескольких тысяч изображений (а не миллионов помеченных изображений) для быстрого создания пользовательской модели (в пределах часа на компьютере без GPU).</span><span class="sxs-lookup"><span data-stu-id="a1a31-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="a1a31-111">В этом учебнике этот процесс еще более уменьшен: используется только десяток изображений для обучения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="a1a31-112">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="a1a31-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a1a31-113">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="a1a31-113">Understand the problem</span></span>
> * <span data-ttu-id="a1a31-114">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="a1a31-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="a1a31-115">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="a1a31-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="a1a31-116">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="a1a31-116">Classify a test image</span></span>

<span data-ttu-id="a1a31-117">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="a1a31-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="a1a31-118">Обратите внимание на то, что по умолчанию конфигурации проекта .NET в этом руководстве предназначена для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="a1a31-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="a1a31-119">Что собой представляет передача обучения?</span><span class="sxs-lookup"><span data-stu-id="a1a31-119">What is transfer learning?</span></span>

<span data-ttu-id="a1a31-120">Передача обучения — это процесс использования знаний, полученных при решении одной проблемы, и применения их к другой, но похожей проблеме.</span><span class="sxs-lookup"><span data-stu-id="a1a31-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="a1a31-121">В этом учебнике используется часть модели TensorFlow, обученной для классификации изображений по тысяче категорий, в модели ML.NET, которая классифицирует изображения по 3-м категориям.</span><span class="sxs-lookup"><span data-stu-id="a1a31-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1a31-122">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="a1a31-122">Prerequisites</span></span>

* <span data-ttu-id="a1a31-123">[Visual Studio 2017 15.6 или более поздней версии](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="a1a31-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="a1a31-124">Пакет Nuget для Microsoft.ML 1.3.1.</span><span class="sxs-lookup"><span data-stu-id="a1a31-124">Microsoft.ML 1.3.1 Nuget package</span></span>
* <span data-ttu-id="a1a31-125">Пакет Nuget для Microsoft.ML.ImageAnalytics 1.3.1.</span><span class="sxs-lookup"><span data-stu-id="a1a31-125">Microsoft.ML.ImageAnalytics 1.3.1 Nuget package</span></span>
* <span data-ttu-id="a1a31-126">Пакет Nuget для Microsoft.ML.TensorFlow 1.3.1.</span><span class="sxs-lookup"><span data-stu-id="a1a31-126">Microsoft.ML.TensorFlow 1.3.1 Nuget package</span></span>

* [<span data-ttu-id="a1a31-127">ZIP-файл каталога ресурсов руководства.</span><span class="sxs-lookup"><span data-stu-id="a1a31-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="a1a31-128">Модель машинного обучения Inception версии 1</span><span class="sxs-lookup"><span data-stu-id="a1a31-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="a1a31-129">Выбор типа задачи машинного обучения</span><span class="sxs-lookup"><span data-stu-id="a1a31-129">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="a1a31-130">Глубокое обучение</span><span class="sxs-lookup"><span data-stu-id="a1a31-130">Deep learning</span></span>

<span data-ttu-id="a1a31-131">[Глубокое обучение](https://en.wikipedia.org/wiki/Deep_learning) — это разновидность машинного обучения, которая произвела революцию в области компьютерного зрения и распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="a1a31-131">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="a1a31-132">Модели глубокого обучения обучаются на крупных наборах [помеченных данных](https://en.wikipedia.org/wiki/Labeled_data) с использованием [нейронных сетей](https://en.wikipedia.org/wiki/Artificial_neural_network), которые содержат множество слоев обучения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-132">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="a1a31-133">Глубокое обучение:</span><span class="sxs-lookup"><span data-stu-id="a1a31-133">Deep learning:</span></span>

* <span data-ttu-id="a1a31-134">лучше выполняет некоторые задачи, например в области компьютерного зрения;</span><span class="sxs-lookup"><span data-stu-id="a1a31-134">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="a1a31-135">Требует огромных объемов данных для обучения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-135">Requires huge amounts of training data.</span></span>

<span data-ttu-id="a1a31-136">Классификация изображений — это типичная задача Машинного обучения, которая позволяет автоматически классифицировать изображения по категориям, например:</span><span class="sxs-lookup"><span data-stu-id="a1a31-136">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="a1a31-137">для определения того, содержит ли изображение человеческое лицо;</span><span class="sxs-lookup"><span data-stu-id="a1a31-137">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="a1a31-138">для различения изображений котов и собак.</span><span class="sxs-lookup"><span data-stu-id="a1a31-138">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="a1a31-139">Она также помогает определить тип объекта на изображении — еда, игрушка или прибор:</span><span class="sxs-lookup"><span data-stu-id="a1a31-139">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="a1a31-140">![Изображение с пиццей](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Изображение с плюшевым мишкой](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Изображение с тостером](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1a31-140">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="a1a31-141">Изображения выше принадлежат Викискладу и имеют следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="a1a31-141">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="a1a31-142">220px-Pepperoni_pizza.jpg, открытый источник, https://commons.wikimedia.org/w/index.php?curid=79505;</span><span class="sxs-lookup"><span data-stu-id="a1a31-142">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="a1a31-143">119px-Nalle_-_a_small_brown_teddy_bear.jpg, автор — [Jonik](https://commons.wikimedia.org/wiki/User:Jonik), автофотография, лицензия CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166;</span><span class="sxs-lookup"><span data-stu-id="a1a31-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="a1a31-144">193px-Broodrooster.jpg, автор — [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972), собственное фото, лицензия CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.</span><span class="sxs-lookup"><span data-stu-id="a1a31-144">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="a1a31-145">Модель `Inception model` обучена классифицировать изображения по тысяче категорий, но в этом учебнике вам столько категорий не нужно. Вам также нужны четко определенные категории.</span><span class="sxs-lookup"><span data-stu-id="a1a31-145">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="a1a31-146">Перейдем к этапу передачи (`transfer`) этого процесса передачи обучения (`transfer learning`).</span><span class="sxs-lookup"><span data-stu-id="a1a31-146">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="a1a31-147">Вы можете передать способность `Inception model` распознавать и классифицировать изображения в новые ограниченные категории своего классификатора изображений.</span><span class="sxs-lookup"><span data-stu-id="a1a31-147">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="a1a31-148">еда;</span><span class="sxs-lookup"><span data-stu-id="a1a31-148">Food</span></span>
* <span data-ttu-id="a1a31-149">игрушка;</span><span class="sxs-lookup"><span data-stu-id="a1a31-149">Toy</span></span>
* <span data-ttu-id="a1a31-150">прибор.</span><span class="sxs-lookup"><span data-stu-id="a1a31-150">Appliance</span></span>

<span data-ttu-id="a1a31-151">В этом учебнике используется модель глубокого обучения TensorFlow [Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), популярная модель распознавания изображений, обученная с помощью набора данных `ImageNet`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-151">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="a1a31-152">Модель TensorFlow классифицирует все изображения по тысячам классов, таких как "зонт", "жакет" и "посудомоечная машина".</span><span class="sxs-lookup"><span data-stu-id="a1a31-152">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="a1a31-153">Так как `Inception model` уже обучена на тысячах различных изображений, она содержит [признаки изображений](https://en.wikipedia.org/wiki/Feature_(computer_vision)), необходимые для их идентификации.</span><span class="sxs-lookup"><span data-stu-id="a1a31-153">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="a1a31-154">Мы можем использовать эти внутренние признаки изображений в модели для обучения новой модели с гораздо меньшим числом классов.</span><span class="sxs-lookup"><span data-stu-id="a1a31-154">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="a1a31-155">Как показано на схеме ниже, вам нужно добавить ссылки на пакеты NuGet ML.NET в приложения .NET Core или .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1a31-155">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="a1a31-156">На внутреннем уровне ML.NET включает и ссылается на встроенную библиотеку `TensorFlow`, которая позволяет создавать код, загружающий существующую обученную модель `TensorFlow`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-156">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Схема преобразования ML.NET с использованием TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="a1a31-158">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="a1a31-158">Multiclass classification</span></span>

<span data-ttu-id="a1a31-159">После использования модели Inception TensorFlow для извлечения признаков, подходящих в качестве входных данных для классического алгоритма машинного обучения, мы добавим [многоклассовый классификатор](../resources/tasks.md#multiclass-classification) ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1a31-159">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="a1a31-160">В этом случае используется алгоритм [мультиномиальной логистической регрессии](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="a1a31-160">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="a1a31-161">Алгоритм, реализованный этим инструктором, хорошо работает в задачах с большим количеством признаков, что характерно для модели глубокого обучения, работающей с данными изображений.</span><span class="sxs-lookup"><span data-stu-id="a1a31-161">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="a1a31-162">Данные</span><span class="sxs-lookup"><span data-stu-id="a1a31-162">Data</span></span>

<span data-ttu-id="a1a31-163">Доступны два источника данных: файл `.tsv` и файлы образов.</span><span class="sxs-lookup"><span data-stu-id="a1a31-163">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="a1a31-164">Файл `tags.tsv` содержит два столбца: первый определен как `ImagePath`, а во втором указана метка `Label`, соответствующая изображению.</span><span class="sxs-lookup"><span data-stu-id="a1a31-164">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="a1a31-165">В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a1a31-165">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="a1a31-166">Изображения для обучения и тестирования расположены в папках ресурсов, которые вы скачали в виде ZIP-файла.</span><span class="sxs-lookup"><span data-stu-id="a1a31-166">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="a1a31-167">Эти изображения принадлежат Викискладу.</span><span class="sxs-lookup"><span data-stu-id="a1a31-167">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="a1a31-168">*[Викисклад](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), бесплатный репозиторий мультимедиа.*</span><span class="sxs-lookup"><span data-stu-id="a1a31-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="a1a31-169">Получено в 10:48 17 октября 2018 г. со страниц: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="a1a31-169">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="a1a31-170">Установка</span><span class="sxs-lookup"><span data-stu-id="a1a31-170">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="a1a31-171">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="a1a31-171">Create a project</span></span>

1. <span data-ttu-id="a1a31-172">Создайте **консольное приложение .NET Core** с именем TransferLearningTF.</span><span class="sxs-lookup"><span data-stu-id="a1a31-172">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="a1a31-173">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="a1a31-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="a1a31-174">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="a1a31-175">Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор" и выполните поиск **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="a1a31-176">Щелкните раскрывающийся список **Версия**, выберите пакет **1.3.1** в списке и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-176">Click on the **Version** drop-down, select the **1.3.1** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="a1a31-177">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-177">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="a1a31-178">Нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с условиями лицензионного соглашения для указанных пакетов.</span><span class="sxs-lookup"><span data-stu-id="a1a31-178">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="a1a31-179">Повторите эти шаги для пакетов **Microsoft.ML.ImageAnalytics версии 1.3.1** и **Microsoft.ML.TensorFlow версии 1.3.1**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-179">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.3.1** and **Microsoft.ML.TensorFlow v1.3.1**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="a1a31-180">Скачивание ресурсов</span><span class="sxs-lookup"><span data-stu-id="a1a31-180">Download assets</span></span>

1. <span data-ttu-id="a1a31-181">Скачайте [ZIP-файл каталога с ресурсами проекта](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) и распакуйте его.</span><span class="sxs-lookup"><span data-stu-id="a1a31-181">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="a1a31-182">Скопируйте каталог `assets` в каталог проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="a1a31-182">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="a1a31-183">Этот каталог и его подкаталоги содержат данные и файлы поддержки (за исключением модели Inception, которую вы скачаете и добавите на следующем шаге), необходимые для работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="a1a31-183">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="a1a31-184">Скачайте [модель Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) и распакуйте ее.</span><span class="sxs-lookup"><span data-stu-id="a1a31-184">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="a1a31-185">Скопируйте содержание каталога `inception5h`, который вы распаковали, в каталог `assets/inputs-train/inception` проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="a1a31-185">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inputs-train/inception` directory.</span></span> <span data-ttu-id="a1a31-186">Этот каталог содержит модель и дополнительные файлы поддержки, необходимые для работы с этим руководством, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="a1a31-186">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Содержание каталога Inception](./media/image-classification/inception-files.png)

1. <span data-ttu-id="a1a31-188">В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге и подкаталогах ресурсов и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-188">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="a1a31-189">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a1a31-190">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="a1a31-190">Create classes and define paths</span></span>

1. <span data-ttu-id="a1a31-191">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="a1a31-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="a1a31-192">Добавьте следующий код в строке справа выше метода `Main` для указания пути к ресурсу:</span><span class="sxs-lookup"><span data-stu-id="a1a31-192">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="a1a31-193">Создайте классы для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="a1a31-193">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="a1a31-194">`ImageData` является классом входных данных изображения и имеет следующие поля <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="a1a31-194">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="a1a31-195">`ImagePath` содержит имя файла изображения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-195">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="a1a31-196">`Label` содержит значение для метки изображения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-196">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="a1a31-197">Добавьте новый класс в свой проект для `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-197">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="a1a31-198">`ImagePrediction` является классом прогноза изображения и имеет следующие поля:</span><span class="sxs-lookup"><span data-stu-id="a1a31-198">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="a1a31-199">`Score` содержит процентное значение достоверности для конкретной классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-199">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="a1a31-200">`PredictedLabelValue` содержит значение для прогнозируемой метки классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-200">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="a1a31-201">Класс `ImagePrediction` используется для прогнозирования после обучения модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-201">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="a1a31-202">Он включает `string` (`ImagePath`) с путем к изображению.</span><span class="sxs-lookup"><span data-stu-id="a1a31-202">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="a1a31-203">`Label` используется для применения и обучения модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-203">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="a1a31-204">`PredictedLabelValue` используется для прогнозирования и оценки.</span><span class="sxs-lookup"><span data-stu-id="a1a31-204">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="a1a31-205">Для оценки применяются входные обучающие данные, прогнозируемые значения и модель.</span><span class="sxs-lookup"><span data-stu-id="a1a31-205">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a1a31-206">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="a1a31-206">Initialize variables in Main</span></span>

1. <span data-ttu-id="a1a31-207">Инициализируйте переменную `mlContext` с использованием нового экземпляра `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-207">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="a1a31-208">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="a1a31-208">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="a1a31-209">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-209">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a1a31-210">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a1a31-210">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="a1a31-211">Создание структуры для параметров модели Inception</span><span class="sxs-lookup"><span data-stu-id="a1a31-211">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="a1a31-212">Модель Inception имеет несколько параметров, которые необходимо передать.</span><span class="sxs-lookup"><span data-stu-id="a1a31-212">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="a1a31-213">Создайте структуру, чтобы сопоставить значения параметров с понятными именами, с помощью следующего кода сразу после метода `Main()`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-213">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="a1a31-214">Создание служебного метода для отображения данных</span><span class="sxs-lookup"><span data-stu-id="a1a31-214">Create a display utility method</span></span>

<span data-ttu-id="a1a31-215">Поскольку вы будете отображать данные изображения и связанные прогнозы несколько раз, создайте метод программы отображения для обработки отображения изображений и результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="a1a31-215">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="a1a31-216">Создайте метод `DisplayResults()` сразу после структуры `InceptionSettings` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="a1a31-216">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="a1a31-217">Заполните текст метода `DisplayResults`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-217">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="a1a31-218">Создание служебного метода для TSV-файла</span><span class="sxs-lookup"><span data-stu-id="a1a31-218">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="a1a31-219">Создайте метод `ReadFromTsv()` сразу после метода `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="a1a31-219">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="a1a31-220">Заполните текст метода `ReadFromTsv`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-220">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="a1a31-221">Указанный ниже код анализирует файл `tags.tsv`, после чего добавляет путь к файлу к имени файла изображения для свойства `ImagePath` и загружает его и `Label` в объект `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-221">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="a1a31-222">Создание метода для формирования прогноза</span><span class="sxs-lookup"><span data-stu-id="a1a31-222">Create a method to make a prediction</span></span>

1. <span data-ttu-id="a1a31-223">Создайте метод `ClassifySingleImage()` непосредственно перед методом `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="a1a31-223">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="a1a31-224">Создайте объект `ImageData`, который хранит абсолютный путь и имя файла изображения для одного значения `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-224">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="a1a31-225">Добавьте такой код в следующие строки в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-225">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="a1a31-226">Создайте один прогноз, добавив следующий код в виде следующей строки в методе `ClassifySingleImage`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-226">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="a1a31-227">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) — это удобный API, который создает прогноз на основе одного экземпляра данных.</span><span class="sxs-lookup"><span data-stu-id="a1a31-227">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) class is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="a1a31-228">Чтобы получить прогноз, используйте метод [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A).</span><span class="sxs-lookup"><span data-stu-id="a1a31-228">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span>

1. <span data-ttu-id="a1a31-229">Отобразите результат прогнозирования с помощью следующей строки кода в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-229">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="a1a31-230">Создание конвейера модели ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1a31-230">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="a1a31-231">Конвейер модели ML.NET — это цепочка средств оценки.</span><span class="sxs-lookup"><span data-stu-id="a1a31-231">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="a1a31-232">Обратите внимание, что во время создания конвейера выполнение не происходит.</span><span class="sxs-lookup"><span data-stu-id="a1a31-232">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="a1a31-233">Объекты оценки создаются, но не выполняются.</span><span class="sxs-lookup"><span data-stu-id="a1a31-233">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="a1a31-234">Добавление метода для создания модели</span><span class="sxs-lookup"><span data-stu-id="a1a31-234">Add a method to generate the model</span></span>

    <span data-ttu-id="a1a31-235">Этот метод является основным в учебнике.</span><span class="sxs-lookup"><span data-stu-id="a1a31-235">This method is the heart of the tutorial.</span></span> <span data-ttu-id="a1a31-236">Он создает конвейер для модели и обучает конвейер для создания модели ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1a31-236">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="a1a31-237">Он также оценивает модель по некоторым ранее неиспользуемым тестовым данным.</span><span class="sxs-lookup"><span data-stu-id="a1a31-237">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="a1a31-238">Создайте метод `GenerateModel()` сразу после структуры `InceptionSettings` и непосредственно перед методом `DisplayResults()` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="a1a31-238">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="a1a31-239">Добавьте средства оценки для загрузки, изменения размера и извлечения пикселей из данных изображения:</span><span class="sxs-lookup"><span data-stu-id="a1a31-239">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="a1a31-240">Данные изображения должны обрабатываться в формате, который требуется модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="a1a31-240">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="a1a31-241">В этом случае изображения загружаются в память, преобразуются в соответствующий размер, а пиксели извлекаются в числовой вектор.</span><span class="sxs-lookup"><span data-stu-id="a1a31-241">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="a1a31-242">Добавьте средство оценки, чтобы загрузить модель TensorFlow и оценить ее:</span><span class="sxs-lookup"><span data-stu-id="a1a31-242">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="a1a31-243">Этот этап конвейера загружает модель TensorFlow в память, а затем обрабатывает вектор значений пикселей через сеть модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="a1a31-243">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="a1a31-244">Применение входных данных к модели глубокого обучения и формирование выходных данных с помощью модели называется **оценкой**.</span><span class="sxs-lookup"><span data-stu-id="a1a31-244">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="a1a31-245">При полном использовании модели оценка делает вывод или прогноз.</span><span class="sxs-lookup"><span data-stu-id="a1a31-245">When using the model in its entirety, scoring makes an inference, or prediction.</span></span> 

    <span data-ttu-id="a1a31-246">В этом случае используется вся модель TensorFlow, за исключением последнего слоя, который делает вывод.</span><span class="sxs-lookup"><span data-stu-id="a1a31-246">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="a1a31-247">Выходные данные предпоследнего слоя помечаются как `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-247">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="a1a31-248">Выходные данные этого слоя фактически являются вектором признаков, характеризующих исходные входные изображения.</span><span class="sxs-lookup"><span data-stu-id="a1a31-248">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="a1a31-249">Этот вектор признаков, созданный моделью TensorFlow, будет использоваться в качестве входных данных для алгоритма обучения ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1a31-249">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="a1a31-250">Добавьте средство оценки, чтобы сопоставлять строковые метки в данных для обучения с целочисленными значениями ключа:</span><span class="sxs-lookup"><span data-stu-id="a1a31-250">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="a1a31-251">Для обучающего алгоритма ML.NET, добавляемого далее, метки должны быть в формате `key`, а не в виде произвольных строк.</span><span class="sxs-lookup"><span data-stu-id="a1a31-251">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="a1a31-252">Ключ — это число, которое содержит сопоставление по принципу "один к одному" со строковым значением.</span><span class="sxs-lookup"><span data-stu-id="a1a31-252">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="a1a31-253">Добавьте алгоритм обучения ML.NET:</span><span class="sxs-lookup"><span data-stu-id="a1a31-253">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="a1a31-254">Добавьте средство оценки для преобразования значения прогнозируемого ключа обратно в строку:</span><span class="sxs-lookup"><span data-stu-id="a1a31-254">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="a1a31-255">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="a1a31-255">Train the model</span></span>

1. <span data-ttu-id="a1a31-256">Загрузите данные для обучения с использованием оболочки [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)).</span><span class="sxs-lookup"><span data-stu-id="a1a31-256">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="a1a31-257">Добавьте в следующую строку метода `GenerateModel()` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="a1a31-257">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="a1a31-258">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="a1a31-258">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="a1a31-259">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="a1a31-259">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="a1a31-260">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="a1a31-260">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="a1a31-261">Обучите модель сна основе данных, загруженных ранее:</span><span class="sxs-lookup"><span data-stu-id="a1a31-261">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="a1a31-262">Метод `Fit()` обучает модель путем применения набора данных для обучения к конвейеру.</span><span class="sxs-lookup"><span data-stu-id="a1a31-262">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="a1a31-263">Оценка точности модели</span><span class="sxs-lookup"><span data-stu-id="a1a31-263">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="a1a31-264">Загрузите и преобразуйте проверочные данные, добавив приведенный ниже код в следующую строку метода `GenerateModel`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-264">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="a1a31-265">Есть несколько примеров изображений, которые можно использовать для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-265">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="a1a31-266">Как и данные для обучения, их нужно загрузить в `IDataView`, чтобы модель могла их преобразовать.</span><span class="sxs-lookup"><span data-stu-id="a1a31-266">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>
   
1. <span data-ttu-id="a1a31-267">Добавьте следующий код в метод `GenerateModel()` для оценки модели:</span><span class="sxs-lookup"><span data-stu-id="a1a31-267">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="a1a31-268">Получив прогноз, с помощью метода [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) вы сможете:</span><span class="sxs-lookup"><span data-stu-id="a1a31-268">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="a1a31-269">оценить модель (сравнивает спрогнозированные значения с тестовым набором данных `labels`);</span><span class="sxs-lookup"><span data-stu-id="a1a31-269">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="a1a31-270">получить метрики производительности модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-270">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="a1a31-271">Отобразите метрики точности модели.</span><span class="sxs-lookup"><span data-stu-id="a1a31-271">Display the model accuracy metrics</span></span>

    <span data-ttu-id="a1a31-272">Используйте следующий код для отображения метрик, передачи результатов и выполнения действий по ним:</span><span class="sxs-lookup"><span data-stu-id="a1a31-272">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="a1a31-273">Для классификации изображений выполняется оценка следующих метрик:</span><span class="sxs-lookup"><span data-stu-id="a1a31-273">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="a1a31-274">`Log-loss` — см. раздел [Логарифмические потери](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="a1a31-274">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="a1a31-275">Значение логарифмических потерь должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="a1a31-275">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="a1a31-276">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="a1a31-276">`Per class Log-loss`.</span></span> <span data-ttu-id="a1a31-277">Значение логарифмических потерь для каждого класса должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="a1a31-277">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="a1a31-278">Добавьте следующий код, чтобы возвращать обученную модель:</span><span class="sxs-lookup"><span data-stu-id="a1a31-278">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="a1a31-279">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="a1a31-279">Run the application!</span></span>

1. <span data-ttu-id="a1a31-280">Добавьте вызов `GenerateModel` в метод `Main` после создания класса MLContext:</span><span class="sxs-lookup"><span data-stu-id="a1a31-280">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="a1a31-281">Добавьте такой вызов в метод `ClassifySingleImage()` в виде следующей строки кода в методе `Main`:</span><span class="sxs-lookup"><span data-stu-id="a1a31-281">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="a1a31-282">Запустите консольное приложение (CTRL+F5).</span><span class="sxs-lookup"><span data-stu-id="a1a31-282">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="a1a31-283">Результаты выполнения должны выглядеть примерно так, как указано ниже.</span><span class="sxs-lookup"><span data-stu-id="a1a31-283">Your results should be similar to the following output.</span></span>  <span data-ttu-id="a1a31-284">Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.</span><span class="sxs-lookup"><span data-stu-id="a1a31-284">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

<span data-ttu-id="a1a31-285">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="a1a31-285">Congratulations!</span></span> <span data-ttu-id="a1a31-286">Вы успешно создали модель машинного обучения для классификации изображений, применив передачу обучения в модель `TensorFlow` в ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1a31-286">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="a1a31-287">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="a1a31-287">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="a1a31-288">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="a1a31-288">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a1a31-289">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="a1a31-289">Understand the problem</span></span>
> * <span data-ttu-id="a1a31-290">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="a1a31-290">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="a1a31-291">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="a1a31-291">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="a1a31-292">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="a1a31-292">Classify a test image</span></span>

<span data-ttu-id="a1a31-293">Ознакомьтесь с примерами Машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример классификации изображений.</span><span class="sxs-lookup"><span data-stu-id="a1a31-293">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a1a31-294">Репозиторий GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="a1a31-294">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
