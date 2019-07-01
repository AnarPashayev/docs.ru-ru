---
title: Общие сведения о модели программирования WCF Web HTTP
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: d4908eb75324d4316ea615d1a0acc286750752e7
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487718"
---
# <a name="wcf-web-http-programming-model-overview"></a>Общие сведения о модели программирования WCF Web HTTP
Модель программирования WEB HTTP Windows Communication Foundation (WCF) предоставляет основные элементы, необходимые для построения служб WEB HTTP с помощью WCF. Службы WCF WEB HTTP, предназначены для доступа со стороны широкого диапазона возможных клиентов, включая веб-браузеры и имеют следующие уникальные требования:  
  
- **URI и обработка URI** URI играют центральную роль в проектировании служб WEB HTTP. Использует модель программирования WCF WEB HTTP <xref:System.UriTemplate> и <xref:System.UriTemplateTable> классы для предоставления возможностей обработки URI.  
  
- **Поддержка операций GET и POST** службы WEB HTTP используют команду GET для получения данных, а также различные команды вызова для изменения данных и удаленного вызова. Использует модель программирования WCF WEB HTTP <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute> для связывания операций службы с GET и другие команды HTTP, такими как PUT, POST и удаления.  
  
- **Несколько форматов данных** веб службы обрабатывают много типов данных, помимо сообщений SOAP. Использует модель программирования WCF WEB HTTP <xref:System.ServiceModel.WebHttpBinding> и <xref:System.ServiceModel.Description.WebHttpBehavior> для поддержки нескольких форматов данных, включая документы XML, объекты данных JSON и потоки двоичного содержимого, такие как изображения, видеофайлы или обычный текст.  
  
 Модель программирования WCF WEB HTTP расширяет сферу использования WCF для веб-сценариев, включающих службы WEB HTTP, AJAX и JSON и веб-каналы синдикации (ATOM/RSS). Дополнительные сведения о службах AJAX и JSON см. в разделе [интеграция с AJAX и поддержка JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Дополнительные сведения о синдикации, см. в разделе [Общие сведения о синдикации WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Какие-либо дополнительные ограничения на типы данных, которые могут быть возвращены из веб-службы HTTP, отсутствуют. При работе веб-службы HTTP могут быть возвращены любые сериализуемые данные. Операции веб-службы HTTP могут быть вызваны веб-браузером, поэтому предусмотрены ограничения, касающиеся того, какие типы данных могут указываться в URL-адресах. Дополнительные сведения о какие типы поддерживаются по умолчанию см. в разделе **параметры строки запроса UriTemplate и URL-адреса** разделе ниже. Это поведение по умолчанию можно изменить, предоставив собственную реализацию объекта T:System.ServiceModel.Dispatcher.QueryStringConverter, которая определяет, как преобразовывать параметры, заданные в URL-адресе, в фактические типы параметров. Дополнительные сведения см. в разделе <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
>  Службы, написанные с помощью модели программирования WCF WEB HTTP используют сообщения SOAP. Поскольку SOAP не используется, нельзя использовать функции безопасности, предоставляемые платформой WCF. Однако можно использовать безопасность уровня транспорта, разместив службу через HTTPS. Дополнительные сведения о безопасности WCF, см. в разделе [Общие сведения о безопасности](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Установка расширения WebDAV для служб IIS может привести к тому, что веб-службы HTTP будут возвращать ошибку HTTP 405, поскольку расширение WebDAV пытается обрабатывать все запросы PUT. Для решения этой проблемы расширение WebDAV можно удалить либо отключить его для данного веб-узла. Дополнительные сведения см. в разделе [IIS и WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Обработка универсального кода ресурса (URI) с помощью UriTemplate и UriTemplateTable  
 Шаблоны URI предоставляют эффективный синтаксис представления больших наборов URI или схожих по структуре URI. Например, следующий шаблон представляет набор всех трехсегментных URI, начинающихся с "a" и заканчивающихся на "c", независимо от значения промежуточного сегмента: a/{segment}/c.  
  
 Данный шаблон описывает универсальные коды ресурса, подобные следующим:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- и т. д.  
  
 В этом шаблоне запись в фигурных скобках ("{segment}") обозначает переменный сегмент, а не литеральное значение.  
  
 Платформа .NET Framework предусматривает API для работы с шаблонами URI, который называется <xref:System.UriTemplate>. `UriTemplates` позволяет выполнять следующие действия.  
  
- Вы можете вызвать один из `Bind` методы с набором параметров для создания *полностью закрытого URI* соответствующего шаблону. Это означает, что все переменные в шаблоне URI заменяются фактическими значениями.  
  
- Можно вызвать `Match`() с потенциальным URI, который использует шаблон для разбиения потенциального URI на составные части и возвращает словарь, содержащий различные части URI, помеченные в соответствии с переменными в шаблоне.  
  
- `Bind`() и `Match`() являются инверсиями, поэтому можно вызвать `Match`( `Bind`( x ) ) и вернуться к той среде, в которой была начата работа.  
  
 Очень часто (особенно на стороне сервера, где необходимо направить запрос операции службы на основе URI), бывает необходимо отслеживать набор объектов <xref:System.UriTemplate> в структуре данных, которые могут независимо обращаться к каждому из включенных шаблонов. <xref:System.UriTemplateTable> представляет набор шаблонов URI и выбирает самый подходящий заданный набор шаблонов и потенциальный URI. Это не связано с одним конкретным сетевым стеком (входит в WCF), поэтому его можно использовать везде, где необходимо.  
  
 Для связывания операций службы с набором URI, который описывается шаблоном <xref:System.UriTemplate>, модель службы WCF использует шаблон <xref:System.UriTemplateTable> и таблицу шаблонов <xref:System.UriTemplate>. Операция службы связывается с шаблоном <xref:System.UriTemplate> с помощью атрибута <xref:System.ServiceModel.Web.WebGetAttribute> или <xref:System.ServiceModel.Web.WebInvokeAttribute>. Дополнительные сведения о <xref:System.UriTemplate> и <xref:System.UriTemplateTable>, см. в разделе [UriTemplate и UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Атрибуты WebGet и WebInvoke  
 Службы WCF WEB HTTP используют команды извлечения (например HTTP GET), а также различные команды (например HTTP POST, PUT и DELETE) вызова. Модель программирования WCF WEB HTTP позволяет разработчикам службы управлять шаблоном URI и командой, связанной с операциями службы, с помощью атрибутов <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute>. Атрибуты <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute> позволяют управлять привязкой отдельных операций к URI и методам HTTP, связанным с этими URI. Например, добавление атрибутов <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute> продемонстрировано в следующем примере кода.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 Предыдущий код позволяет создавать следующие HTTP-запросы.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 Атрибут <xref:System.ServiceModel.Web.WebInvokeAttribute> по умолчанию имеет значение POST, но его можно использовать и для других команд.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Чтобы просмотреть полный пример службы WCF, которая использует модель программирования WCF WEB HTTP, см. в разделе [как: Создание веб-службы HTTP Basic WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Параметры строки запроса UriTemplate и URL-адреса  
 Веб-службы можно вызвать из веб-браузера, введя URL-адрес, связанный с операцией службы. Эти операции службы могут принимать параметры строки запроса, которые необходимо указывать в URL-адресе в строковом формате. В таблице ниже представлены типы, которые могут передаваться внутри URL-адреса и используемого формата.  
  
|Тип|Формат|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38–3.402823e38 (экспоненциальная запись не требуется)|  
|<xref:System.Double>|-1.79769313486232e308–1.79769313486232e308 (экспоненциальная запись не требуется)|  
|<xref:System.Char>|Любой отдельный знак|  
|<xref:System.Decimal>|Любое десятичное число в стандартной записи (без экспоненты)|  
|<xref:System.Boolean>|True или False (с учетом регистра)|  
|<xref:System.String>|Любая строка (пустая строка не поддерживается, преобразование не производится)|  
|<xref:System.DateTime>|ММ/ДД/ГГГГ<br /><br /> ММ/ДД/ГГГГ ЧЧ: ММ: [AM&AMP;#124;PM]<br /><br /> Месяц, день, год<br /><br /> Месяц, день года чч: мм: [AM&#124;PM]|  
|<xref:System.TimeSpan>|ДД.ЧЧ:ММ:СС,<br /><br /> где ДД = дни, ЧЧ = часы, ММ = минуты, СС = секунды.|  
|<xref:System.Guid>|Например, идентификатор GUID:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|ММ/ДД/ГГГГ ЧЧ:ММ:СС ММ:СС,<br /><br /> где ДД = дни, ЧЧ = часы, ММ = минуты, СС = секунды.|  
|Перечисления|Значение перечисления, которое, например, определяет перечисление, как показано в следующем примере кода.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> В строке запроса можно указать любое отдельное значение перечисления (или соответствующее ему целочисленное значение).|  
|Типы, содержащие `TypeConverterAttribute`, который может преобразовать типы в строковое представление и обратно.|Зависит от преобразователя типов.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Форматы и модель программирования WCF WEB HTTP  
 Модель программирования WCF WEB HTTP содержит новые возможности для работы с несколькими различными форматами данных. На уровне привязки <xref:System.ServiceModel.WebHttpBinding> может считывать и записывать следующие различные типы данных.  
  
- XML  
  
- JSON  
  
- Непрозрачные двоичные потоки  
  
 Это означает, что модель программирования WCF WEB HTTP может обрабатывать любой тип данных, но при этом возможно программирование <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] обеспечивает поддержку данных JSON (AJAX), а также RSS-каналов (включая ATOM и RSS). Дополнительные сведения об этих функциях см. в разделе [WCF Web HTTP форматирование](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[Общие сведения о синдикации WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) и [интеграция с AJAX и поддержка JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Модель программирования WCF WEB HTTP и безопасность  
 Поскольку модель программирования WCF WEB HTTP не поддерживает WS-* протоколы, единственным способом защиты службы WCF WEB HTTP является предоставление доступа к ней по протоколу HTTPS, с помощью протокола SSL. Дополнительные сведения о настройке SSL с IIS 7.0 см. в разделе [реализация SSL-сертификата в IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Устранение неполадок в модели программирования WCF WEB HTTP  
 Когда службы WCF WEB HTTP вызываются с помощью <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> для создания канала, <xref:System.ServiceModel.Description.WebHttpBehavior> использует адрес <xref:System.ServiceModel.EndpointAddress>, заданный в файле конфигурации, даже в случае, когда в <xref:System.ServiceModel.EndpointAddress> передается другой <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>См. также

- [Синдикация WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Объектная модель веб-программирования HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Модель веб-программирования HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
