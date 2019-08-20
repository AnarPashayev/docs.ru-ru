---
title: Примеры проектирования бессерверных приложений. бессерверные приложения
description: Узнайте о различных сценариях, поддерживаемых бессерверными архитектурами, от планирования и обработки событий до триггеров файлов и потокового процесса.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 096dce6ef23bde5ef9c6ca65769f4dcc7e08a904
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577197"
---
# <a name="serverless-design-examples"></a>Примеры бессерверного проектирования

Существует множество шаблонов разработки, которые существуют для бессерверных. В этом разделе записываются некоторые распространенные сценарии, использующие бессерверные. Все приведенные примеры являются фундаментальным сочетанием триггера событий и бизнес-логики.

## <a name="scheduling"></a>Создается

Планирование задач — это общая функция. На следующей диаграмме показана устаревшая база данных, для которой не предусмотрены соответствующие проверки целостности. База данных должна быть периодически очищена. Бессерверная функция находит недопустимые данные и очищает их. Триггер — это таймер, который запускает код по расписанию.

![Бессерверное планирование](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Разделение команд и запросов (CQRS)

Разделение команд и запросов (CQRS) — это шаблон, предоставляющий различные интерфейсы для чтения (или запроса) данных и операций, изменяющих данные. В ней рассматриваются некоторые распространенные проблемы. В традиционном создании систем на основе чтения с обновлением (CRUD) конфликты могут возникать из большого объема операций чтения и записи в одном хранилище данных. Блокировка может часто происходить и значительно замедлить чтение. Часто данные представляются в составе нескольких объектов домена, и операции чтения должны объединять данные из разных сущностей.

При использовании CQRS для чтения может потребоваться специальная «плоская» сущность, которая моделирует данные так, как она используется. Чтение обрабатывается не так, как оно хранится. Например, несмотря на то, что база данных может хранить контакт как запись заголовка с дочерней записью адреса, чтение может затрагивать сущность со свойствами заголовка и адреса. Создание модели чтения имеет множество методов. Он может быть материализованным из представлений. Операции обновления могут быть инкапсулированы в виде изолированных событий, которые затем активируют обновления для двух разных моделей. Для чтения и записи существуют отдельные модели.

![Пример CQRS](./media/cqrs-example.png)

Серверная модель может соответствовать шаблону CQRS путем предоставления разделенных конечных точек. Одна бессерверная функция поддерживает запросы или операции чтения, а другая функция или набор функций, бессерверных, обрабатывает операции обновления. Бессерверная функция может также отвечать за поддержание актуальности модели чтения и может быть активирована [веб-каналом изменений](https://docs.microsoft.com/azure/cosmos-db/change-feed)базы данных. Интерфейсная разработка упрощает подключение к необходимым конечным точкам. Обработка событий обрабатывается в серверной части. Эта модель также хорошо масштабируется для больших проектов, так как различные команды могут работать с разными операциями.

## <a name="event-based-processing"></a>Обработка на основе событий

В системах на основе сообщений события часто собираются в очереди или в разделах, посвященных издателю и подписчику. Эти события могут активировать бессерверные функции для выполнения части бизнес-логики. Примером обработки на основе событий являются системы, в которых используется источник событий. Создается событие, помечающая задачу как завершенную. Функция, бессерверная, активируемая событием, обновляет соответствующий документ базы данных. Вторая функция, бессерверная, может использовать событие для обновления модели чтения для системы. Служба " [Сетка событий Azure](https://docs.microsoft.com/azure/event-grid/overview) " предоставляет способ интеграции событий с функциями в качестве подписчиков.

> События представляют собой информационные сообщения. Дополнительные сведения см. в разделе [шаблон источников событий](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Триггеры и преобразования файлов

Извлечение, преобразование и загрузка (ETL) — это обычная бизнес-функция. Бессерверное решение является отличным решением для ETL, так как позволяет запускать код как часть конвейера. Отдельные компоненты кода могут обращаться к различным аспектам. Одна бессерверная функция может скачать файл, другой применяет преобразование, а другая загружает данные. Код можно тестировать и развертывать независимо, что упрощает обслуживание и масштабирование по мере необходимости.

![Несерверные триггеры и преобразования файлов](./media/serverless-file-triggers.png)

На схеме "Холодное хранилище" представлены данные, которые анализируются в [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Все проблемы, обнаруженные в потоке данных, активируют функцию Azure для устранения аномалий.

## <a name="asynchronous-background-processing-and-messaging"></a>Асинхронная фоновая обработка и обмен сообщениями

Асинхронный обмен сообщениями и фоновая обработка позволяют приложениям запускать процессы без ожидания. Примером асинхронной обработки является приложение для OCR. Изображение отправляется и помещается в очередь для обработки. Сканирование образа для извлечения текста может занять некоторое время, после чего отправляется уведомление. В этом сценарии бессерверные операции могут выполнять как вызов, так и результат.

## <a name="web-apps-and-apis"></a>Веб-приложения и API

Популярным сценарием для бессерверных приложений являются N-уровневые приложения, чаще всего те, где слой пользовательского интерфейса является веб-приложением. Популярность одностраничных приложений (SPA) суржед недавно. Приложения SPA отображают одну страницу, затем полагаются на вызовы API и возвращенные данные для динамического отображения нового пользовательского интерфейса без перезагрузки полной страницы. При отрисовке на стороне клиента обеспечивается гораздо быстрее и более быстрое реагирование приложения для конечного пользователя.

Бессерверные конечные точки, активируемые HTTP-вызовами, можно использовать для обработки запросов API. Например, компания служб AD может вызвать бессерверную функцию с данными профиля пользователя, чтобы запросить пользовательское объявление. Бессерверная функция возвращает пользовательский баннер, а веб-страница визуализирует ее.

![Бессерверный веб-API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Конвейер данных

Для упрощения конвейера данных можно использовать бессерверные функции. В этом примере файл запускает функцию для преобразования данных в CSV-файл в строки данных в таблице. Организованная таблица позволяет Power BI панели мониторинга для отображения анализа конечному пользователю.

![Конвейер бессерверных данных](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Потоковая обработка

Устройства и датчики часто создают потоки данных, которые должны обрабатываться в режиме реального времени. Существует ряд технологий, которые могут записывать сообщения и потоки из концентраторов [событий](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) и [центра Интернета вещей](https://docs.microsoft.com/azure/iot-hub) в [служебную шину](https://docs.microsoft.com/azure/service-bus). Независимо от транспорта, бессерверный процесс является идеальным механизмом обработки сообщений и потоков данных по мере их появления. Без сервера можно быстро масштабироваться в соответствии с потребностями больших объемов данных. Несерверный код может применять бизнес-логику для анализа данных и вывода в структурированном формате для действий и аналитики.

![Обработка бессерверного потока](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Шлюз API

Шлюз API обеспечивает единую точку входа для клиентов, а затем направляет запросы к серверным службам через интеллектуальный маршрут. Очень удобно управлять большими наборами служб. Он также может управлять версиями и упростить разработку, просто подключив клиентов к разнородным средам. Бессерверные решения могут работать с внутренним масштабированием отдельных микрослужб, в то же время предоставляя один внешний интерфейс через шлюз API.

![Шлюз API бессерверных интерфейсов](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Рекомендуемые ресурсы

* [Сетка событий Azure](https://docs.microsoft.com/azure/event-grid/overview)
* [Центр Интернета вещей Azure](https://docs.microsoft.com/azure/iot-hub)
* [Распределенное управление данными: проблемы и решения](../microservices/architect-microservice-container-applications/distributed-data-management.md)
* [Проектирование микрослужб: определение границ микрослужб](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Центры событий](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Шаблон источников событий](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Реализация шаблона размыкателя цепи](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [Центр Интернета вещей](https://docs.microsoft.com/azure/iot-hub)
* [Служебная шина](https://docs.microsoft.com/azure/service-bus)
* [Работа с поддержкой веб-канала изменений в Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Назад](serverless-architecture-considerations.md)
>[Вперед](azure-serverless-platform.md)