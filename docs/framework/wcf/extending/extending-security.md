---
title: Расширение безопасности
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 95dacf3ef975be1ddd56db747936cca35db50625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099642"
---
# <a name="extending-security"></a><span data-ttu-id="79823-102">Расширение безопасности</span><span class="sxs-lookup"><span data-stu-id="79823-102">Extending Security</span></span>
<span data-ttu-id="79823-103">Чтобы адаптировать новые типы утверждений и пользовательские маркеры, можно расширить инфраструктуру безопасности Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="79823-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="79823-104">Это подробно описывается в следующих подразделах.</span><span class="sxs-lookup"><span data-stu-id="79823-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79823-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="79823-105">In This Section</span></span>  
  
 [<span data-ttu-id="79823-106">Пользовательские учетные данные и проверка учетных данных</span><span class="sxs-lookup"><span data-stu-id="79823-106">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="79823-107">Рассматривается, как модель удостоверения используется при проверке пользовательских учетных данных.</span><span class="sxs-lookup"><span data-stu-id="79823-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="79823-108">Пользовательские маркеры</span><span class="sxs-lookup"><span data-stu-id="79823-108">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="79823-109">Маркеры, выдаваемые службой маркеров безопасности (STS), - обычно маркеры SAML.</span><span class="sxs-lookup"><span data-stu-id="79823-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="79823-110">В этом разделе описывается, как создать тип пользовательского маркера.</span><span class="sxs-lookup"><span data-stu-id="79823-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="79823-111">Пользовательская авторизация</span><span class="sxs-lookup"><span data-stu-id="79823-111">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="79823-112">Объясняется, как реализовать пользовательскую авторизацию.</span><span class="sxs-lookup"><span data-stu-id="79823-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="79823-113">Переопределение идентификатора службы для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="79823-113">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="79823-114">Описывается, как переопределить идентификацию службы для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="79823-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="79823-115">Практическое руководство. Создание пользовательского средства проверки идентификации клиентов</span><span class="sxs-lookup"><span data-stu-id="79823-115">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="79823-116">Демонстрирует, как проверить идентификацию пользовательской конечной точки.</span><span class="sxs-lookup"><span data-stu-id="79823-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="79823-117">Практическое руководство. Использование отдельных сертификатов X.509 для подписывания и шифрования</span><span class="sxs-lookup"><span data-stu-id="79823-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="79823-118">Обычно сообщения подписываются и шифруются одним сертификатом.</span><span class="sxs-lookup"><span data-stu-id="79823-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="79823-119">В этом разделе объясняется, как при необходимости использовать два сертификата.</span><span class="sxs-lookup"><span data-stu-id="79823-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="79823-120">Практическое руководство. Изменение поставщика служб шифрования для закрытого ключа сертификата X.509</span><span class="sxs-lookup"><span data-stu-id="79823-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="79823-121">Объясняет, как изменить поставщика служб шифрования, используемый для предоставления закрытый ключ сертификата X.509 и как интегрировать поставщика в платформу Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="79823-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79823-122">Ссылка</span><span class="sxs-lookup"><span data-stu-id="79823-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="79823-123">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="79823-123">Related Sections</span></span>  
 [<span data-ttu-id="79823-124">Безопасность</span><span class="sxs-lookup"><span data-stu-id="79823-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="79823-125">Базовое программирование WCF</span><span class="sxs-lookup"><span data-stu-id="79823-125">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="79823-126">См. также</span><span class="sxs-lookup"><span data-stu-id="79823-126">See also</span></span>

- [<span data-ttu-id="79823-127">Общие сведения о безопасности</span><span class="sxs-lookup"><span data-stu-id="79823-127">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
