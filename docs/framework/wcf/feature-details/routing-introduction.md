---
title: Введение в маршрутизацию
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: d0f07d0dd171de428f7d556d84dfda04e35880b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158682"
---
# <a name="routing-introduction"></a>Введение в маршрутизацию
Служба маршрутизации реализует универсальный расширяемый SOAP-посредник, маршрутизирующий сообщения с использованием их содержимого. Эта служба позволяет создавать сложные алгоритмы маршрутизации для реализации сценариев объединения служб, управления версиями, управления приоритетами и многоадресной маршрутизации. Функция обработки ошибок службы маршрутизации позволяет создавать списки резервных конечных точек (сообщения отправляются в резервные конечные точки в случае сбоя при отправке в основную целевую конечную точку).  
  
 Данный раздел предназначен для тех, кто впервые знакомится со службой маршрутизации. В разделе приведены базовые сведения о конфигурации и размещении службы маршрутизации.  
  
## <a name="configuration"></a>Параметр Configuration  
 Служба маршрутизация представляет собой службу WCF, которая обнаруживает одну или несколько конечных точек службы, получающих сообщения от клиентских приложений и перенаправляющих их в одну или несколько целевых конечных точек. Эта служба предоставляет поведение <xref:System.ServiceModel.Routing.RoutingBehavior>, которое применяется к обнаруженным конечным точкам службы. Это поведение используется для настройки различных аспектов работы службы. Для упрощения настройки с помощью файла конфигурации, параметры указываются в **RoutingBehavior**. В сценариях на основе кода, эти параметры указываются как часть <xref:System.ServiceModel.Routing.RoutingConfiguration> объект, который может быть передан **RoutingBehavior**.  
  
 При запуске этого поведения к клиентским конечным точкам добавляется параметр <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, который используется для обработки сообщений SOAP. Данное значение позволяет службе маршрутизации для передачи сообщений в конечные точки, требующие **MessageVersion** чем конечная точка, через которую было получено сообщение. **RoutingBehavior** также регистрирует расширение службы <xref:System.ServiceModel.Routing.RoutingExtension>, который предоставляет точку доступа для изменения конфигурации службы маршрутизации во время выполнения.  
  
 **RoutingConfiguration** класс позволяет согласованным образом настраивать и обновлять конфигурацию службы маршрутизации.  Оно содержит параметры, которые действуют как параметры для службы маршрутизации и используется для настройки **RoutingBehavior** при запуске службы, или передается **RoutingExtension** для изменения маршрутизации конфигурации во время выполнения.  
  
 Логика маршрутизации на основе содержимого определяется путем группирования нескольких объектов <xref:System.ServiceModel.Dispatcher.MessageFilter> в таблицы фильтрации (объекты <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>). Входящие сообщения анализируются с использованием фильтров сообщений, содержащихся в таблице фильтров, а также для каждого **MessageFilter** , соответствующий сообщения, передаваемые для целевой конечной точки. Таблица фильтров, который должен использоваться для маршрутизации сообщений задается с помощью либо **RoutingBehavior** в конфигурации или посредством кода с помощью **RoutingConfiguration** объекта.  
  
### <a name="defining-endpoints"></a>Определение конечных точек  
 Кажется логичным, что начинать настройку нужно с определения используемой логики маршрутизации. Тем не менее, сперва нужно задать форму конечных точек, куда будут перенаправляться сообщения. Служба маршрутизации использует контракты, определяющие форму каналов, которые будут использованы для получения и отправки сообщений. Форма входящего канала должна соответствовать форме исходящего канала.  Если маршрутизация выполняется в точки, использующие форму канала «запрос-ответ», необходимо использовать совместимый контракт для входящих конечных точек (например, <xref:System.ServiceModel.Routing.IRequestReplyRouter>).  
  
 Это означает, что если целевые конечные точки используют контракты с несколькими шаблонами взаимодействия (например со смешением односторонних и двусторонних операций), нельзя создать единую конечную точку службы, которая могла бы принимать и перенаправлять сообщения во все целевые точки. Нужно понять, какие конечные точки имеют совместимые формы, и определить одну или несколько конечных точек службы, предназначенных для получения сообщений, которые будут перенаправлены в целевые конечные точки.  
  
> [!NOTE]
> При работе с контрактами, задействующими несколько шаблонов взаимодействия (например со смешением односторонних и двусторонних операций), правильным решением будет использование в службе маршрутизации дуплексного контракта (например <xref:System.ServiceModel.Routing.IDuplexSessionRouter>). Это значит, что привязка должна быть совместима с дуплексным взаимодействием, однако это неприменимо ко всем сценариям. В сценариях, для которых это неприменимо, может понадобиться разбиение модели взаимодействия на несколько конечных точек либо изменение приложения.  
  
 Дополнительные сведения о контрактах маршрутизации см. в разделе [контракты маршрутизации](routing-contracts.md).  
  
 После определения конечной точки службы можно использовать **RoutingBehavior** для связывания конкретной **RoutingConfiguration** с конечной точкой. При настройке службы маршрутизации с помощью файла конфигурации, **RoutingBehavior** используется для указания фильтра таблицы, содержащей логику маршрутизации, используемый для обработки сообщений, получаемых этой конечной точки. При настройке службы маршрутизации программными средствами можно указать в таблицу фильтров с помощью **RoutingConfiguration**.  
  
 В следующем примере показано, как определять клиентские конечные точки для службы маршрутизации (как с использованием файла конфигурации, так и с помощью программного кода).  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 В этом примере настраивается служба маршрутизации будет единственной конечной точки с адресом `http://localhost:8000/routingservice/router`, который используется для получения сообщений для маршрутизации. Сообщения перенаправляются в конечные точки типа «запрос-ответ», поэтому конечная точка службы использует контракт <xref:System.ServiceModel.Routing.IRequestReplyRouter>. Эта конфигурация также определяет единственную клиентскую конечную точку `http://localhost:8000/servicemodelsample/service` что направляются сообщения. Таблицы фильтров (не показано) с именем «routingTable1» содержит логику маршрутизации, используемый для перенаправления сообщений она связывается с конечной точки службы с помощью **RoutingBehavior** (для файла конфигурации) или  **RoutingConfiguration** (для программной конфигурации).  
  
### <a name="routing-logic"></a>Логика маршрутизации  
 Для определения логики маршрутизации, используемой при перенаправлении сообщений, необходимо указать, какие данные, содержащиеся во входящих сообщениях, будут обрабатываться уникальным образом. Например, если все целевые конечные точки используют одинаковые действия SOAP, то значение действия внутри сообщения не может указывать, в какую конкретную точку должно перенаправляться сообщение. Если нужно перенаправить сообщения в одну конкретную точку, необходимо задать соответствующую фильтрацию (по данным, которые уникальным образом определяют целевую конечную точку).  
  
 Служба маршрутизации предоставляет несколько **MessageFilter** реализаций, которые проверяют определенных значений в сообщении, например адрес, действия, имя конечной точки или даже запрос XPath. Если ни одна из этих реализаций не соответствует вашим потребностям, можно создать пользовательскую **MessageFilter** реализации. Дополнительные сведения о фильтрах сообщений и сравнение различных реализаций, используемых службой маршрутизации, см. в разделе [фильтры сообщений](message-filters.md) и [Выбор фильтра](choosing-a-filter.md).  
  
 Множество фильтров сообщений организовано в таблицы фильтров, связывающие каждый **MessageFilter** с целевой конечной точки. Кроме того, в таблице фильтров можно привести список резервных конечных точек, в которые служба маршрутизации отправляет сообщение в случае сбоя соединения.  
  
 По умолчанию все фильтры сообщений в таблице оцениваются одновременно. Однако, если нужно, чтобы фильтры оценивались в определенном порядке, можно указать приоритет оценки - <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>. Сначала оцениваются все записи с наивысшим приоритетом. Если найдено сопоставление на более высоком уровне, фильтры сообщений с низким приоритетом не оцениваются. Дополнительные сведения о таблицах фильтров см. в разделе [фильтры сообщений](message-filters.md).  
  
 В следующем примере использован фильтр <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, который оценивает все сообщения как `true`. Это **MessageFilter** добавляется в таблицу «routingTable1» фильтров, которая связывает **MessageFilter** с клиентской конечной точкой «CalculatorService». **RoutingBehavior** указывает, что эта таблица следует использовать для маршрутизации сообщений, обрабатываемых этой конечной точкой службы.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  По умолчанию служба маршрутизации оценивает только заголовки сообщений. Чтобы предоставить фильтрам доступ к тексту сообщения, нужно присвоить параметру <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> значение `false`.  
  
 **Multicast**  
  
 Множество конфигураций службы маршрутизации используют логику монопольной фильтрации (сообщения перенаправляются в одну конкретную конечную точку). Однако может возникнуть необходимость перенаправить сообщение в несколько целевых конечных точек. Для многоадресной рассылки сообщения в разные целевые точки должны быть выполнены следующие условия.  
  
-   Форма канала не должна иметь тип «запрос-ответ» (хотя он может быть односторонним или дуплексным), так как данный тип требует, чтобы на запрос от клиентского приложения выдавался только один ответ.  
  
-   При оценке сообщения несколько фильтров должны возвращать значение `true`.  
  
 Если эти условия выполняются, сообщение перенаправляется во все конечные точки всех фильтров, обнаруживших значение `true`. В следующем примере определяется конфигурация маршрутизации, полученного сообщения перенаправляются в обе конечные точки, если адрес конечной точки в сообщении `http://localhost:8000/routingservice/router/rounding`.  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a>Обработка SOAP  
 Для поддержки маршрутизации сообщений между разнородными протоколами **RoutingBehavior** по умолчанию добавляет <xref:System.ServiceModel.Routing.SoapProcessingBehavior> к всем клиентским конечным точкам, которые направляются сообщения. Это поведение автоматически создает новую **MessageVersion** до маршрутизации сообщения в конечную точку, а также создается **MessageVersion** для любого ответного документа перед возвращением к запрашивающему клиентскому приложению.  
  
 Действия, предпринятые для создания нового **MessageVersion** для исходящего сообщения, следующим образом:  
  
 **Обработка запроса**  
  
-   Получить **MessageVersion** из исходящей привязки или канала.  
  
-   Получение модуля чтения текста для первоначального сообщения.  
  
-   Создайте новое сообщение с те же действия, модуля чтения текста и новый **MessageVersion**.  
  
-   Если <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, скопируйте To, From, FaultTo и RelatesTo в новое сообщение.  
  
-   Копирование всех свойств в новое сообщение.  
  
-   Сохранение первоначального сообщения с запросом для обработки ответа.  
  
-   Возврат нового сообщения с запросом.  
  
 **Обработка ответа**  
  
-   Получить **MessageVersion** исходного сообщения запроса.  
  
-   Получение модуля чтения текста для принятого ответного сообщения.  
  
-   Создание нового ответного сообщения с тем же действием и модулем чтения текста и **MessageVersion** исходного сообщения запроса.  
  
-   Если <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, скопируйте To, From, FaultTo и RelatesTo в новое сообщение.  
  
-   Копирование всех свойств в новое сообщение.  
  
-   Возврат нового ответного сообщения.  
  
 По умолчанию **SoapProcessingBehavior** клиентских конечных точек, автоматически добавляется <xref:System.ServiceModel.Routing.RoutingBehavior> при запуске службы; тем не менее, можно управлять, добавляется ли обработки SOAP ко всем клиентским конечным точкам с помощью <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> свойство. Можно напрямую добавить поведение к конкретной клиентской точке, а также включить или отключить это поведение на уровне конечной точки, если требуется более точное управление обработкой SOAP.  
  
> [!NOTE]
>  Если обработка SOAP отключена для точки, требующей версии (MessageVersion), отличной от версии первоначального сообщения с запросом, то перед отправкой сообщения в целевую конечную точку необходимо указать пользовательский механизм для выполнения любых требуемых изменений SOAP.  
  
 В следующих примерах **soapProcessingEnabled** свойство используется для предотвращения **SoapProcessingBehavior** автоматическое добавление ко всем клиентским конечным точкам.  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a>Динамическая конфигурация  
 Если добавляются дополнительные клиентские конечные точки или возникает необходимость изменить фильтры маршрутизации сообщений, нужно иметь возможность динамически обновлять конфигурацию во время выполнения. Таким образом можно предотвратить прерывание службы в конечных точках, в настоящий момент получающих сообщения через службу маршрутизации. Может оказаться недостаточным изменить файл конфигурации или код размещающего приложения. Оба этих метода требуют перезапуска приложения, что может привести к потере передаваемых в настоящий момент сообщений, а также к простою на время перезапуска службы.  
  
 Можно изменять только **RoutingConfiguration** программным способом. Изначально можно настроить службу с помощью файла конфигурации, можно только изменить конфигурацию во время выполнения, создав новый **RoutingConfigution** и передается в качестве параметра <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> метод предоставляемые <xref:System.ServiceModel.Routing.RoutingExtension> расширения службы. Наличие сообщений, передаваемых в настоящий момент по-прежнему будет направляться с предыдущей конфигурацией, во время сообщения, полученные после вызова **ApplyConfiguration** использовать новую конфигурацию. В следующем примере показано создание экземпляра службы маршрутизации с последующим изменением конфигурации.  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  При обновлении службы маршрутизации подобным образом возможно только передать новую конфигурацию. Нельзя изменить отдельные элементы текущей конфигурации или добавить в нее новые записи. Необходимо создать и передать новую конфигурацию, которая заменит текущую.  
  
> [!NOTE]
>  Все сеансы, открытые с предыдущей конфигурацией, продолжат ее использовать. Новая конфигурация применяется только к новым сеансам.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если при попытке отправки сообщения возникнет исключение <xref:System.ServiceModel.CommunicationException>, будет запущена обработка ошибок. Эти исключения обычно указывают на то, что при попытке связаться с определенной конечной точкой клиента была обнаружена проблема, например <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException> или <xref:System.ServiceModel.CommunicationObjectFaultedException>. Код обработки ошибок также перехватит и попытается повторить отправку при <xref:System.TimeoutException> происходит, это еще одно общее исключение, которое не является производным от **CommunicationException**.  
  
 Если возникнет одно из вышеприведенных исключений, служба маршрутизации перейдет к резервному списку конечных точек. В случае, если все резервные конечные точки обнаружат сбой сети или канала связи, либо конечная точка вернет исключение, указывающее на сбой целевой службы, служба маршрутизации вернет клиентскому приложению ошибку.  
  
> [!NOTE]
>  Функция обработки ошибок перехватывает и обрабатывает исключения, возникающие при отправке сообщения или при закрытии канала. Код обработки ошибок не предназначен для обнаружения или обработки исключений, созданных конечных точек приложения, в которой он взаимодействует с; <xref:System.ServiceModel.FaultException> , создаваемых службой, отображается в службе маршрутизации как **FaultMessage** и передается обратно клиенту.  
>   
>  Если при попытке службы маршрутизации перенаправить сообщение возникает ошибка, на стороне клиента можно получить исключение <xref:System.ServiceModel.FaultException>, а не исключение <xref:System.ServiceModel.EndpointNotFoundException>, которое обычно формируется при отсутствии службы маршрутизации. Таким способом служба маршрутизации может маскировать исключения и не обеспечивать полную прозрачность при просмотре вложенных исключений.  
  
### <a name="tracing-exceptions"></a>Исключения трассировки  
 При отправке сообщение в конечную точку в списке не, служба маршрутизации отслеживает полученные данные исключения и прикрепляет их в виде свойства сообщения с именем **исключения**. Таким образом данные исключения сохраняются, а пользователь получает к ним программный доступ (через инспектор сообщений).  Данные исключения хранятся в сообщении в словаре, который сопоставляет имя конечной точки со сведениями об исключении, полученными при попытке отправить сообщение.  
  
### <a name="backup-endpoints"></a>Резервные конечные точки  
 Для каждой записи фильтра в таблице фильтров можно указать список резервных конечных точек, которые будут использованы в случае сбоя при отправке в основную точку. Если произойдет такой сбой, служба маршрутизации попытается передать сообщение в конечную точку, содержащуюся в первой записи списка резервных конечных точек. Если при этом также возникнет сбой, служба попытается использовать следующую конечную точку в списке. Служба маршрутизации продолжит отправлять сообщения в каждую конечную точку списка до тех пор, пока не будет выполнено одно из следующих условий: сообщение успешно получено, все точки возвратили ошибку передачи, конечная точка возвратила сбой, не связанный с сетью или доступом.  
  
 В следующих примерах выполняется настройка службы маршрутизации для использования резервного списка.  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a>Поддерживаемые шаблоны ошибок  
 В следующей таблице описаны шаблоны, совместимые со списком резервных конечных точек, а также приведены более подробные сведения по обработке ошибок для конкретных шаблонов.  
  
|Шаблон|Сеанс|Транзакция|Контекст получения|Поддерживаемый резервный список|Примечания|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Одностороннее взаимодействие||||Да|Пытается повторно отправить сообщение резервной конечной точке. Если сообщение является многоадресным, в резервное назначение перемещается только сообщение, в канале которого произошел сбой.|  
|Одностороннее взаимодействие||✓||Нет|Возникает исключение, и выполняется откат транзакции.|  
|Одностороннее взаимодействие|||✓|Да|Пытается повторно отправить сообщение резервной конечной точке. После успешного получения сообщения нужно закрыть все контексты получения. Если сообщение не получено любой конечной точкой, завершать контекст получения не нужно.<br /><br /> В случае многоадресной рассылки сообщения контекст получения завершается, если сообщение получено хотя бы одной конечной точкой (основной или резервной). Если ни одна из конечных точек многоадресной рассылки не получила сообщение, завершать контекст получения не нужно.|  
|Одностороннее взаимодействие||✓|✓|Да|Отмените предыдущую транзакцию, создайте новую транзакцию и повторно отправьте все сообщения. Сообщения, обнаруживающие ошибку, передаются в резервное назначение.<br /><br /> После создания транзакции, в которой все операции по передаче были успешными, можно завершить контексты получения и зафиксировать транзакцию.|  
|Одностороннее взаимодействие|✓|||Да|Пытается повторно отправить сообщение резервной конечной точке. В случае многоадресного сценария в резервные назначения повторно отправляются только сообщения, в сеансах которых обнаружена ошибка или сбой при закрытии.|  
|Одностороннее взаимодействие|✓|✓||Нет|Возникает исключение, и выполняется откат транзакции.|  
|Одностороннее взаимодействие|✓||✓|Да|Пытается повторно отправить сообщение резервной конечной точке. После того как все сообщения отправлены без ошибок, сеанс указывает на то, что сообщений не осталось, служба маршрутизации закрывает все исходящие каналы сеанса, завершаются все контексты получения, а затем закрывается входящий канал сеанса.|  
|Одностороннее взаимодействие|✓|✓|✓|Да|Отмена текущей транзакции и создание новой. Повторная отправка всех предыдущих сообщений в сеансе. После создания транзакции, в которой все сообщения отправлены без ошибок, а также после того, как сеанс указывает на то, что сообщений не осталось, закрываются все исходящие каналы сеанса, завершаются все контексты получения, закрывается входящий канал и происходит фиксация транзакции.<br /><br /> Если в сеансах использовалась многоадресная рассылка, сообщения без ошибок повторно отправляются в то же назначение, а сообщения с ошибками - в резервное назначение.|  
|Двусторонний||||Да|Отправьте резервному назначению.  После того как канал вернет ответное сообщение, верните ответ исходному клиенту.|  
|Двусторонний|✓|||Да|Отправка всех сообщений в канале в резервное назначение.  После того как канал вернет ответное сообщение, верните ответ исходному клиенту.|  
|Двусторонний||✓||Нет|Возникает исключение, и выполняется откат транзакции.|  
|Двусторонний|✓|✓||Нет|Возникает исключение, и выполняется откат транзакции.|  
|Дуплекс||||Нет|В настоящий момент дуплексная связь вне сеанса не поддерживается.|  
|Дуплекс|✓|||Да|Отправьте резервному назначению.|  
  
## <a name="hosting"></a>Размещение  
 Служба маршрутизация реализована как служба WCF, поэтому она должна размещаться в приложении или в службах IIS или WAS. Рекомендуется, чтобы служба маршрутизации размещалась в служебном приложении Windows, IIS или WAS. В этом случае будут доступны преимущества этих сред размещения - автоматический запуск и управление жизненным циклом.  
  
 В следующем примере показано размещение службы маршрутизации в приложении.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Чтобы разместить службу маршрутизации в службах IIS или WAS, нужно создать файл службы (SVC) или использовать основанную на конфигурации активацию службы. При использовании файла службы нужно задать <xref:System.ServiceModel.Routing.RoutingService>, используя параметр Service. В следующем примере приведен образец файла службы, который можно использовать для размещения службы маршрутизации с помощью служб IIS или WAS.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Служба маршрутизации и олицетворение  
 Службу маршрутизации WCF можно использовать с олицетворением как для отправки, так и для получения сообщений. Применяются все стандартные ограничения Windows для процесса олицетворения. Если при написании собственной службы для использования олицетворения необходимо было настроить некоторые разрешения учетной записи или службы, то такие же шаги необходимо выполнить и для использования олицетворения в службе маршрутизации. Дополнительные сведения см. в разделе [делегирование и олицетворение](delegation-and-impersonation-with-wcf.md).  
  
 Олицетворение в службе маршрутизации требует использования олицетворения средствами ASP.NET в режиме совместимости с ASP.NET или использования учетных данных Windows, для которых олицетворение разрешено. Дополнительные сведения о режиме совместимости с ASP.NET, см. в разделе [службы WCF и ASP.NET](wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Служба маршрутизации WCF не поддерживает олицетворение с обычной проверкой подлинности.  
  
 Для использования олицетворения ASP.NET со службой маршрутизации включите режим совместимости с ASP.NET в рабочей среде размещения службы. Для службы маршрутизации уже выставлено разрешение использования режима совместимости с ASP.NET и функции олицетворения будут включены автоматически. Олицетворение - единственная поддерживаемая функция интеграции ASP.NET со службой маршрутизации.  
  
 Чтобы использовать олицетворение с помощью учетных данных Windows в службе маршрутизации, необходимо соответствующим образом настроить и службу, и учетные данные. Объект пользовательских учетных данных клиента (<xref:System.ServiceModel.Security.WindowsClientCredential>, доступный из фабрики <xref:System.ServiceModel.ChannelFactory>) определяет свойство <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>, которое должно быть задано, чтобы разрешить использование олицетворения. Наконец, в службе требуется настроить поведение <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> для установки свойства `ImpersonateCallerForAllOperations` в значение `true`. Служба маршрутизации использует этот флаг, чтобы определить, следует ли создавать клиентов для направления сообщений с олицетворением пользователей.  
  
## <a name="see-also"></a>См. также

- [Фильтры сообщений](message-filters.md)
- [Контракты маршрутизации](routing-contracts.md)
- [Выбор фильтра](choosing-a-filter.md)
