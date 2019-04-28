---
title: Элемент <add> для webRequestModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 4c1116c088c12ad3859714c8d75704d0156c12f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705146"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="2724f-102">\<Добавить > элемент для webRequestModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="2724f-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="2724f-103">Добавляет пользовательский модуль веб-запросов к приложению.</span><span class="sxs-lookup"><span data-stu-id="2724f-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="2724f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2724f-104">\<configuration></span></span>  
<span data-ttu-id="2724f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2724f-105">\<system.net></span></span>  
<span data-ttu-id="2724f-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="2724f-106">\<webRequestModules></span></span>  
<span data-ttu-id="2724f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2724f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2724f-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2724f-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2724f-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2724f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2724f-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2724f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2724f-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2724f-111">Attributes</span></span>  
  
|<span data-ttu-id="2724f-112">**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))</span><span class="sxs-lookup"><span data-stu-id="2724f-112">**Attribute**</span></span>|<span data-ttu-id="2724f-113">**Описание**</span><span class="sxs-lookup"><span data-stu-id="2724f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="2724f-114">Префикс URI для запросов, обрабатываемых этот модуль веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="2724f-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="2724f-115">Полное имя типа (обозначается <xref:System.Type.FullName%2A> свойства) и имя сборки (обозначается <xref:System.Reflection.Assembly.FullName%2A> свойство), разделенные запятыми, который реализует этот модуль веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="2724f-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2724f-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2724f-116">Child Elements</span></span>  
 <span data-ttu-id="2724f-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2724f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2724f-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2724f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2724f-119">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="2724f-119">**Element**</span></span>|<span data-ttu-id="2724f-120">**Описание**</span><span class="sxs-lookup"><span data-stu-id="2724f-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2724f-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="2724f-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="2724f-122">Задает модули, используемые для запроса данных от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="2724f-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2724f-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="2724f-123">Remarks</span></span>  
 <span data-ttu-id="2724f-124">`prefix` Атрибут определяет префикс URI, который использует указанный модуль веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="2724f-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="2724f-125">Модули веб-запросов обычно регистрируются для обработки конкретного протокола, например HTTP или FTP, но могут быть зарегистрированы для обработки запросов к конкретному серверу или пути на сервере.</span><span class="sxs-lookup"><span data-stu-id="2724f-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="2724f-126">Модуль веб-запросов создается в том случае, если соответствующий префикс URI передается на <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="2724f-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2724f-127">Значение для `prefix` атрибут должен быть из ведущих символов является допустимым URI.</span><span class="sxs-lookup"><span data-stu-id="2724f-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="2724f-128">Например, `http` или `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2724f-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="2724f-129">Значение для `type` атрибут должен быть допустимым именем типа и соответствующее имя сборки, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="2724f-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="2724f-130">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="2724f-130">Configuration Files</span></span>  
 <span data-ttu-id="2724f-131">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2724f-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2724f-132">Пример</span><span class="sxs-lookup"><span data-stu-id="2724f-132">Example</span></span>  
 <span data-ttu-id="2724f-133">В следующем примере регистрируется пользовательский модуль веб-запросов для HTTP.</span><span class="sxs-lookup"><span data-stu-id="2724f-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="2724f-134">Следует заменить значения для версии и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="2724f-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2724f-135">См. также</span><span class="sxs-lookup"><span data-stu-id="2724f-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="2724f-136">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="2724f-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
