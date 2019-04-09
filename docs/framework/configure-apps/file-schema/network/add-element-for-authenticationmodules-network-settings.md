---
title: <add> Элемент для authenticationModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: a46e6af97f37974805812fb0d19801d618eee4d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105876"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="60245-102">\<Добавить > элемент для authenticationModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="60245-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="60245-103">Добавляет модуль проверки подлинности в приложение.</span><span class="sxs-lookup"><span data-stu-id="60245-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="60245-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="60245-104">\<configuration></span></span>  
<span data-ttu-id="60245-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="60245-105">\<system.net></span></span>  
<span data-ttu-id="60245-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="60245-106">\<authenticationModules></span></span>  
<span data-ttu-id="60245-107">\<add></span><span class="sxs-lookup"><span data-stu-id="60245-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60245-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60245-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60245-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="60245-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60245-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="60245-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60245-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="60245-111">Attributes</span></span>  
  
|**<span data-ttu-id="60245-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="60245-112">Attribute</span></span>**|**<span data-ttu-id="60245-113">Описание</span><span class="sxs-lookup"><span data-stu-id="60245-113">Description</span></span>**|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="60245-114">Полное имя типа (обозначается <xref:System.Type.FullName%2A> свойства) и имя сборки (обозначается <xref:System.Reflection.Assembly.FullName%2A> свойство), разделенные запятыми.</span><span class="sxs-lookup"><span data-stu-id="60245-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60245-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="60245-115">Child Elements</span></span>  
 <span data-ttu-id="60245-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="60245-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60245-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="60245-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="60245-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="60245-118">Element</span></span>**|**<span data-ttu-id="60245-119">Описание</span><span class="sxs-lookup"><span data-stu-id="60245-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="60245-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="60245-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="60245-121">Задает модули, используемые для проверки подлинности сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="60245-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60245-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="60245-122">Remarks</span></span>  
 <span data-ttu-id="60245-123">Элемент `add` добавляет модуль проверки подлинности в конец списка зарегистрированных модулей проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="60245-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="60245-124">Модули проверки подлинности вызываются в порядке, в котором они были добавлены в список.</span><span class="sxs-lookup"><span data-stu-id="60245-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="60245-125">Значение для `type` атрибут должен быть допустимым именем типа и соответствующее имя сборки, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="60245-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="60245-126">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="60245-126">Configuration Files</span></span>  
 <span data-ttu-id="60245-127">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="60245-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60245-128">Пример</span><span class="sxs-lookup"><span data-stu-id="60245-128">Example</span></span>  
 <span data-ttu-id="60245-129">В следующем примере включается по умолчанию модули проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="60245-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="60245-130">Следует заменить значения для версии и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="60245-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60245-131">См. также</span><span class="sxs-lookup"><span data-stu-id="60245-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="60245-132">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="60245-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
