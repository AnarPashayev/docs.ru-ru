---
title: <developmentMode> Элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192060"
---
# <a name="developmentmode-element"></a><span data-ttu-id="03fc5-102">\<developmentMode > элемент</span><span class="sxs-lookup"><span data-stu-id="03fc5-102">\<developmentMode> Element</span></span>
<span data-ttu-id="03fc5-103">Указывает, выполняет ли среда поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="03fc5-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="03fc5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="03fc5-104">\<configuration></span></span>  
<span data-ttu-id="03fc5-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="03fc5-105">\<runtime></span></span>  
<span data-ttu-id="03fc5-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="03fc5-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03fc5-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03fc5-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03fc5-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="03fc5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="03fc5-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="03fc5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03fc5-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="03fc5-110">Attributes</span></span>  
  
|<span data-ttu-id="03fc5-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="03fc5-111">Attribute</span></span>|<span data-ttu-id="03fc5-112">Описание</span><span class="sxs-lookup"><span data-stu-id="03fc5-112">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="03fc5-113">developerInstallation</span><span class="sxs-lookup"><span data-stu-id="03fc5-113">developerInstallation</span></span>**|<span data-ttu-id="03fc5-114">Указывает, выполняет ли среда поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="03fc5-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="03fc5-115">developerInstallation атрибут</span><span class="sxs-lookup"><span data-stu-id="03fc5-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="03fc5-116">Значение</span><span class="sxs-lookup"><span data-stu-id="03fc5-116">Value</span></span>|<span data-ttu-id="03fc5-117">Описание</span><span class="sxs-lookup"><span data-stu-id="03fc5-117">Description</span></span>|  
|-----------|-----------------|  
|**<span data-ttu-id="03fc5-118">true</span><span class="sxs-lookup"><span data-stu-id="03fc5-118">true</span></span>**|<span data-ttu-id="03fc5-119">Поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="03fc5-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|**<span data-ttu-id="03fc5-120">False</span><span class="sxs-lookup"><span data-stu-id="03fc5-120">false</span></span>**|<span data-ttu-id="03fc5-121">Не выполняет поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="03fc5-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="03fc5-122">Это значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="03fc5-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03fc5-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="03fc5-123">Child Elements</span></span>  
 <span data-ttu-id="03fc5-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="03fc5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03fc5-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="03fc5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="03fc5-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="03fc5-126">Element</span></span>|<span data-ttu-id="03fc5-127">Описание</span><span class="sxs-lookup"><span data-stu-id="03fc5-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="03fc5-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03fc5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="03fc5-129">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="03fc5-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03fc5-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="03fc5-130">Remarks</span></span>  
 <span data-ttu-id="03fc5-131">Используйте этот параметр только во время разработки.</span><span class="sxs-lookup"><span data-stu-id="03fc5-131">Use this setting only at development time.</span></span> <span data-ttu-id="03fc5-132">Среда выполнения не проверяет версии на в DEVPATH сборок со строгим именем.</span><span class="sxs-lookup"><span data-stu-id="03fc5-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="03fc5-133">Он просто использует первый найденную сборку.</span><span class="sxs-lookup"><span data-stu-id="03fc5-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03fc5-134">Пример</span><span class="sxs-lookup"><span data-stu-id="03fc5-134">Example</span></span>  
 <span data-ttu-id="03fc5-135">В следующем примере показано, как среда выполнения для поиска сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="03fc5-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03fc5-136">См. также</span><span class="sxs-lookup"><span data-stu-id="03fc5-136">See also</span></span>

- [<span data-ttu-id="03fc5-137">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="03fc5-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="03fc5-138">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="03fc5-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="03fc5-139">Практическое руководство. Поиск сборок с помощью DEVPATH</span><span class="sxs-lookup"><span data-stu-id="03fc5-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
