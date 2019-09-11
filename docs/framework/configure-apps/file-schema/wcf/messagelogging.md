---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855123"
---
# <a name="messagelogging"></a><span data-ttu-id="e3ad9-101">\<Мессажелоггинг ></span><span class="sxs-lookup"><span data-stu-id="e3ad9-101">\<messageLogging></span></span>
<span data-ttu-id="e3ad9-102">Данный элемент определяет параметры ведения журнала сообщений для Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
<span data-ttu-id="e3ad9-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3ad9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3ad9-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3ad9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3ad9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Диагностика >** ](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="e3ad9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="e3ad9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Мессажелоггинг >**</span><span class="sxs-lookup"><span data-stu-id="e3ad9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ad9-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3ad9-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3ad9-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e3ad9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3ad9-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3ad9-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e3ad9-110">Attributes</span></span>  
  
|<span data-ttu-id="e3ad9-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e3ad9-111">Attribute</span></span>|<span data-ttu-id="e3ad9-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e3ad9-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="e3ad9-113">Логическое значение, указывающее, заносится ли в журнал сообщение целиком (тело и заголовок сообщения).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="e3ad9-114">Значением по умолчанию является `false`, означающее, что в журнал заносится только заголовок сообщения.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="e3ad9-115">Действие этого параметра распространяется на все уровни ведения журнала сообщений (службы, транспорта и неправильных сообщений).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="e3ad9-116">Логическое значение, указывающее, заносятся ли в журнал неправильные сообщения.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="e3ad9-117">Такие сообщения не учитываются в значении `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="e3ad9-118">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="e3ad9-119">Логическое значение, указывающее, трассируются ли сообщения на уровне службы (перед шифрованием и преобразованиями, связанными с транспортом).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="e3ad9-120">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="e3ad9-121">Логическое значение, указывающее, трассируются ли сообщения на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="e3ad9-122">Применяются все фильтры, указанные в файле конфигурации, и трассируются только те сообщения, которые соответствуют данным фильтрам.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="e3ad9-123">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="e3ad9-124">Положительное целое число, указывающее максимальное количество сообщений для внесения в журнал.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="e3ad9-125">Значение по умолчанию — 1000.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="e3ad9-126">Положительное целое число, указывающее максимальный размер сообщения для внесения в журнал (в байтах).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="e3ad9-127">Сообщения, размер которых превышает данное ограничение, в журнал не вносятся.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="e3ad9-128">Действие этого параметра распространяется на все уровни трассировки.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-128">This setting affects all trace levels.</span></span> <span data-ttu-id="e3ad9-129">Значение по умолчанию - 262 144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="e3ad9-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3ad9-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e3ad9-130">Child Elements</span></span>  
  
|<span data-ttu-id="e3ad9-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="e3ad9-131">Element</span></span>|<span data-ttu-id="e3ad9-132">Описание</span><span class="sxs-lookup"><span data-stu-id="e3ad9-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3ad9-133">фильтры</span><span class="sxs-lookup"><span data-stu-id="e3ad9-133">filters</span></span>|<span data-ttu-id="e3ad9-134">Элемент `filters` содержит коллекцию фильтров XPath.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="e3ad9-135">Если включена регистрация сообщений на уровне транспорта (то есть атрибуту `logMessagesAtTransportLevel` присвоено значение `true`), в журнал заносятся только те сообщения, которые соответствуют фильтрам.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="e3ad9-136">Фильтры применяются только на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="e3ad9-137">Фильтры не влияют на ведение журнала сообщений уровня службы и неправильно сформированных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="e3ad9-138">Единственным атрибутом элемента `filter` является XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3ad9-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e3ad9-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e3ad9-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="e3ad9-140">Element</span></span>|<span data-ttu-id="e3ad9-141">Описание</span><span class="sxs-lookup"><span data-stu-id="e3ad9-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3ad9-142">диагностика</span><span class="sxs-lookup"><span data-stu-id="e3ad9-142">diagnostics</span></span>|<span data-ttu-id="e3ad9-143">Определяет параметры WCF для проверки во время выполнения и управления администратором.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ad9-144">Примечания</span><span class="sxs-lookup"><span data-stu-id="e3ad9-144">Remarks</span></span>  
 <span data-ttu-id="e3ad9-145">Сообщения вносятся в журнал на трех различных уровнях в стеке: сообщения уровня службы, транспорта и неправильные сообщения.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="e3ad9-146">Активация каждого уровня может происходить отдельно.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="e3ad9-147">Фильтры XPath можно добавлять для внесения в журнал отдельных сообщений уровней транспорта и службы.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="e3ad9-148">Если не определено ни одного фильтра, в журнал вносятся все сообщения.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="e3ad9-149">Фильтры применяются только к заголовкам сообщений.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="e3ad9-150">Текст сообщения не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-150">The body is ignored.</span></span> <span data-ttu-id="e3ad9-151">WCF игнорирует тело сообщения для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="e3ad9-152">Если требуется применить фильтрацию по содержимому текста сообщения, можно создать пользовательский прослушиватель с фильтром, который будет выполнять эту задачу.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="e3ad9-153">Чтобы включить трассировку сообщений, необходимо создать прослушиватель трассировки.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="e3ad9-154">Сам прослушиватель может быть любым прослушивателем, который работает с архитектурой трассировки <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="e3ad9-155">В следующем примере показано создание подобного прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="e3ad9-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="e3ad9-156">Пример</span><span class="sxs-lookup"><span data-stu-id="e3ad9-156">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="e3ad9-157">См. также</span><span class="sxs-lookup"><span data-stu-id="e3ad9-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="e3ad9-158">Настройка ведения журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="e3ad9-158">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
