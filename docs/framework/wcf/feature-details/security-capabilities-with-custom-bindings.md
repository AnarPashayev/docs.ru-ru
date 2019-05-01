---
title: Возможности безопасности при использовании пользовательских привязок
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990929"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="7a7db-102">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="7a7db-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="7a7db-103">Основные задачи обеспечения безопасности можно выполнить, используя одну из предоставляемых системой привязок.</span><span class="sxs-lookup"><span data-stu-id="7a7db-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="7a7db-104">Однако при необходимости в дополнительных элементах управления можно создать пользовательскую привязку с помощью элемента <xref:System.ServiceModel.Channels.SecurityBindingElement>, следуя объяснениям в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="7a7db-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="7a7db-105">Дополнительные сведения о пользовательских привязках см. в разделе [пользовательских привязок](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7a7db-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a7db-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7a7db-106">In This Section</span></span>  
 [<span data-ttu-id="7a7db-107">Режимы проверки подлинности SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a7db-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="7a7db-108">Содержит описание режимов проверки подлинности, которые возможны для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="7a7db-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="7a7db-109">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a7db-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="7a7db-110">Содержит описание основных шагов, которые необходимо предпринять для создания пользовательской привязки к элементу безопасности.</span><span class="sxs-lookup"><span data-stu-id="7a7db-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="7a7db-111">Практическое руководство. Создание SecurityBindingElement для заданного режима проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="7a7db-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="7a7db-112">Описывается, как создать элемент безопасности для заданного режима проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="7a7db-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="7a7db-113">Практическое руководство. Отключения безопасных сеансов в WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7a7db-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="7a7db-114">Описывается, как отключить безопасные сеансы при создании службы федерации.</span><span class="sxs-lookup"><span data-stu-id="7a7db-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="7a7db-115">Практическое руководство. Включение обнаружения повтора сообщений</span><span class="sxs-lookup"><span data-stu-id="7a7db-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="7a7db-116">Описывается, как определить, когда будет осуществлена атака воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="7a7db-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="7a7db-117">Практическое руководство. Создание вспомогательных учетных данных</span><span class="sxs-lookup"><span data-stu-id="7a7db-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="7a7db-118">Описывается, как предоставить службе подтверждающие учетные данные при необходимости.</span><span class="sxs-lookup"><span data-stu-id="7a7db-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="7a7db-119">Практическое руководство. Настройка подтверждения сигнатуры</span><span class="sxs-lookup"><span data-stu-id="7a7db-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="7a7db-120">Содержит описание шагов, которые необходимо предпринять для подтверждения подписей при использовании цифровых подписей сообщений.</span><span class="sxs-lookup"><span data-stu-id="7a7db-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="7a7db-121">Практическое руководство. Установка разницы в показаниях часов Max</span><span class="sxs-lookup"><span data-stu-id="7a7db-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="7a7db-122">Описывается, как настроить максимально допустимую разницу во времени между службой и клиентом.</span><span class="sxs-lookup"><span data-stu-id="7a7db-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="7a7db-123">Практическое руководство. Выключение шифрования цифровых сигнатур</span><span class="sxs-lookup"><span data-stu-id="7a7db-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="7a7db-124">Описывается, как отключение шифрования цифровых подписей может увеличить производительность.</span><span class="sxs-lookup"><span data-stu-id="7a7db-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a7db-125">Ссылка</span><span class="sxs-lookup"><span data-stu-id="7a7db-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="7a7db-126">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="7a7db-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="7a7db-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="7a7db-127">Related Sections</span></span>  
 [<span data-ttu-id="7a7db-128">Основные сведения об уровне защиты</span><span class="sxs-lookup"><span data-stu-id="7a7db-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="7a7db-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="7a7db-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a7db-130">См. также</span><span class="sxs-lookup"><span data-stu-id="7a7db-130">See also</span></span>

- [<span data-ttu-id="7a7db-131">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="7a7db-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="7a7db-132">Общие сведения о безопасности</span><span class="sxs-lookup"><span data-stu-id="7a7db-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="7a7db-133">Привязки, предоставляемые системой</span><span class="sxs-lookup"><span data-stu-id="7a7db-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
