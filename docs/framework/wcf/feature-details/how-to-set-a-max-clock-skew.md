---
title: Практическое руководство. Установка максимальной разницы в показаниях часов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586920"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="8f5a6-102">Практическое руководство. Установка максимальной разницы в показаниях часов</span><span class="sxs-lookup"><span data-stu-id="8f5a6-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="8f5a6-103">Если настройки времени в двух компьютерах различаются, возможен сбой критичных по времени функций.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="8f5a6-104">Чтобы устранить такую возможность, можно задать для свойства `MaxClockSkew` значение <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="8f5a6-105">Это свойство предусмотрено в двух классах.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f5a6-106">Для безопасного диалога изменения `MaxClockSkew` свойства должны быть сделаны при начальной загрузке службы или клиента.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="8f5a6-107">Для этого необходимо задать свойство для свойства, <xref:System.ServiceModel.Channels.SecurityBindingElement> возвращаемого <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> свойством.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="8f5a6-108">Чтобы изменить это свойство в одной из привязок, предоставляемых системой, необходимо найти элемент привязки безопасности в коллекции привязок и задать для свойства `MaxClockSkew` новое значение.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="8f5a6-109">От класса <xref:System.ServiceModel.Channels.SecurityBindingElement> наследуют два класса: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> и <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="8f5a6-110">При извлечении привязки безопасности из коллекции необходимо приведение к одному из этих типов, чтобы правильно задать свойство `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="8f5a6-111">В следующем примере используется привязка <xref:System.ServiceModel.WSHttpBinding>, которая использует класс <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="8f5a6-112">Список, указывающий тип привязки безопасности, используемый в каждой предоставляемой системой привязке, см. в разделе [привязки, предоставляемые системой](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="8f5a6-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="8f5a6-113">Создание пользовательской привязки с новым значением разницы в показаниях часов в коде</span><span class="sxs-lookup"><span data-stu-id="8f5a6-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8f5a6-114">Добавьте ссылки на следующие пространства имен в коде: <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> и <xref:System.ServiceModel.Security.Tokens> .</span><span class="sxs-lookup"><span data-stu-id="8f5a6-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="8f5a6-115">Создайте новый экземпляр класса <xref:System.ServiceModel.WSHttpBinding> и задайте для него режим безопасности <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="8f5a6-116">Создайте новый экземпляр класса <xref:System.ServiceModel.Channels.BindingElementCollection>, вызвав метод <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="8f5a6-117">С помощью метода <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> класса <xref:System.ServiceModel.Channels.BindingElementCollection> найдите требуемый элемент привязки безопасности.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="8f5a6-118">При использовании метода <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> выполните приведение к фактическому типу.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="8f5a6-119">В приведенном ниже примере производится приведение к типу <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="8f5a6-120">Задайте свойство <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> в элементе привязки безопасности.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="8f5a6-121">Создайте <xref:System.ServiceModel.ServiceHost> с требуемыми типом и базовым адресом службы.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="8f5a6-122">С помощью метода <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> добавьте конечную точку и включите <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="8f5a6-123">Задание MaxClockSkew в конфигурации</span><span class="sxs-lookup"><span data-stu-id="8f5a6-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="8f5a6-124">Создайте [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) в [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) разделе Element.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-124">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="8f5a6-125">Создайте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемент и присвойте `name` атрибуту соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="8f5a6-126">В следующем примере задается значение `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="8f5a6-127">Добавьте элемент кодирования.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-127">Add an encoding element.</span></span> <span data-ttu-id="8f5a6-128">В приведенном ниже примере добавляется [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="8f5a6-128">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="8f5a6-129">Добавьте [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) элемент и задайте `authenticationMode` для атрибута соответствующий параметр.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-129">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="8f5a6-130">В следующем примере для этого атрибута задается значение `Kerberos`, чтобы задать, что в службе используется проверка подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="8f5a6-131">Добавьте [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) и присвойте `maxClockSkew` атрибуту значение в виде `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="8f5a6-131">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="8f5a6-132">В следующем примере задается значение 7 минут.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="8f5a6-133">При необходимости добавьте [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) и задайте `maxClockSkew` для атрибута соответствующий параметр.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-133">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="8f5a6-134">Добавьте транспортный элемент.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-134">Add a transport element.</span></span> <span data-ttu-id="8f5a6-135">В следующем примере используется [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="8f5a6-135">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="8f5a6-136">Для безопасного диалога параметры безопасности должны выполняться при начальной загрузке в [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="8f5a6-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8f5a6-137">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="8f5a6-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8f5a6-138">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8f5a6-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
