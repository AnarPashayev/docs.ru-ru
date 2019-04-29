---
title: Элемент <webRequestModules> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e5d1780a204b2e99593d51179a479845fd49e608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704951"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="4a1da-102">\<webRequestModules > (сетевые параметры)</span><span class="sxs-lookup"><span data-stu-id="4a1da-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="4a1da-103">Задает модули, используемые для запроса данных от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="4a1da-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="4a1da-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4a1da-104">\<configuration></span></span>  
<span data-ttu-id="4a1da-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4a1da-105">\<system.net></span></span>  
<span data-ttu-id="4a1da-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="4a1da-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1da-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a1da-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a1da-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4a1da-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4a1da-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4a1da-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a1da-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4a1da-110">Attributes</span></span>  
 <span data-ttu-id="4a1da-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4a1da-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a1da-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4a1da-112">Child Elements</span></span>  
  
|<span data-ttu-id="4a1da-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="4a1da-113">**Element**</span></span>|<span data-ttu-id="4a1da-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4a1da-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4a1da-115">add</span><span class="sxs-lookup"><span data-stu-id="4a1da-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="4a1da-116">Добавляет пользовательский модуль веб-запросов к приложению.</span><span class="sxs-lookup"><span data-stu-id="4a1da-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="4a1da-117">clear</span><span class="sxs-lookup"><span data-stu-id="4a1da-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="4a1da-118">Удаляет все зарегистрированные модули веб-запросов из приложения.</span><span class="sxs-lookup"><span data-stu-id="4a1da-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="4a1da-119">remove</span><span class="sxs-lookup"><span data-stu-id="4a1da-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="4a1da-120">Удаляет пользовательский модуль веб-запросов из приложения.</span><span class="sxs-lookup"><span data-stu-id="4a1da-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a1da-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4a1da-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4a1da-122">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="4a1da-122">**Element**</span></span>|<span data-ttu-id="4a1da-123">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4a1da-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4a1da-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="4a1da-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="4a1da-125">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="4a1da-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a1da-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="4a1da-126">Remarks</span></span>  
 <span data-ttu-id="4a1da-127">Элемент `webRequestModules` регистрирует потомки класса <xref:System.Net.WebRequest>, чтобы обработать запросы информации к сетевым узлам.</span><span class="sxs-lookup"><span data-stu-id="4a1da-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="4a1da-128">Модули веб-запросов необходимо реализовать <xref:System.Net.IWebRequestCreate> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4a1da-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="4a1da-129">.NET Framework включает модули веб-запросов для URI, которые начинаются с `http://`, `https://`, и `file://`.</span><span class="sxs-lookup"><span data-stu-id="4a1da-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="4a1da-130">Модули по умолчанию можно переопределить только путем регистрации пользовательского модуля в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4a1da-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4a1da-131">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="4a1da-131">Configuration Files</span></span>  
 <span data-ttu-id="4a1da-132">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4a1da-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a1da-133">Пример</span><span class="sxs-lookup"><span data-stu-id="4a1da-133">Example</span></span>  
 <span data-ttu-id="4a1da-134">В следующем примере регистрируется модуль HTTP по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4a1da-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="4a1da-135">Следует заменить значения для версии и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="4a1da-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a1da-136">См. также</span><span class="sxs-lookup"><span data-stu-id="4a1da-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="4a1da-137">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="4a1da-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
