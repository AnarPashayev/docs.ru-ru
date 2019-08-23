---
title: Элемент <configSections> для <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927669"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="d1c02-102">\<Элемент > configSections для \<> конфигурации</span><span class="sxs-lookup"><span data-stu-id="d1c02-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="d1c02-103">Содержит раздел конфигурации и объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="d1c02-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="d1c02-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d1c02-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d1c02-105">&nbsp;&nbsp; **\<> configSections**</span><span class="sxs-lookup"><span data-stu-id="d1c02-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="d1c02-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d1c02-106">Attributes</span></span>

<span data-ttu-id="d1c02-107">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="d1c02-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d1c02-108">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="d1c02-108">Parent element</span></span>

|     | <span data-ttu-id="d1c02-109">Описание</span><span class="sxs-lookup"><span data-stu-id="d1c02-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d1c02-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="d1c02-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="d1c02-111">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1c02-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d1c02-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d1c02-112">Child elements</span></span>

|     | <span data-ttu-id="d1c02-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d1c02-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d1c02-114"> **\<раздел >** </span><span class="sxs-lookup"><span data-stu-id="d1c02-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="d1c02-115">Содержит объявление раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d1c02-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="d1c02-116"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="d1c02-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="d1c02-117">Определяет пространство имен для разделов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d1c02-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="d1c02-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="d1c02-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="d1c02-119">Удаляет предопределенный раздел или группу разделов.</span><span class="sxs-lookup"><span data-stu-id="d1c02-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="d1c02-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="d1c02-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="d1c02-121">Удаляет все ранее определенные разделы и группы разделов.</span><span class="sxs-lookup"><span data-stu-id="d1c02-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d1c02-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="d1c02-122">Remarks</span></span>

<span data-ttu-id="d1c02-123">Если этот элемент находится в файле конфигурации, он должен быть первым дочерним элементом  **\<элемента Configuration >** .</span><span class="sxs-lookup"><span data-stu-id="d1c02-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="d1c02-124">Пример</span><span class="sxs-lookup"><span data-stu-id="d1c02-124">Example</span></span>

<span data-ttu-id="d1c02-125">В следующем примере показано, как определить раздел конфигурации и определить параметры для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d1c02-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d1c02-126">файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="d1c02-126">Configuration file</span></span>

<span data-ttu-id="d1c02-127">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine. config*) и файлах *Web. config* , которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="d1c02-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c02-128">См. также</span><span class="sxs-lookup"><span data-stu-id="d1c02-128">See also</span></span>

- [<span data-ttu-id="d1c02-129">Схема файла конфигурации для .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1c02-129">Configuration file schema for the .NET Framework</span></span>](index.md)
