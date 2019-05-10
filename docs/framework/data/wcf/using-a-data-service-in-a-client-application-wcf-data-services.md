---
title: Использование служб данных в клиентском приложении (службы данных WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: fc14b6a2b3782ae7ed3d26f9878646f004504d1c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660560"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Использование служб данных в клиентском приложении (службы данных WCF)
Можно получить доступ к службе, предоставляющей [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] веб-канала, указав URI в веб-браузер. URI предоставляет адрес ресурса, и сообщения запроса отправляются по этим адресам для доступа или изменения базовых данных, представляемых ресурсом. Браузер формирует команду HTTP GET и возвращает запрошенный ресурс в виде канала [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Дополнительные сведения см. в разделе [доступа к службе из веб-браузер](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Хотя веб-браузер может быть полезен для проверки того, что служба [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] возвращает ожидаемые данные, доступ к производственным службам [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], позволяющим создавать, обновлять и удалять данные, обычно осуществляется из кода приложения или языков создания скриптов на веб-странице. В этом разделе представлен обзор того, как получить доступ к [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-каналов из клиентского приложения.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Доступ и изменение данных с помощью семантики REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] помогает осуществить взаимодействие между службами, которые предоставляют [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-каналы и приложения, обрабатывающие [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-каналов. Приложения обращаются и изменяют данные в [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-службу на основе, отправляя сообщения запросов конкретного действия HTTP вместе с URI, Адресующим ресурс сущности, над которой должно быть выполнено действие. Если необходимо передать данные сущности, они передаются в специально закодированных полезных данных в тексте сообщения.  
  
### <a name="http-actions"></a>Действия HTTP  
 Службы [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] поддерживают следующие действия HTTP для создания, чтения, обновления и удаления данных сущностей, представленных адресуемыми ресурсами.  
  
- **HTTP GET** -это действие по умолчанию при доступе к ресурсу из браузера. Сообщение запроса не содержит полезных данных, а возвращается метод ответа с полезными данными, содержащими запрошенные данные.  
  
- **HTTP POST** -вставляет данные новой сущности в переданный ресурс. Вставляемые данные передаются в виде полезных данных сообщения запроса. Полезные данные ответного сообщения содержат данные созданной сущности. К ним относятся все ключевые значения, формируемые автоматически. Заголовок содержит также URI, адресующий ресурс новой сущности.  
  
- **HTTP DELETE** -удаляет данные сущности, представленной указанным ресурсом. Полезные данные в сообщениях запроса и ответа отсутствуют.  
  
- **HTTP PUT** — заменяет имеющиеся данные сущности в запрошенном ресурсе новыми данными, передаваемыми в полезных данных сообщения запроса.  
  
- **HTTP MERGE** — в выполнения удаления, а затем вставки в источнике данных только для изменения данных сущности, связи с неэффективностью [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] представляют новое действие HTTP MERGE. Полезные данные сообщения запроса содержат свойства, которые необходимо изменить в адресуемом ресурсе сущности. Поскольку метод HTTP MERGE не определен в спецификации HTTP, ему может потребоваться дополнительная обработка для отправки запроса HTTP MERGE через серверы, не поддерживающие службы [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 Дополнительные сведения см. в разделе [OData: Операции](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Форматы представления информации  
 Для запросов HTTP PUT, HTTP POST или HTTP MERGE полезные данные сообщения запроса содержат данные сущности, отправляемые службе данных. Содержимое полезных данных зависит от формата данных сообщения. Ответы HTTP на все действия, кроме DELETE, также содержат полезные данные. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] поддерживает следующие форматы полезных данных для доступа и изменения данных в службе:  
  
- **Atom** — Кодировка сообщений на основе XML, определяемые [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] как расширение протокола публикации Atom (AtomPub) для обмена данными по протоколу HTTP для веб-каналов, подкастов, вики и функций Интернета на основе XML. Дополнительные сведения см. в разделе [OData: Формат Atom](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
- **JSON** -JavaScript Object Notation (JSON) — это формат обмена небольшого количества данных, который основан на подмножестве языка JavaScript. Дополнительные сведения см. в разделе [OData: Формат JSON](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Формат сообщения полезных данных запрашивается в заголовке HTTP-запроса. Дополнительные сведения см. в разделе [OData: Операции](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Доступ и изменения данных с помощью клиентских библиотек  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] включает в себя клиентские библиотеки, которые позволяют упростить использование [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-канал из .NET Framework и приложений клиента на основе Silverlight. Эти библиотеки упрощают отправку и получение сообщений HTTP. Кроме того, они преобразуют полезные данные сообщений в объекты CLR, представляющие данные сущностей. Клиентские библиотеки содержат два базовых класса: <xref:System.Data.Services.Client.DataServiceContext> и <xref:System.Data.Services.Client.DataServiceQuery%601>. Эти классы позволяют отправлять запросы к службе данных и работать с возвращенными данными сущностей как с объектами CLR. Дополнительные сведения см. в разделе [клиентскую библиотеку WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) и [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Можно использовать **Add Service Reference** диалоговое окно в Visual Studio для добавления ссылки на службу данных. Эта программа запрашивает метаданные службы у упомянутой службы данных и формирует контекст <xref:System.Data.Services.Client.DataServiceContext>, который представляет службу данных, а также клиентские классы службы данных, которые представляют сущности. Дополнительные сведения см. в разделе [Создание клиентской библиотеки службы данных](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Существуют программные библиотеки, которое можно использовать для использования [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] веб-канала в другие виды клиентских приложений. Дополнительные сведения см. в разделе [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>См. также

- [Доступ к ресурсам служб данных](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [Краткое руководство](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
