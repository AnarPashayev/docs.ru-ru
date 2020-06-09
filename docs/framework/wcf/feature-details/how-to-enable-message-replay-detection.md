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
ms.openlocfilehash: bf45b39f59e2fe38fec88d1fac23ab824c009546
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597089"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="d2a5e-102">Практическое руководство. Включение обнаружения повтора сообщений</span><span class="sxs-lookup"><span data-stu-id="d2a5e-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="d2a5e-103">Атака воспроизведения заключается в том, что злоумышленник копирует поток сообщений между двумя сторонами и воспроизводит его для одной или нескольких сторон.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="d2a5e-104">Если не приняты ответные меры, атакованные компьютеры обрабатывают этот поток как надлежащие сообщения, что приводит к ряду негативных последствий, таких как повторные заказы одного элемента.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="d2a5e-105">Дополнительные сведения об обнаружении воспроизведения сообщений см. в разделе [обнаружение воспроизведения сообщений](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="d2a5e-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="d2a5e-106">В следующей процедуре показаны различные свойства, которые можно использовать для управления обнаружением воспроизведения с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d2a5e-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="d2a5e-107">Управление обнаружением воспроизведения на стороне клиента с помощью кода</span><span class="sxs-lookup"><span data-stu-id="d2a5e-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="d2a5e-108">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="d2a5e-109">Дополнительные сведения см. в разделе [инструкции. Создание пользовательской привязки с помощью SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="d2a5e-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="d2a5e-110">В следующем примере используется объект <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, созданный с помощью объекта <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> класса <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="d2a5e-111">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> и задайте некоторые из следующих свойств согласно необходимости:</span><span class="sxs-lookup"><span data-stu-id="d2a5e-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="d2a5e-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-112">`DetectReplay`.</span></span> <span data-ttu-id="d2a5e-113">Значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-113">A Boolean value.</span></span> <span data-ttu-id="d2a5e-114">Управляет тем, пытается ли клиент обнаружить воспроизведение сообщений сервера.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="d2a5e-115">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="d2a5e-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-116">`MaxClockSkew`.</span></span> <span data-ttu-id="d2a5e-117">Значение <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="d2a5e-118">Задает максимальную разницу по времени, допускаемую механизмом обнаружения воспроизведения между клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="d2a5e-119">Механизм безопасности проверяет отправленную отметку времени и определяет, не слишком ли давно она отправлена.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="d2a5e-120">Значение по умолчанию равно 5 минутам.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="d2a5e-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-121">`ReplayWindow`.</span></span> <span data-ttu-id="d2a5e-122">Значение `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-122">A `TimeSpan` value.</span></span> <span data-ttu-id="d2a5e-123">Задает максимальное время жизни сообщения в сети с момента его отправки сервером (через промежуточные узлы), прежде чем оно доставляется клиенту.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="d2a5e-124">Клиент отслеживает подписи сообщений, отправленных в течение последнего промежутка времени `ReplayWindow`, с целью обнаружения воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="d2a5e-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="d2a5e-126">Целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-126">An integer value.</span></span> <span data-ttu-id="d2a5e-127">Клиент сохраняет подписи сообщений в кэше.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="d2a5e-128">Этот параметр задает максимальное количество подписей, которое может храниться в кэше.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="d2a5e-129">Если количество сообщений, отправленных в пределах последнего окна воспроизведения, достигает предела кэша, новые сообщения отклоняются, пока не будет достигнут предел по времени для самых старых подписей в кэше.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="d2a5e-130">Значение по умолчанию — 500000.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="d2a5e-131">Управление обнаружением воспроизведения на стороне службы с помощью кода</span><span class="sxs-lookup"><span data-stu-id="d2a5e-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="d2a5e-132">Создайте элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> для использования в привязке <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="d2a5e-133">С помощью свойства <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> получите ссылку на класс <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> и задайте свойства, как указано выше.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="d2a5e-134">Управление обнаружением воспроизведения с помощью конфигурации для клиента или службы</span><span class="sxs-lookup"><span data-stu-id="d2a5e-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="d2a5e-135">Создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d2a5e-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="d2a5e-136">Создайте элемент `<security>`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="d2a5e-137">Создайте [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) или [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d2a5e-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="d2a5e-138">Задайте следующие значение атрибутов (согласно необходимости): `detectReplays`, `maxClockSkew`, `replayWindow` и `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="d2a5e-139">В следующем примере задаются атрибуты для обоих элементов: `<localServiceSettings>`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d2a5e-140">Пример</span><span class="sxs-lookup"><span data-stu-id="d2a5e-140">Example</span></span>  
 <span data-ttu-id="d2a5e-141">В следующем примере создается элемент <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> с помощью метода <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> и задает свойства воспроизведения привязки.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="d2a5e-142">Область воспроизведения: только для режима безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="d2a5e-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="d2a5e-143">Обратите внимание, что следующие процедуры применяются только для режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="d2a5e-144">В режиме транспорта и в режиме транспорта с учетными данными сообщения воспроизведение обнаруживает транспортный механизм.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="d2a5e-145">Примечания о безопасном диалоге</span><span class="sxs-lookup"><span data-stu-id="d2a5e-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="d2a5e-146">Для привязок, обеспечивающих безопасные диалоги, можно изменить эти настройки и для канала приложения, и для привязки начальной загрузки безопасного диалога.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="d2a5e-147">Например, можно отключить воспроизведение для канала приложения, но разрешить его для канала начальной загрузки, устанавливающего безопасный диалог.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="d2a5e-148">Если сеансы безопасных диалогов не используются, средства обнаружения воспроизведения не гарантируют обнаружение воспроизведения в случаях использования фермы серверов и перезапуска процесса.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="d2a5e-149">Это относится к следующим привязкам, предоставляемым системой:</span><span class="sxs-lookup"><span data-stu-id="d2a5e-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="d2a5e-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="d2a5e-151">Привязка <xref:System.ServiceModel.WSHttpBinding>, в которой свойство <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2a5e-152">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="d2a5e-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="d2a5e-153">Для компиляции кода требуются следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="d2a5e-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="d2a5e-154">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="d2a5e-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="d2a5e-155">Безопасные диалоги и безопасные сеансы</span><span class="sxs-lookup"><span data-stu-id="d2a5e-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="d2a5e-156">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d2a5e-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
