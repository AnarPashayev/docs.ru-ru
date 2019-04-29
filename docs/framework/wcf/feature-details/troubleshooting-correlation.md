---
title: Устранение неполадок корреляции
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932825"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="ead29-102">Устранение неполадок корреляции</span><span class="sxs-lookup"><span data-stu-id="ead29-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="ead29-103">Корреляция позволяет сопоставлять сообщения службы рабочего процесса друг с другом и с нужным экземпляром рабочего процесса. Если же корреляция настроена неправильно, то сообщения не будут приниматься и приложения будут работать неправильно.</span><span class="sxs-lookup"><span data-stu-id="ead29-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="ead29-104">В этом разделе даны общие сведения о нескольких методах устранения неполадок корреляции, а также перечислен ряд распространенных проблем, которые возникают при использовании корреляции.</span><span class="sxs-lookup"><span data-stu-id="ead29-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="ead29-105">Обработка события UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="ead29-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="ead29-106">Событие <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> происходит, когда служба получает неизвестное сообщение, в том числе сообщение, для которого не удается выполнить корреляцию с существующим экземпляром.</span><span class="sxs-lookup"><span data-stu-id="ead29-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="ead29-107">Для резидентных служб это событие можно обрабатывать в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="ead29-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="ead29-108">Для служб, размещенных на веб-сервере, это событие можно обработать, создав класс, производный от <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory>, и переопределив метод <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="ead29-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="ead29-109">Затем этот настраиваемый объект <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> можно указать в файле `svc` для службы.</span><span class="sxs-lookup"><span data-stu-id="ead29-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 <span data-ttu-id="ead29-110">Когда вызывается этот обработчик, сообщение можно получить через свойство <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> объекта <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>. Оно будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ead29-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```Output
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="ead29-111">Проверка сообщений, передаваемых в обработчик события <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>, может помочь понять, почему не выполнена корреляция сообщения с экземпляром службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="ead29-112">Использование отслеживания для наблюдения за ходом рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="ead29-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="ead29-113">Отслеживание позволяет наблюдать за ходом рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="ead29-114">По умолчанию записи отслеживания создаются для событий жизненного цикла рабочего процесса, событий жизненного цикла действия, распространения ошибок и возобновления закладок.</span><span class="sxs-lookup"><span data-stu-id="ead29-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="ead29-115">Кроме того, настраиваемые действия могут создавать настраиваемые записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ead29-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="ead29-116">При устранении неполадок корреляции наиболее полезны записи отслеживания действий, записи возобновления закладок и записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="ead29-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="ead29-117">Записи отслеживания действий позволяют определить текущий ход выполнения рабочего процесса и выявить действие обмена сообщения, которое в данный момент ожидает сообщений.</span><span class="sxs-lookup"><span data-stu-id="ead29-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="ead29-118">Записи возобновления закладок полезны, поскольку в них указывается, что сообщение получено рабочим процессом, а в записях распространения ошибок регистрируются все ошибки в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="ead29-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="ead29-119">Чтобы включить отслеживание, укажите нужный объект <xref:System.Activities.Tracking.TrackingParticipant> в свойстве <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> объекта <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ead29-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="ead29-120">В следующем примере `ConsoleTrackingParticipant` (из [настраиваемое отслеживание](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) образец) настраивается с помощью профиль отслеживания по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ead29-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="ead29-121">Участник отслеживания, такой как ConsoleTrackingParticipant, удобен для резидентных служб рабочего процесса с окном консоли.</span><span class="sxs-lookup"><span data-stu-id="ead29-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="ead29-122">Для службы веб сервере, участника отслеживания, который записывает данные отслеживания в постоянное хранилище следует использовать, например встроенный <xref:System.Activities.Tracking.EtwTrackingParticipant>, или настраиваемого участника отслеживания, записывает сведения в файл.</span><span class="sxs-lookup"><span data-stu-id="ead29-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="ead29-123">Дополнительные сведения об отслеживании и настройке отслеживания для службы рабочего процесса, размещенные в Интернете, см. в разделе [отслеживание и трассировка рабочих процессов](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Настройка отслеживания для рабочего процесса](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)и [ Отслеживание &#91;образцы WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) примеры.</span><span class="sxs-lookup"><span data-stu-id="ead29-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="ead29-124">Использование трассировки WCF</span><span class="sxs-lookup"><span data-stu-id="ead29-124">Use WCF Tracing</span></span>
 <span data-ttu-id="ead29-125">Трассировка WCF отслеживает поток входящих и исходящих сообщений для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="ead29-126">Данные такой трассировки удобны при устранении неполадок корреляции, особенно для корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="ead29-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="ead29-127">Чтобы включить трассировку, укажите нужные прослушиватели трассировки в разделе `system.diagnostics` файла `web.config` для службы рабочего процесса, размещенной на веб-сервере, или файла `app.config` для резидентной службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="ead29-128">Чтобы включить содержимое сообщений в файл трассировки, укажите значение `true` для атрибута `logEntireMessage` в элементе `messageLogging` в разделе `diagnostics` объекта `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="ead29-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="ead29-129">В следующем примере для данных трассировки, включая содержимое сообщений, задается запись в файл с именем `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="ead29-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="ead29-130">Чтобы просмотреть сведения о трассировке, содержащийся в `service.svclog`, [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) используется.</span><span class="sxs-lookup"><span data-stu-id="ead29-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="ead29-131">Оно особенно полезно при устранении неполадок корреляции по содержимому, поскольку можно просматривать содержимое сообщений, точно определять переданные данные и проверять соответствие <xref:System.ServiceModel.CorrelationQuery> для корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="ead29-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="ead29-132">Дополнительные сведения о трассировке WCF см. в разделе [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), и [с помощью трассировки для устранения неполадок приложения](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="ead29-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="ead29-133">Распространенные проблемы корреляции обмена контекстом</span><span class="sxs-lookup"><span data-stu-id="ead29-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="ead29-134">Для правильной работы некоторых типов корреляции необходимо использовать определенный тип привязки.</span><span class="sxs-lookup"><span data-stu-id="ead29-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="ead29-135">Примерами служат корреляция по схеме «запрос-ответ», где требуется двусторонняя привязка, такая как <xref:System.ServiceModel.BasicHttpBinding>, и корреляция обмена контекстом, для которой требуется привязка на основе контекста, такая как <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="ead29-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="ead29-136">Большинство привязок поддерживают двусторонние операции, поэтому проблема совместимости редко возникает для корреляции по схеме «запрос-ответ», однако существует лишь небольшое число привязок на основе контекста, включая <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> и <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="ead29-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="ead29-137">Если не используется одна из этих привязок, то первый вызов службы рабочего процесса завершится успешно, однако последующие вызовы завершатся ошибкой со следующим исключением <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="ead29-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="ead29-138">Данные контекста, используемые для корреляции контекста, можно вернуть из <xref:System.ServiceModel.Activities.SendReply> в действие <xref:System.ServiceModel.Activities.Receive>, которое инициализирует корреляцию контекста, если используется двусторонняя операция, или указать в вызывающем объекте в случае односторонней операции.</span><span class="sxs-lookup"><span data-stu-id="ead29-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="ead29-139">Если контекст не отправляется вызывающим объектом и не возвращается службой рабочего процесса, то при вызове последующей операции будет возвращаться исключение <xref:System.ServiceModel.FaultException>, описанное ранее.</span><span class="sxs-lookup"><span data-stu-id="ead29-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="ead29-140">Распространенные проблемы корреляции по схеме «запрос-ответ»</span><span class="sxs-lookup"><span data-stu-id="ead29-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="ead29-141">Корреляция запросов и ответов используется с <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> пары для реализации двусторонней операции в службе рабочего процесса и с <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> пары, вызывающей двустороннюю операцию в другой веб- Служба.</span><span class="sxs-lookup"><span data-stu-id="ead29-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="ead29-142">При вызове двусторонней операции в службе WCF, служба может быть либо традиционного императивного службы WCF на основе кода, или он может быть службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="ead29-143">Для корреляции «запрос-ответ» необходимо использовать двустороннюю привязку, такую как <xref:System.ServiceModel.BasicHttpBinding>, и операции должны быть двусторонними.</span><span class="sxs-lookup"><span data-stu-id="ead29-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="ead29-144">Если служба рабочего процесса имеет двусторонние операции в параллельном режиме, или перекрывающиеся <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> или <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> пары, то неявной корреляции обработки управления, предоставляемые <xref:System.ServiceModel.Activities.WorkflowServiceHost>может оказаться недостаточно, особенно в сценариях с высокой загрузкой, и сообщения могут маршрутизироваться неправильно.</span><span class="sxs-lookup"><span data-stu-id="ead29-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="ead29-145">Чтобы предотвратить эту проблему, рекомендуется всегда явно указывать <xref:System.ServiceModel.Activities.CorrelationHandle> при использовании корреляции «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="ead29-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="ead29-146">При использовании **SendAndReceiveReply** и **ReceiveAndSendReply** шаблоны из раздела Messaging **элементов** в конструкторе рабочих процессов, <xref:System.ServiceModel.Activities.CorrelationHandle> явно задан по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ead29-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="ead29-147">Если рабочий процесс создается из программного кода, то дескриптор <xref:System.ServiceModel.Activities.CorrelationHandle> указывается в свойстве <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> первого действия из пары.</span><span class="sxs-lookup"><span data-stu-id="ead29-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="ead29-148">В следующем примере действие <xref:System.ServiceModel.Activities.Receive> настраивается с явным дескриптором <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A>, указанным в <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="ead29-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="ead29-149">Сохраняемость не допускается между <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> пары или <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> пары.</span><span class="sxs-lookup"><span data-stu-id="ead29-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="ead29-150">Создается зона несохраняемости, которая существует до завершения обоих действий.</span><span class="sxs-lookup"><span data-stu-id="ead29-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="ead29-151">Если действие, например действие Delay, находится в этой зоне несохраняемости и вызывает переход рабочего процесса в состояние бездействия, рабочий поток не будет сохранен, даже если узел настроен на сохранение рабочих потоков после их перехода в состояние бездействия.</span><span class="sxs-lookup"><span data-stu-id="ead29-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="ead29-152">Если действие, например действие Persist, пытается выполнить явное сохранение в зоне несохраняемости, формируется неустранимое исключение, выполнение рабочего процесса прерывается, а вызывающему возвращается исключение <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="ead29-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="ead29-153">Сообщение о неустранимом исключении «System.InvalidOperationException: Сохранение действия не могут содержаться в блоках несохраняемости.».</span><span class="sxs-lookup"><span data-stu-id="ead29-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="ead29-154">Это исключение не возвращается вызывающему, его можно обнаружить, если включено отслеживание.</span><span class="sxs-lookup"><span data-stu-id="ead29-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="ead29-155">Сообщение об исключении <xref:System.ServiceModel.FaultException>, возвращаемое вызывающему: «Операцию выполнить не удалось, потому что рабочий процесс '5836145b-7da2-49d0-a052-a49162adeab6' завершился».</span><span class="sxs-lookup"><span data-stu-id="ead29-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="ead29-156">Дополнительные сведения о корреляция запросов и ответов, см. в разделе [типа запрос-ответ](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="ead29-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="ead29-157">Распространенные проблемы корреляции по содержимому</span><span class="sxs-lookup"><span data-stu-id="ead29-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="ead29-158">Корреляция по содержимому применяется, если служба рабочего процесса получает несколько сообщений, а нужный экземпляр определяется по некоторому фрагменту данных в передаваемых сообщениях.</span><span class="sxs-lookup"><span data-stu-id="ead29-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="ead29-159">При корреляции по содержимому такие данные в сообщении, например номер заказчика или идентификатор заказа, используются для маршрутизации сообщений в нужный экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ead29-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="ead29-160">В этом разделе описан ряд распространенных проблем, которые возникают при использовании корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="ead29-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="ead29-161">Убедитесь, что определяющие данные уникальны</span><span class="sxs-lookup"><span data-stu-id="ead29-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="ead29-162">Данные, используемые для идентификации экземпляра, хэшируются в ключ корреляции.</span><span class="sxs-lookup"><span data-stu-id="ead29-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="ead29-163">Необходимо обеспечить уникальность данных, используемых для корреляции. В противном случае в хэшированном ключе могут возникнуть конфликты, которые приведут к неправильной маршрутизации сообщений.</span><span class="sxs-lookup"><span data-stu-id="ead29-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="ead29-164">Например, корреляция на основе только имени заказчика может вызвать конфликт, так как возможно наличие заказчиков с одинаковыми именами.</span><span class="sxs-lookup"><span data-stu-id="ead29-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="ead29-165">Двоеточие (:) не должно встречаться в данных, используемых для корреляции сообщений, так как оно уже применяется в качестве разделителя ключа и значения в запросе сообщения, формирующих строку, которая затем хэшируется.</span><span class="sxs-lookup"><span data-stu-id="ead29-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="ead29-166">Если используется сохраняемость, убедитесь, что текущие определяющие данные не используются в ранее сохраненном экземпляре.</span><span class="sxs-lookup"><span data-stu-id="ead29-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="ead29-167">Эту проблему можно выявить, временно отключив сохраняемость.</span><span class="sxs-lookup"><span data-stu-id="ead29-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="ead29-168">С помощью трассировки WCF можно просмотреть вычисленный ключ корреляции. Такая трассировка полезна в отладке проблем с ключом корреляции.</span><span class="sxs-lookup"><span data-stu-id="ead29-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="ead29-169">Конфликты</span><span class="sxs-lookup"><span data-stu-id="ead29-169">Race Conditions</span></span>
 <span data-ttu-id="ead29-170">Между получением сообщения службой и инициализацией корреляции проходит некоторое время, в течение которого последующие сообщения будут пропускаться.</span><span class="sxs-lookup"><span data-stu-id="ead29-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="ead29-171">Если служба рабочего процесса инициализирует корреляцию по содержимому с использованием данных, переданных от клиента через одностороннюю операцию, а вызывающий объект немедленно отправляет последующие сообщения, то такие сообщения будут пропускаться в течение этого интервала.</span><span class="sxs-lookup"><span data-stu-id="ead29-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="ead29-172">Чтобы избежать этого, используйте для инициализации корреляции двустороннюю операцию или используйте действие <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="ead29-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="ead29-173">Проблемы с запросами корреляции</span><span class="sxs-lookup"><span data-stu-id="ead29-173">Correlation Query Issues</span></span>
 <span data-ttu-id="ead29-174">Запросы корреляции указывают, какие данные в сообщении используются для корреляции сообщения.</span><span class="sxs-lookup"><span data-stu-id="ead29-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="ead29-175">Эти данные указываются с помощью запроса XPath.</span><span class="sxs-lookup"><span data-stu-id="ead29-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="ead29-176">Если сообщения в службу не доставляются, хотя ошибки не обнаруживаются, то одним из приемов диагностики является указание вместо запроса XPath литерального значения, совпадающего со значением данных сообщения.</span><span class="sxs-lookup"><span data-stu-id="ead29-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="ead29-177">Чтобы указать литеральное значение, используйте функцию `string`.</span><span class="sxs-lookup"><span data-stu-id="ead29-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="ead29-178">В следующем примере <xref:System.ServiceModel.MessageQuerySet> настраивается для использования литерального значения `11445` для `OrderId`, а запрос XPath помещается в комментарий.</span><span class="sxs-lookup"><span data-stu-id="ead29-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="ead29-179">Если запрос XPath настроен неправильно, таким образом, данные корреляции не загружаются, возвращается ошибка со следующим сообщением: «Запрос корреляции возвратил пустой результирующий набор.</span><span class="sxs-lookup"><span data-stu-id="ead29-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="ead29-180">Проверьте правильность настройки запросов корреляции для данной конечной точки».</span><span class="sxs-lookup"><span data-stu-id="ead29-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="ead29-181">Одним из быстрых способов решения этой проблемы является замена запроса XPath на литеральное значение, как описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="ead29-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="ead29-182">Эта проблема может возникать при использовании построителя запросов XPath в **Добавление инициализаторов корреляции** или **корреляция по определению** диалоговые окна и службой рабочего процесса использует контракты сообщений.</span><span class="sxs-lookup"><span data-stu-id="ead29-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="ead29-183">В следующем примере определяется класс контракта сообщения.</span><span class="sxs-lookup"><span data-stu-id="ead29-183">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="ead29-184">В рабочем процессе этот контракт сообщения используется действием <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="ead29-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="ead29-185">Идентификатор `CartId` в заголовке сообщения используется для корреляции сообщения с правильным экземпляром.</span><span class="sxs-lookup"><span data-stu-id="ead29-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="ead29-186">Если запрос XPath, возвращающий идентификатор `CartId`, создается с помощью диалоговых окон корреляции в конструкторе рабочих процессов, формируется следующий неверный запрос XPath.</span><span class="sxs-lookup"><span data-stu-id="ead29-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="ead29-187">Этот запрос XPath был бы правильным, если бы действие <xref:System.ServiceModel.Activities.Receive> использовало параметры для данных, но, поскольку оно использует контракт сообщения, запрос является неверным.</span><span class="sxs-lookup"><span data-stu-id="ead29-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="ead29-188">Следующий запрос XPath является правильным для получения идентификатора `CartId` из заголовка.</span><span class="sxs-lookup"><span data-stu-id="ead29-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="ead29-189">Это можно проверить, изучив текст сообщения.</span><span class="sxs-lookup"><span data-stu-id="ead29-189">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="ead29-190">В следующем примере показано действие <xref:System.ServiceModel.Activities.Receive>, настроенное для операции `AddItem`, использующей предыдущий контракт сообщения для получения данных.</span><span class="sxs-lookup"><span data-stu-id="ead29-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="ead29-191">Запрос XPath настроен правильно.</span><span class="sxs-lookup"><span data-stu-id="ead29-191">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
