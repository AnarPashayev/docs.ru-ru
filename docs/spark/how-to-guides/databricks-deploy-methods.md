---
title: Отправка задания .NET для Apache Spark в Databricks
description: Узнайте, как отправить задание .NET для Apache Spark в Databricks с помощью spark-submit и действия "Указание файла JAR".
ms.date: 05/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: a158110854f80921740954403a8fd51b30cbcb12
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379651"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Отправка задания .NET для Apache Spark в Databricks

Вы можете запустить .NET для заданий Apache Spark в кластерах Databricks, но это не будет доступным готовым решением. Есть два способа развертывания задания .NET для Apache Spark в Databricks: с помощью команды `spark-submit` и действия "Указание файла JAR".

## <a name="deploy-using-spark-submit"></a>Развертывание с помощью spark-submit

Для отправки заданий .NET для Apache Spark в Databricks можно использовать команду [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html). `spark-submit` разрешает отправку только в кластер, который создается по требованию.

1. Перейдите в рабочую область Databricks и создайте задание. Выберите название задания, а затем нажмите **Настройка spark-submit**. Вставьте следующие параметры в конфигурацию задания и щелкните **Подтвердить**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Обновите содержимое указанного выше параметра с учетом конкретных файлов и конфигурации. Например, укажите версию файла JAR Microsoft.Spark, который вы отправили в DBFS, и используйте соответствующее имя приложения и ZIP-файла опубликованного приложения.

2. Перейдите к своему заданию и выберите **Изменить**, чтобы настроить кластер задания. Задайте версию Databricks Runtime в зависимости от версии Apache Spark, которую вы хотите использовать в развертывании. Затем щелкните **Дополнительные параметры > Скрипты инициализации** и задайте значение `dbfs:/spark-dotnet/db-init.sh` для параметра пути к скрипту инициализации. Выберите **Подтвердить**, чтобы подтвердить параметры кластера.

3. Перейдите к своему заданию и выберите **Запустить сейчас**, чтобы запустить задание в только что настроенном кластере Spark. Создание кластера для задания может занять несколько минут. После этого в кластер будет отправлено задание. Чтобы просмотреть выходные данные, выберите **Кластеры** в меню слева в рабочей области Databricks, а затем щелкните **Журналы драйверов**.

## <a name="deploy-using-set-jar"></a>Развертывание с помощью действия "Указание файла JAR"

Кроме того, для отправки заданий .NET для Apache Spark в Databricks можно использовать действия [Указание файла JAR](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) в рабочей области Databricks. Действие *Указание файла JAR* позволяет отправить задание в существующий активный кластер.

### <a name="one-time-setup"></a>Однократная настройка

1. Перейдите в кластер Databricks и в меню слева выберите **Задания**, а затем **Указание файла JAR**.

2. Отправьте соответствующий файл `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.

3. Измените следующие параметры, чтобы вместо `<your-app-name>` указать правильное имя опубликованного исполняемого файла.

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Настройте для кластера ссылку на существующий кластер, для которого вы уже настроили скрипт инициализации.

### <a name="publish-and-run-your-app"></a>Публикация и запуск приложения

1. Убедитесь, что приложение опубликовано, а код приложения не использует `SparkSession.Stop()`.

2. Чтобы передать приложение в кластер Databricks, используйте [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli). Например, следующая команда отправляет опубликованное приложение в ваш кластер.

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Если в приложении есть определяемые пользователем функции, сборки приложения (например, библиотеки DLL, содержащие определяемые пользователем функции и их зависимости) необходимо поместить в рабочий каталог каждой роли *Microsoft.Spark.Worker*.

    Отправка сборок приложения в кластер Databricks.

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Раскомментируйте и измените раздел зависимостей приложения в файле [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh), указав путь к зависимостям приложения. После этого отправьте обновленный файл *db-init.sh* в кластер:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Чтобы запустить задание, последовательно выберите **Кластер Databricks > Задания > [имя_задания] > Запустить сейчас**.

## <a name="next-steps"></a>Следующие шаги

* [Начало работы с .NET для Apache Spark](../tutorials/get-started.md)
* [Развертывание приложения .NET для Apache Spark в Databricks](../tutorials/databricks-deployment.md)
* [Документация по Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
