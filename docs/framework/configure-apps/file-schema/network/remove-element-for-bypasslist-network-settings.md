---
title: Элемент <remove> для bypasslist (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697896"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="015b0-102">Элемент > @no__t 0remove для бипасслист (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="015b0-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="015b0-103">Удаляет IP-адрес или DNS-имя из списка обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="015b0-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[<span data-ttu-id="015b0-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="015b0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="015b0-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="015b0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="015b0-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="015b0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="015b0-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="015b0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="015b0-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="015b0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="015b0-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="015b0-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="015b0-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="015b0-110">Attributes and Elements</span></span>

<span data-ttu-id="015b0-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="015b0-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="015b0-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="015b0-112">Attributes</span></span>

|<span data-ttu-id="015b0-113">**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))</span><span class="sxs-lookup"><span data-stu-id="015b0-113">**Attribute**</span></span>|<span data-ttu-id="015b0-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="015b0-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="015b0-115">Регулярное выражение, описывающее IP-адрес или DNS-имя.</span><span class="sxs-lookup"><span data-stu-id="015b0-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="015b0-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="015b0-116">Child Elements</span></span>

<span data-ttu-id="015b0-117">Нет.</span><span class="sxs-lookup"><span data-stu-id="015b0-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="015b0-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="015b0-118">Parent Elements</span></span>

|<span data-ttu-id="015b0-119">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="015b0-119">**Element**</span></span>|<span data-ttu-id="015b0-120">**Описание**</span><span class="sxs-lookup"><span data-stu-id="015b0-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="015b0-121">бипасслист</span><span class="sxs-lookup"><span data-stu-id="015b0-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="015b0-122">Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="015b0-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="015b0-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="015b0-123">Remarks</span></span>

<span data-ttu-id="015b0-124">Элемент `remove` удаляет регулярные выражения, описывающие IP-адреса или имена DNS-серверов, из списка адресов, которые обходят прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="015b0-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="015b0-125">Адреса были определены ранее в файле конфигурации или на более высоком уровне иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="015b0-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="015b0-126">Значение атрибута `address` должно быть регулярным выражением, описывающим набор IP-адресов или имен узлов.</span><span class="sxs-lookup"><span data-stu-id="015b0-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="015b0-127">Дополнительные сведения о регулярных выражениях см. в разделе. [.NET Framework регулярных выражений](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="015b0-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="015b0-128">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="015b0-128">Configuration Files</span></span>

<span data-ttu-id="015b0-129">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="015b0-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="015b0-130">Пример</span><span class="sxs-lookup"><span data-stu-id="015b0-130">Example</span></span>

<span data-ttu-id="015b0-131">В следующем примере удаляется предыдущее определение для домена adventure-works.com, а затем домен contoso.com добавляется в список обхода.</span><span class="sxs-lookup"><span data-stu-id="015b0-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="015b0-132">См. также</span><span class="sxs-lookup"><span data-stu-id="015b0-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="015b0-133">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="015b0-133">Network Settings Schema</span></span>](index.md)
