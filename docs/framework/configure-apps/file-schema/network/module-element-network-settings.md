---
title: Элемент <module> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084119"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="44f8d-102">\<модуль > (сетевые параметры)</span><span class="sxs-lookup"><span data-stu-id="44f8d-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="44f8d-103">Добавляет в приложение новый модуль прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="44f8d-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="44f8d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="44f8d-104">\<configuration></span></span>  
<span data-ttu-id="44f8d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="44f8d-105">\<system.net></span></span>  
<span data-ttu-id="44f8d-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="44f8d-106">\<defaultProxy></span></span>  
<span data-ttu-id="44f8d-107">\<модуль ></span><span class="sxs-lookup"><span data-stu-id="44f8d-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f8d-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44f8d-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44f8d-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="44f8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44f8d-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="44f8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44f8d-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="44f8d-111">Attributes</span></span>  
  
|<span data-ttu-id="44f8d-112">**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))</span><span class="sxs-lookup"><span data-stu-id="44f8d-112">**Attribute**</span></span>|<span data-ttu-id="44f8d-113">**Описание**</span><span class="sxs-lookup"><span data-stu-id="44f8d-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="44f8d-114">Полное имя типа (обозначается <xref:System.Type.FullName%2A> свойства) и имя сборки (обозначается <xref:System.Reflection.Assembly.FullName%2A> свойство), разделенные запятыми, который реализует прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="44f8d-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44f8d-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="44f8d-115">Child Elements</span></span>  
 <span data-ttu-id="44f8d-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44f8d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44f8d-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="44f8d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44f8d-118">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="44f8d-118">**Element**</span></span>|<span data-ttu-id="44f8d-119">**Описание**</span><span class="sxs-lookup"><span data-stu-id="44f8d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44f8d-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="44f8d-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="44f8d-121">Настраивает прокси-сервер протокола передачи гипертекста (HTTP).</span><span class="sxs-lookup"><span data-stu-id="44f8d-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f8d-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="44f8d-122">Remarks</span></span>  
 <span data-ttu-id="44f8d-123">`module` Элемент регистрирует прокси-классы, реализующие <xref:System.Net.IWebProxy> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="44f8d-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="44f8d-124">После регистрации прокси-класса элемент `module` может использоваться для запроса данных через поддерживаемый прокси.</span><span class="sxs-lookup"><span data-stu-id="44f8d-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="44f8d-125">Значение для `type` атрибут должен иметь имя класса, модуля и имя из его соответствующие динамические ссылки библиотеки (DLL).</span><span class="sxs-lookup"><span data-stu-id="44f8d-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="44f8d-126">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="44f8d-126">Configuration Files</span></span>  
 <span data-ttu-id="44f8d-127">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="44f8d-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f8d-128">Пример</span><span class="sxs-lookup"><span data-stu-id="44f8d-128">Example</span></span>  
 <span data-ttu-id="44f8d-129">В следующем примере регистрируется пользовательский прокси-класс.</span><span class="sxs-lookup"><span data-stu-id="44f8d-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44f8d-130">См. также</span><span class="sxs-lookup"><span data-stu-id="44f8d-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="44f8d-131">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="44f8d-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
