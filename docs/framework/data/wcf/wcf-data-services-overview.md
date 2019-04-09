---
title: Общие сведения о службах данных WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: ca52b725f5fad4b591b95bf6a6dd778c7a72d235
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202057"
---
# <a name="wcf-data-services-overview"></a>Общие сведения о службах данных WCF
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] обеспечивает создание и использование служб данных в Интернете или интрасети с помощью [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] позволяет предоставлять данные в качестве ресурсов, которые можно обращаться по URI. Это позволяет обращаться к данным и изменять их с использованием семантики REST, в частности стандартных команд HTTP, таких как GET, PUT, POST и DELETE. В этом разделе приведены общие сведения о шаблонах и методиках, определенных службами [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], а также о функциях, предоставляемых службами [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] для использования [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] в приложениях на базе .NET Framework.  
  
## <a name="address-data-as-resources"></a>Адресация данных в виде ресурсов  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] предоставляет доступ к данным как к ресурсам, можно обращаться по URI. Пути к ресурсам формируются на основе соглашений о связи сущностей, описанных в модели EDM. Сущности в этой модели представляют операционные единицы данных в домене приложения, таких как клиенты, заказы, элементы и продукты. Дополнительные сведения см. в разделе [модели EDM](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Адресация ресурсов сущностей в службах [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] осуществляется в виде набора сущностей, содержащего экземпляры типов сущностей. Например, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` возвращает все заказы из `Northwind` службы данных, которые связаны с клиентом `CustomerID` значение `ALFKI.`  
  
 Выражения запросов позволяют выполнять традиционные операции с запросами к ресурсам, такие как фильтрация, сортировка и подкачка страниц. Например, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` фильтрует ресурсы, возвращая только заказы со стоимостью транспортировки, превышающей 50 долларов. Дополнительные сведения см. в разделе [доступ к ресурсам службы данных](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Доступ к данным с возможностью взаимодействия  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] основана на стандартных протоколах Интернета, для обеспечения взаимодействия с приложениями, не использующими .NET Framework службы данных. Так, как можно использовать стандартный URI для адресации данных, приложение может получить доступ и изменение данных с помощью семантики передачи репрезентативного состояния (REST), в частности стандартных HTTP-команд GET, PUT, POST и DELETE. Это позволяет обращаться к службам из любого клиента, поддерживающего синтаксический анализ и доступ к данным, передаваемым по стандартным протоколам HTTP.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Определяет набор расширений для протокола публикации Atom (AtomPub). Они поддерживают запросы и ответы HTTP в нескольких форматах данных, что позволяет использовать различные клиентские приложения и платформы. Канал [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] может представлять данные в формате Atom, формате нотации объектов JavaScript (JSON) и в виде простого XML. Atom является форматом по умолчанию. Формат канала указывается в заголовке HTTP-запроса. Дополнительные сведения см. в разделе [OData: Формат Atom](https://go.microsoft.com/fwlink/?LinkID=185794) и [OData: Формат JSON](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 При публикации данных в виде [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-канала, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] полагается на другие имеющиеся службы Интернета для таких операций, как кэширование и проверка подлинности. Чтобы выполнить это, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] интегрируется с существующими ведущими приложениями и службами, например ASP.NET, Windows Communication Foundation (WCF) и Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Независимость хранилища  
 Хотя ресурсы адресуются на основе модели связей сущностей, службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] предоставляют каналы [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] независимо от базового источника данных. После того как службы [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] принимают запрос HTTP к ресурсу, идентифицируемому URI, запрос десериализуется и его представление передается поставщику [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Поставщик преобразует запрос в формат, зависящий от источника данных, и выполняет его на базовом источнике данных. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] независимость хранилища достигается путем отделения концептуальной модели адресации ресурсов [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] от конкретной схемы базового источника данных.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] интегрируется с ADO.NET Entity Framework, позволяя создавать службы данных, предоставляющие реляционные данные. Для создания модели данных, содержащей адресуемые ресурсы в виде сущностей и в то же время определяющей сопоставление между этой моделью и таблицами нижележащей базы данных, можно использовать программы для работы с моделью EDM. Дополнительные сведения см. в разделе [поставщика Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] также позволяет создавать службы данных, предоставляющие любые структуры данных, которые возвращают реализацию <xref:System.Linq.IQueryable%601> интерфейс. Это позволяет создавать службы данных, предоставляющие данные из типов .NET Framework. Для поддержки операций создания, обновления и удаления должен быть также реализован интерфейс <xref:System.Data.Services.IUpdatable>. Дополнительные сведения см. в разделе [поставщик отражения](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Дополнительные сведения о том, как [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] интегрируется с этими поставщиками данных см. в разделе Архитектурная схема далее в этом разделе.  
  
## <a name="custom-business-logic"></a>Пользовательская бизнес-логика  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] упрощает добавление пользовательской бизнес-логики в службе данных с помощью операции и перехватчики службы. Операции службы — это методы, определенные на сервере и адресуемые с помощью URI в том же формате, что и ресурсы данных. Операции службы могут также использовать синтаксис выражений запросов для фильтрации, упорядочения и разбиения на страницы данных, возвращаемых операцией. Например, URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` представляет вызов служебной операции с именем `GetOrdersByCity` для службы данных Northwind, возвращающей заказы клиентов из Лондона, разбитые на страницы и отсортированные по значению `OrderDate`. Дополнительные сведения см. в разделе [операций службы](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Перехватчики позволяют разработчику интегрировать настраиваемую прикладную логику в процесс обработки запросов и ответов службы данных. Перехватчики вызываются при выполнении операции запроса, вставки, обновления или удаления над указанным набором сущностей. При этом перехватчик может изменить данные, применить политику проверки подлинности и даже преждевременно завершить операцию. Методы перехватчика необходимо явно регистрировать для конкретного набора сущностей, предоставляемого службой данных. Дополнительные сведения см. в разделе [перехватчики](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Клиентские библиотеки  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Определяет набор универсальных шаблонов для взаимодействия со службами данных. Это предоставляет возможность создавать повторно используемые компоненты, которые основаны на этих служб, таких как клиентские библиотеки, упрощающие использование служб данных.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] включает в себя клиентские библиотеки платформы .NET Framework и на основе Silverlight клиентскими приложениями. Эти клиентские библиотеки позволяют взаимодействовать со службами данных с помощью объектов .NET Framework. Они также поддерживают запросы на базе объектов и запросы LINQ, загрузку связанных объектов, отслеживание изменений и разрешение идентификаторов. Дополнительные сведения см. в разделе [клиентскую библиотеку служб данных WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 В дополнение к [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] клиентские библиотеки, в составе платформы .NET Framework и Silverlight, существуют другие клиентские библиотеки, позволяющие использовать [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-канала в клиентских приложениях, таких как PHP, AJAX и Java. Дополнительные сведения см. в разделе [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Общие сведения об архитектуре  
 На следующей схеме показана [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] архитектуры для предоставления [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-каналы и их использования в [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-поддержкой клиентских библиотек:  
  
 ![Снимок экрана, показывающий на схеме архитектуры служб данных WCF.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>См. также

- [Службы WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)
- [Начало работы](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Определение служб данных WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Доступ к ресурсам служб данных (службы данных WCF)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Библиотека клиентов служб данных WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Передача состояния представления (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
