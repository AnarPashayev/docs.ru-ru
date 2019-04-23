---
title: Разработка и развертывание служб WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 8b709de728726b7695b987c48574d2a70a1bc27e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481383"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Разработка и развертывание службы WCF Data Services

Этот раздел содержит сведения о разработке и развертывании службы данных WCF. Дополнительные сведения о службах WCF Data Services, см. в разделе [Приступая к работе](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) и [Обзор](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Разработка служб WCF Data Services

При использовании служб данных WCF для создания службы данных, которая поддерживает [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], во время разработки необходимо выполнить следующие основные задачи:

1. **Определение модели данных**

     Службы данных WCF поддерживают разнообразные поставщики служб данных, которые позволяют определить модель данных на основе данных из различных источников данных из реляционных баз данных в типы данных с поздним связыванием. Дополнительные сведения см. в разделе [поставщики служб данных](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

2. **Создание службы данных**

     Самая базовая служба данных предоставляет класс, производный от класса <xref:System.Data.Services.DataService%601> , с типом `T` , представляющим имя контейнера сущностей, квалифицированное пространством имен. Дополнительные сведения см. в разделе [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3. **Настройка службы данных**

     По умолчанию службы данных WCF запрещает доступ к ресурсам, предоставляемым контейнером сущностей. <xref:System.Data.Services.DataServiceConfiguration> Интерфейс позволяет настроить доступ к ресурсам и операциям службы, задать поддерживаемую версию OData и определить другие особенности поведения службы, такие как использование пакетирования или максимальное количество сущностей, которые могут быть возвращены в одном ответе веб-канале. Дополнительные сведения см. в разделе [Настройка службы данных](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

В этом разделе рассматриваются главным образом разработку и развертывание служб данных с помощью Visual Studio. Сведения о гибких возможностях службами данных WCF для предоставления данных в качестве веб-каналов OData, см. в разделе [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Выберите веб-сервера разработки

При разработке службы данных WCF в качестве [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] приложения или [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] веб-сайта с помощью Visual Studio 2015, вы увидите список веб-серверов, на котором работает служба данных во время разработки. Следующие веб-серверы интеграции с Visual Studio, чтобы упростить тестирование и отладку служб данных на локальном компьютере.

1. **Локальный сервер служб IIS**

     При создании службы данных, которая является приложением [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] или веб-узлом [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , работающим на базе служб IIS, рекомендуется разрабатывать и тестировать службу данных с помощью IIS на локальном компьютере. Запуск службы данных в IIS упрощает трассировку HTTP-запросов во время отладки. Это также позволяет заранее определить необходимые права, которые требуются службам IIS для доступа к файлам, базам данных и другим ресурсам для службы данных. Чтобы запустить службу данных в службах IIS, необходимо проверить наличие, что службы IIS и Windows Communication Foundation (WCF) установлены и настроены правильно и предоставить доступ к учетным записям служб IIS в файловой системе и баз данных. Дополнительные сведения см. в разделе [Как Разработке службы данных WCF, выполняющегося на сервере IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Необходимо запустить Visual Studio с правами администратора, чтобы позволить среде разработки настроить локальный сервер IIS.

2. **Сервер разработки Visual Studio**

     Visual Studio включает в себя встроенный веб-сервер Visual Studio Development Server, который является сервером по умолчанию для [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] проектов. Этот веб-сервер предназначен для запуска проектов [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] на локальном компьютере во время разработки. [Краткое руководство по службам данных WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) показано, как создать службу данных, которая выполняется в Visual Studio Development Server.

     Вы должны помнить о следующих ограничениях при разработке службы данных с помощью Visual Studio Development Server:

    - Доступ к этому серверу возможен только с локального компьютера.

    - Этот сервер прослушивает `localhost` и указанный порт, отличный от порта 80, который по умолчанию настроен для HTTP-сообщений. Дополнительные сведения см. в разделе [Веб-серверы в Visual Studio для веб-проектов ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - На этом сервере служба данных работает в контексте текущей учетной записи пользователя. Например при запуске пользователя уровня администратора служба данных, работающая в Visual Studio Development Server будет иметь права уровня администратора. Это может обеспечить службе данных доступ к ресурсам, для которых у нее не будет прав после развертывания на сервере служб IIS.

    - На этом сервере отсутствуют дополнительные возможности служб IIS, такие как проверка подлинности.

    - Этот сервер не может обрабатывать фрагментированный HTTP-потоков, которые отправляются будет по умолчанию с помощью клиента службы данных WCF, при доступе к больших объемов двоичных данных из службы данных. Дополнительные сведения см. в разделе [потокового поставщика](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

    - Этого сервера есть проблемы с обработкой периода (`.`) символов в URL-адрес, несмотря на то, что этот символ поддерживается службами данных WCF в значениях ключа.

    > [!TIP]
    > Несмотря на то, что Visual Studio Development Server можно использовать для тестирования служб данных во время разработки, вам следует повторно их протестировать после развертывания на веб-сервере, где работают службы IIS.

3. **Среда разработки Microsoft Azure**

     Windows Azure Tools для Visual Studio включает набор интегрированных средств для разработки служб Windows Azure в Visual Studio. С помощью этих средств можно разрабатывать службы данных, которые могут развертываться на Microsoft Azure, а также тестировать службу данных на локальном компьютере перед развертыванием. Эти средства можно используйте, при использовании Visual Studio разработке службы данных, которая работает на платформе Windows Azure. Вы можете скачать инструменты Windows Azure для Visual Studio из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?LinkID=201848). Дополнительные сведения о разработке службы данных для запуска в Windows Azure см. в публикации [Deploying an OData Service в Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="development-tips"></a>Советы по разработке

При разработке службы данных необходимо учитывать следующее:

- Определите требования по безопасности к службе данных, если планируется проверять подлинность пользователей или ограничивать доступ определенным пользователям. Дополнительные сведения см. в разделе [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

- Программа проверки HTTP может быть очень полезной при развертывании службы данных, позволяя проверять содержимое сообщений запросов и ответов. Любой планировщик сетевых пакетов, способный отображать необработанные пакеты, можно использовать для проверки HTTP-запросов к службе данных и ответов от нее.

- При отладке службы данных, можно получить дополнительные сведения об ошибке из службы данных, чем во время простой операции. Дополнительные сведения об ошибках можно получить из службы данных, установив свойство <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> в <xref:System.Data.Services.DataServiceConfiguration> значение `true` , а свойство <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> атрибута <xref:System.ServiceModel.Description.ServiceDebugBehavior> класса службы данных — в значение `true`. Дополнительные сведения см. в публикации [Debugging WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=201868). Можно также включить трассировку в WCF для просмотра исключений, созданных в уровень обмена сообщениями HTTP. Для получения дополнительной информации см. [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).

- Службы данных обычно разрабатывается как [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] проект приложения, но вы также можете создать службу данных как [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] проекта веб-сайта в Visual Studio. Сведения о различиях между двумя типами проектов см. в разделе [проектами веб-приложения веб-сайта в Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- При создании службы данных с помощью **Добавление нового элемента** диалоговое окно в Visual Studio, службы данных управляется [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] в службах IIS. Несмотря на то что [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] и IIS используются для размещения службы данных по умолчанию, поддерживаются и другие варианты размещения. Дополнительные сведения см. в разделе [размещение служб данных](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Развертывания служб данных WCF

Службы данных WCF обеспечивают гибкость в выборе процесса, в котором будет размещаться служба данных. Visual Studio можно использовать для развертывания службы данных на следующих платформах:

- **Веб-сервер, размещенный в службах IIS**

    Если служба данных разрабатывается как проект [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , то его можно развернуть на веб-сервере IIS с помощью стандартной процедуры развертывания [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] .  Visual Studio предоставляет следующие технологии развертывания для [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], в зависимости от типа объекта [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , на котором размещена служба данных, при развертывании проекта.

  - **Технологии развертывания для веб-приложений ASP.NET**

    - [Практическое руководство. Создать пакет веб-развертывания в Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Практическое руководство. Развертывание веб-публикации проекта с помощью одним щелчком в Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Технологии развертывания для веб-узлов ASP.NET**

    - [Практическое руководство. Скопируйте файлы веб-сайта с помощью средства копирования веб-сайта](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Практическое руководство. Публикация веб-сайтов](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Пошаговое руководство: Развертывание веб-приложения ASP.NET с помощью XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Дополнительные сведения о вариантах развертывания для [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] приложения, см. в разделе [Обзор веб-развертывания для Visual Studio и ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Прежде чем пытаться выполнить развертывание службы данных в IIS, обязательно протестируйте развертывание на веб-сервере, где работают службы IIS. Дополнительные сведения см. в разделе [Как Разработке службы данных WCF, выполняющегося на сервере IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Microsoft Azure**

     Службы данных можно развернуть в Windows Azure с помощью Windows Azure Tools для Visual Studio. Вы можете скачать инструменты Windows Azure для Visual Studio из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?LinkID=201848). Дополнительные сведения о развертывании службы данных в Windows Azure см. в публикации [Deploying an OData Service в Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="deployment-considerations"></a>Требования к развертыванию

При разработке службы данных необходимо учитывать следующее:

- При развертывании службы данных, использующей поставщика [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] для доступа к базе данных SQL Server, можно также распространить структуры данных, данные или и то и другое. Visual Studio может автоматически создавать скрипты (SQL-файлы) для этого в целевой базе данных, и эти скрипты могут быть включены в пакет развертывания веб- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] приложения. Дополнительные сведения см. в разделе [Как Развертывание базы данных для проекта веб-приложения](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Для [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] веб-сайта, это можно сделать помощью **мастер публикации баз данных** в Visual Studio. Дополнительные сведения см. в разделе [публикации базы данных SQL](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Поскольку службы данных WCF включает в себя базовую реализацию WCF, можно использовать Windows Server AppFabric для наблюдения за службой данных, развернутой в службах IIS, под управлением Windows Server. Дополнительные сведения об использовании Windows Server AppFabric для наблюдения за службами данных см. в публикации [Tracking WCF Data Services with Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=202005).

## <a name="see-also"></a>См. также

- [Размещение служб данных](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
- [Защита служб WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Определение служб данных WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
