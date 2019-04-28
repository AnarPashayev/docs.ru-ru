---
title: Элемент <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19103b2ac6e6dbba930050074fcea3cfd5a97661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704665"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="2d323-102">\<gcAllowVeryLargeObjects > элемент</span><span class="sxs-lookup"><span data-stu-id="2d323-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="2d323-103">На 64 разрядных платформах позволяет использовать массивы, размер которых превышает 2 гигабайта (ГБ).</span><span class="sxs-lookup"><span data-stu-id="2d323-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="2d323-104">\<Конфигурация > элемент</span><span class="sxs-lookup"><span data-stu-id="2d323-104">\<configuration> Element</span></span>  
<span data-ttu-id="2d323-105">\<Среда выполнения > элемент</span><span class="sxs-lookup"><span data-stu-id="2d323-105">\<runtime> Element</span></span>  
<span data-ttu-id="2d323-106">\<gcAllowVeryLargeObjects > элемент</span><span class="sxs-lookup"><span data-stu-id="2d323-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d323-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d323-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d323-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2d323-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2d323-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2d323-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d323-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2d323-110">Attributes</span></span>  
  
|<span data-ttu-id="2d323-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2d323-111">Attribute</span></span>|<span data-ttu-id="2d323-112">Описание</span><span class="sxs-lookup"><span data-stu-id="2d323-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2d323-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="2d323-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d323-114">Указывает, включены ли массивов, размер которых превышает 2 ГБ в общий размер на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="2d323-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2d323-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="2d323-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2d323-116">Значение</span><span class="sxs-lookup"><span data-stu-id="2d323-116">Value</span></span>|<span data-ttu-id="2d323-117">Описание</span><span class="sxs-lookup"><span data-stu-id="2d323-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2d323-118">Больше, чем 2 ГБ, общий размер массивов не включены.</span><span class="sxs-lookup"><span data-stu-id="2d323-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="2d323-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2d323-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2d323-120">Больше, чем 2 ГБ, общий размер массивов включены на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="2d323-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d323-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2d323-121">Child Elements</span></span>  
 <span data-ttu-id="2d323-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2d323-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d323-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2d323-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2d323-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="2d323-124">Element</span></span>|<span data-ttu-id="2d323-125">Описание</span><span class="sxs-lookup"><span data-stu-id="2d323-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2d323-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d323-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2d323-127">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2d323-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d323-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="2d323-128">Remarks</span></span>  
 <span data-ttu-id="2d323-129">С помощью этого элемента в файле конфигурации приложения позволяет использовать массивы, размер которых превышает 2 ГБ, но не изменяет другие ограничения на размер объекта или массива:</span><span class="sxs-lookup"><span data-stu-id="2d323-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="2d323-130">Максимальное количество элементов в массиве является <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d323-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="2d323-131">Максимальный индекс в любом измерении единый — 2,147,483,591 (0x7FFFFFC7) для массивов байтов и массивы структур однобайтовых и 2,146,435,071 (0X7FEFFFFF) для других типов.</span><span class="sxs-lookup"><span data-stu-id="2d323-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="2d323-132">Максимальный размер строки и другие не являющиеся массивами объекты не изменяется.</span><span class="sxs-lookup"><span data-stu-id="2d323-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2d323-133">Прежде чем включать эту функцию, убедитесь, что приложение не содержит небезопасный код, который предполагается, что все массивы меньше, чем размером 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="2d323-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="2d323-134">Например небезопасный код, который использует массивы в качестве буфера, можно привести к переполнению буфера записывается на предположении, что массивы не может превышать 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="2d323-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d323-135">Пример</span><span class="sxs-lookup"><span data-stu-id="2d323-135">Example</span></span>  
 <span data-ttu-id="2d323-136">В следующем примере показано, как включить эту функцию для приложения.</span><span class="sxs-lookup"><span data-stu-id="2d323-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d323-137">См. также</span><span class="sxs-lookup"><span data-stu-id="2d323-137">See also</span></span>

- [<span data-ttu-id="2d323-138">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="2d323-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="2d323-139">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="2d323-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
