---
title: Практическое руководство. Включение обнаружения повтора сообщений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 3fe43e3f815e0f918e22a1ec0fd485079afadde8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156030"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="56eda-102">Практическое руководство. Включение обнаружения повтора сообщений</span><span class="sxs-lookup"><span data-stu-id="56eda-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="56eda-103">Атака воспроизведения заключается в том, что злоумышленник копирует поток сообщений между двумя сторонами и воспроизводит его для одной или нескольких сторон.</span><span class="sxs-lookup"><span data-stu-id="56eda-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="56eda-104">Если не приняты ответные меры, атакованные компьютеры обрабатывают этот поток как надлежащие сообщения, что приводит к ряду негативных последствий, таких как повторные заказы одного элемента.</span><span class="sxs-lookup"><span data-stu-id="56eda-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="56eda-105">Дополнительные сведения об обнаружении воспроизведения сообщений см. в разделе [обнаружение воспроизведения сообщений](https://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="56eda-105">For more information about message replay detection, see [Message Replay Detection](https://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="56eda-106">Следующая процедура показывает различные свойства, которые можно использовать управление обнаружением воспроизведения с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="56eda-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="56eda-107">Управление обнаружением воспроизведения на стороне клиента с помощью кода</span><span class="sxs-lookup"><span data-stu-id="56eda-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="56eda-108">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="56eda-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="56eda-109">Дополнительные сведения см. в разделе [Как Создание пользовательской привязки с использованием элемента SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="56eda-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="56eda-110">В следующем примере используется объект <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, созданный с помощью объекта <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> класса <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="56eda-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="56eda-111">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> и задайте некоторые из следующих свойств согласно необходимости:</span><span class="sxs-lookup"><span data-stu-id="56eda-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  `DetectReplay`<span data-ttu-id="56eda-112">.</span><span class="sxs-lookup"><span data-stu-id="56eda-112">.</span></span> <span data-ttu-id="56eda-113">Значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="56eda-113">A Boolean value.</span></span> <span data-ttu-id="56eda-114">Управляет тем, пытается ли клиент обнаружить воспроизведение сообщений сервера.</span><span class="sxs-lookup"><span data-stu-id="56eda-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="56eda-115">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="56eda-115">The default is `true`.</span></span>  
  
    2.  `MaxClockSkew`<span data-ttu-id="56eda-116">.</span><span class="sxs-lookup"><span data-stu-id="56eda-116">.</span></span> <span data-ttu-id="56eda-117">Значение <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="56eda-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="56eda-118">Задает максимальную разницу по времени, допускаемую механизмом обнаружения воспроизведения между клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="56eda-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="56eda-119">Механизм безопасности проверяет отправленную отметку времени и определяет, не слишком ли давно она отправлена.</span><span class="sxs-lookup"><span data-stu-id="56eda-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="56eda-120">Значение по умолчанию — 5 минут.</span><span class="sxs-lookup"><span data-stu-id="56eda-120">The default is 5 minutes.</span></span>  
  
    3.  `ReplayWindow`<span data-ttu-id="56eda-121">.</span><span class="sxs-lookup"><span data-stu-id="56eda-121">.</span></span> <span data-ttu-id="56eda-122">Значение `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="56eda-122">A `TimeSpan` value.</span></span> <span data-ttu-id="56eda-123">Задает максимальное время жизни сообщения в сети с момента его отправки сервером (через промежуточные узлы), прежде чем оно доставляется клиенту.</span><span class="sxs-lookup"><span data-stu-id="56eda-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="56eda-124">Клиент отслеживает подписи сообщений, отправленных в течение последнего промежутка времени `ReplayWindow`, с целью обнаружения воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="56eda-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  `ReplayCacheSize`<span data-ttu-id="56eda-125">.</span><span class="sxs-lookup"><span data-stu-id="56eda-125">.</span></span> <span data-ttu-id="56eda-126">Целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="56eda-126">An integer value.</span></span> <span data-ttu-id="56eda-127">Клиент сохраняет подписи сообщений в кэше.</span><span class="sxs-lookup"><span data-stu-id="56eda-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="56eda-128">Этот параметр задает максимальное количество подписей, которое может храниться в кэше.</span><span class="sxs-lookup"><span data-stu-id="56eda-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="56eda-129">Если количество сообщений, отправленных в пределах последнего окна воспроизведения, достигает предела кэша, новые сообщения отклоняются, пока не будет достигнут предел по времени для самых старых подписей в кэше.</span><span class="sxs-lookup"><span data-stu-id="56eda-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="56eda-130">Значение по умолчанию — 500000.</span><span class="sxs-lookup"><span data-stu-id="56eda-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="56eda-131">Управление обнаружением воспроизведения на стороне службы с помощью кода</span><span class="sxs-lookup"><span data-stu-id="56eda-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="56eda-132">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="56eda-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="56eda-133">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> и задайте свойства, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="56eda-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="56eda-134">Управление обнаружением воспроизведения с помощью конфигурации для клиента или службы</span><span class="sxs-lookup"><span data-stu-id="56eda-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="56eda-135">Создание [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="56eda-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="56eda-136">Создайте элемент `<security>`.</span><span class="sxs-lookup"><span data-stu-id="56eda-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="56eda-137">Создание [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) или [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="56eda-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="56eda-138">Задайте следующие значение атрибутов (согласно необходимости): `detectReplays`, `maxClockSkew`, `replayWindow` и `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="56eda-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="56eda-139">В следующем примере задаются атрибуты для обоих элементов: `<localServiceSettings>` и`<localClientSettings>`.</span><span class="sxs-lookup"><span data-stu-id="56eda-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="56eda-140">Пример</span><span class="sxs-lookup"><span data-stu-id="56eda-140">Example</span></span>  
 <span data-ttu-id="56eda-141">В следующем примере создается элемент <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> с помощью метода <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="56eda-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="56eda-142">Область воспроизведения: Только безопасность сообщений</span><span class="sxs-lookup"><span data-stu-id="56eda-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="56eda-143">Обратите внимание, что следующие процедуры применяются только для режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="56eda-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="56eda-144">В режиме транспорта и в режиме транспорта с учетными данными сообщения воспроизведение обнаруживает транспортный механизм.</span><span class="sxs-lookup"><span data-stu-id="56eda-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="56eda-145">Примечания о безопасном диалоге</span><span class="sxs-lookup"><span data-stu-id="56eda-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="56eda-146">Для привязок, обеспечивающих безопасные диалоги, можно изменить эти настройки и для канала приложения, и для привязки начальной загрузки безопасного диалога.</span><span class="sxs-lookup"><span data-stu-id="56eda-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="56eda-147">Например, можно отключить воспроизведение для канала приложения, но разрешить его для канала начальной загрузки, устанавливающего безопасный диалог.</span><span class="sxs-lookup"><span data-stu-id="56eda-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="56eda-148">Если сеансы безопасных диалогов не используются, средства обнаружения воспроизведения не гарантируют обнаружение воспроизведения в случаях использования фермы серверов и перезапуска процесса.</span><span class="sxs-lookup"><span data-stu-id="56eda-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="56eda-149">Это относится к следующим привязкам, предоставляемым системой:</span><span class="sxs-lookup"><span data-stu-id="56eda-149">This applies to the following system-provided bindings:</span></span>  
  
-   <xref:System.ServiceModel.BasicHttpBinding><span data-ttu-id="56eda-150">.</span><span class="sxs-lookup"><span data-stu-id="56eda-150">.</span></span>  
  
-   <xref:System.ServiceModel.WSHttpBinding> <span data-ttu-id="56eda-151">с помощью <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> свойство значение `false`.</span><span class="sxs-lookup"><span data-stu-id="56eda-151">with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56eda-152">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="56eda-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="56eda-153">Для компиляции кода требуются следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="56eda-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="56eda-154">См. также</span><span class="sxs-lookup"><span data-stu-id="56eda-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="56eda-155">Безопасные диалоги и безопасные сеансы</span><span class="sxs-lookup"><span data-stu-id="56eda-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="56eda-156">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="56eda-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="56eda-157">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="56eda-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
