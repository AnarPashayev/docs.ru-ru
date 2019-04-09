---
title: <remove> Элемент для authenticationModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 0eb3ef7db422d5cbbe70bd5633798b8d3787452d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125257"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d2731-102">\<Удалить > элемент для authenticationModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="d2731-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d2731-103">Удаляет модуль проверки подлинности из приложения.</span><span class="sxs-lookup"><span data-stu-id="d2731-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="d2731-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d2731-104">\<configuration></span></span>  
<span data-ttu-id="d2731-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d2731-105">\<system.net></span></span>  
<span data-ttu-id="d2731-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="d2731-106">\<authenticationModules></span></span>  
<span data-ttu-id="d2731-107">\<Удалить ></span><span class="sxs-lookup"><span data-stu-id="d2731-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2731-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2731-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2731-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d2731-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d2731-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d2731-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2731-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d2731-111">Attributes</span></span>  
  
|**<span data-ttu-id="d2731-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d2731-112">Attribute</span></span>**|**<span data-ttu-id="d2731-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d2731-113">Description</span></span>**|  
|-------------------|---------------------|  
|**<span data-ttu-id="d2731-114">type</span><span class="sxs-lookup"><span data-stu-id="d2731-114">type</span></span>**|<span data-ttu-id="d2731-115">Имя модуля проверки подлинности для удаления.</span><span class="sxs-lookup"><span data-stu-id="d2731-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2731-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d2731-116">Child Elements</span></span>  
 <span data-ttu-id="d2731-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d2731-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2731-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d2731-118">Parent Elements</span></span>  
  
|**<span data-ttu-id="d2731-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="d2731-119">Element</span></span>**|**<span data-ttu-id="d2731-120">Описание</span><span class="sxs-lookup"><span data-stu-id="d2731-120">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="d2731-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d2731-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="d2731-122">Задает модули, используемые для проверки подлинности сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="d2731-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2731-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="d2731-123">Remarks</span></span>  
 <span data-ttu-id="d2731-124">`remove` Элемент удаляет модули проверки подлинности, которые были ранее определены в файле конфигурации или на более высоком уровне в иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d2731-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="d2731-125">Значение для `type` атрибут должен быть допустимым именем класса.</span><span class="sxs-lookup"><span data-stu-id="d2731-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d2731-126">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="d2731-126">Configuration Files</span></span>  
 <span data-ttu-id="d2731-127">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d2731-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2731-128">Пример</span><span class="sxs-lookup"><span data-stu-id="d2731-128">Example</span></span>  
 <span data-ttu-id="d2731-129">В следующем примере удаляется модуля проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d2731-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2731-130">См. также</span><span class="sxs-lookup"><span data-stu-id="d2731-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d2731-131">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="d2731-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
