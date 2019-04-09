---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091659"
---
# <a name="rsa"></a><span data-ttu-id="02db7-101">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="02db7-101">\<rsa></span></span>
<span data-ttu-id="02db7-102">Защищенный клиент WCF, подключающийся к конечной точке с использованием этого удостоверения, проверяет, что среди утверждений, представленных сервером, есть утверждение, содержащее открытый ключ RSA, который используется для конструирования этого удостоверения.</span><span class="sxs-lookup"><span data-stu-id="02db7-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="02db7-103">\<удостоверение ></span><span class="sxs-lookup"><span data-stu-id="02db7-103">\<identity></span></span>  
<span data-ttu-id="02db7-104">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="02db7-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02db7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02db7-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02db7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="02db7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="02db7-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="02db7-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02db7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="02db7-108">Attributes</span></span>  
  
|<span data-ttu-id="02db7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="02db7-109">Attribute</span></span>|<span data-ttu-id="02db7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="02db7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02db7-111">value</span><span class="sxs-lookup"><span data-stu-id="02db7-111">value</span></span>|<span data-ttu-id="02db7-112">Дополнительная строка.</span><span class="sxs-lookup"><span data-stu-id="02db7-112">Optional String.</span></span> <span data-ttu-id="02db7-113">Значение открытого ключа RSA, с которым происходит сравнение на клиенте.</span><span class="sxs-lookup"><span data-stu-id="02db7-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02db7-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="02db7-114">Child Elements</span></span>  
 <span data-ttu-id="02db7-115">Нет</span><span class="sxs-lookup"><span data-stu-id="02db7-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02db7-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="02db7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="02db7-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="02db7-117">Element</span></span>|<span data-ttu-id="02db7-118">Описание</span><span class="sxs-lookup"><span data-stu-id="02db7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02db7-119">\<удостоверение ></span><span class="sxs-lookup"><span data-stu-id="02db7-119">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="02db7-120">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="02db7-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02db7-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="02db7-121">Remarks</span></span>  
 <span data-ttu-id="02db7-122">Проверка RSA дает возможность ограничить проверку подлинности, задействовав один сертификат с использованием его ключа RSA или другого значения ключа RSA, созданного в отдельном порядке.</span><span class="sxs-lookup"><span data-stu-id="02db7-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="02db7-123">Это позволяет выполнить более строгую проверку подлинности конкретного ключа RSA, однако если значение ключа RSA будет изменено, служба больше не будет работать с существующими клиентами.</span><span class="sxs-lookup"><span data-stu-id="02db7-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="02db7-124">Дополнительные сведения об использовании удостоверения для проверки службы для клиента, см. в разделе [службы идентификации и проверки подлинности](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="02db7-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02db7-125">Пример</span><span class="sxs-lookup"><span data-stu-id="02db7-125">Example</span></span>  
 <span data-ttu-id="02db7-126">В следующем коде конфигурации задается значение открытого ключа сертификата X.509, используемого для проверки подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="02db7-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="02db7-127">См. также</span><span class="sxs-lookup"><span data-stu-id="02db7-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="02db7-128">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="02db7-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="02db7-129">\<удостоверение ></span><span class="sxs-lookup"><span data-stu-id="02db7-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
