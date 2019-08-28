---
title: Отладка приложения .NET для Apache Spark в Windows
description: Узнайте, как отлаживать приложения .NET для Apache Spark в Windows.
ms.date: 08/15/2019
ms.topic: how-to
ms.custom: mvc
ms.openlocfilehash: 08142bd45c475ddd131053213ebdea5f843fa736
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667672"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Отладка приложения .NET для Apache Spark

В этом практическом руководстве приведены команды, которые необходимы для отладки приложения .NET для Apache Spark и кода Scala в Windows.

## <a name="debug-your-application"></a>Отладка приложения

Откройте новое окно командной строки и выполните следующую команду:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

При выполнении команды выводятся следующие выходные данные:

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

В этом режиме отладки `DotnetRunner` не запускает приложение .NET, но ожидает его подключения. Не закрывайте окно командной строки.

Теперь можно запустить приложение .NET с любым отладчиком.

## <a name="debug-scala-code"></a>Отладка кода Scala

Если необходимо выполнить отладку кода на стороне Scala, например `DotnetRunner` или `DotnetBackendHandler`, выполните следующую команду:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

После выполнения команды подключите отладчик к выполняющемуся процессу с помощью [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Следующие шаги

* [Начало работы с .NET для Apache Spark](../tutorials/get-started.md)
* [Развертывание приложения .NET для Apache Spark в Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Развертывание приложения .NET для Apache Spark в Databricks](../tutorials/databricks-deployment.md)
* [Развертывание приложения .NET для Apache Spark в Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)