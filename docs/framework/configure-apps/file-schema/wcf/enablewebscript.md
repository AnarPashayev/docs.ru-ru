---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213003"
---
# <a name="enablewebscript"></a><span data-ttu-id="ec1f6-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="ec1f6-101">\<enableWebScript></span></span>
<span data-ttu-id="ec1f6-102">Этот элемент включает поведение конечной точки, которое позволяет использовать службу с веб-страниц ASP.NET с поддержкой технологии AJAX.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="ec1f6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec1f6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec1f6-104">\<варианты поведения ></span><span class="sxs-lookup"><span data-stu-id="ec1f6-104">\<behaviors></span></span>  
<span data-ttu-id="ec1f6-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ec1f6-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="ec1f6-106">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="ec1f6-106">\<behavior></span></span>  
<span data-ttu-id="ec1f6-107">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="ec1f6-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1f6-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec1f6-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec1f6-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ec1f6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ec1f6-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec1f6-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ec1f6-111">Attributes</span></span>  
 <span data-ttu-id="ec1f6-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec1f6-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ec1f6-113">Child Elements</span></span>  
 <span data-ttu-id="ec1f6-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec1f6-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ec1f6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ec1f6-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="ec1f6-116">Element</span></span>|<span data-ttu-id="ec1f6-117">Описание</span><span class="sxs-lookup"><span data-stu-id="ec1f6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec1f6-118">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="ec1f6-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ec1f6-119">Задает набор поведений конечной точки.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec1f6-120">Примечания</span><span class="sxs-lookup"><span data-stu-id="ec1f6-120">Remarks</span></span>  
 <span data-ttu-id="ec1f6-121">Это поведение можно использовать только в сочетании со [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) стандартной привязки или [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="ec1f6-122">Дополнительные сведения об этом поведении см. в разделе <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ec1f6-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1f6-123">См. также</span><span class="sxs-lookup"><span data-stu-id="ec1f6-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="ec1f6-124">Интеграция с AJAX и поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="ec1f6-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="ec1f6-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="ec1f6-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
