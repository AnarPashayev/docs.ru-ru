---
title: <oidEntry> Элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: c686d2b99ad66aec753a356b09fa3c7151193808
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219347"
---
# <a name="oidentry-element"></a><span data-ttu-id="18e46-102">\<oidEntry > элемент</span><span class="sxs-lookup"><span data-stu-id="18e46-102">\<oidEntry> Element</span></span>
<span data-ttu-id="18e46-103">Сопоставляет идентификатор объекта (OID) ASN.1 с понятным именем.</span><span class="sxs-lookup"><span data-stu-id="18e46-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="18e46-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="18e46-104">\<configuration></span></span>  
<span data-ttu-id="18e46-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="18e46-105">\<mscorlib></span></span>  
<span data-ttu-id="18e46-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="18e46-106">\<cryptographySettings></span></span>  
<span data-ttu-id="18e46-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="18e46-107">\<oidMap></span></span>  
<span data-ttu-id="18e46-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="18e46-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e46-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18e46-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18e46-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="18e46-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18e46-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="18e46-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18e46-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="18e46-112">Attributes</span></span>  
  
|<span data-ttu-id="18e46-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="18e46-113">Attribute</span></span>|<span data-ttu-id="18e46-114">Описание</span><span class="sxs-lookup"><span data-stu-id="18e46-114">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="18e46-115">OID</span><span class="sxs-lookup"><span data-stu-id="18e46-115">OID</span></span>**|<span data-ttu-id="18e46-116">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="18e46-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="18e46-117">Указывает идентификатор Объекта ASN.1, соответствующий алгоритм, реализованный класс.</span><span class="sxs-lookup"><span data-stu-id="18e46-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|**<span data-ttu-id="18e46-118">имя</span><span class="sxs-lookup"><span data-stu-id="18e46-118">name</span></span>**|<span data-ttu-id="18e46-119">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="18e46-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="18e46-120">Указывает значение для **имя** атрибут в [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) тега.</span><span class="sxs-lookup"><span data-stu-id="18e46-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18e46-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="18e46-121">Child Elements</span></span>  
 <span data-ttu-id="18e46-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="18e46-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18e46-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="18e46-123">Parent Elements</span></span>  
  
|<span data-ttu-id="18e46-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="18e46-124">Element</span></span>|<span data-ttu-id="18e46-125">Описание</span><span class="sxs-lookup"><span data-stu-id="18e46-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18e46-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18e46-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="18e46-127">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="18e46-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="18e46-128">Содержит `cryptographySettings` элемент.</span><span class="sxs-lookup"><span data-stu-id="18e46-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="18e46-129">Содержит сопоставления идентификатора объекта ASN.1 с классами.</span><span class="sxs-lookup"><span data-stu-id="18e46-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18e46-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="18e46-130">Remarks</span></span>  
 <span data-ttu-id="18e46-131">Идентификаторы объектов ASN.1 определяют алгоритмы в некоторых криптографических форматах.</span><span class="sxs-lookup"><span data-stu-id="18e46-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="18e46-132">Понятные имена алгоритмов, которые вы хотите определить сопоставления идентификаторов объектов.</span><span class="sxs-lookup"><span data-stu-id="18e46-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e46-133">Пример</span><span class="sxs-lookup"><span data-stu-id="18e46-133">Example</span></span>  
 <span data-ttu-id="18e46-134">В следующем примере показано, как использовать  **\<oidEntry >** элемент для сопоставления идентификатора объекта хэш-алгоритма RIPEMD-160 с реализацией этого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="18e46-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18e46-135">См. также</span><span class="sxs-lookup"><span data-stu-id="18e46-135">See also</span></span>

- [<span data-ttu-id="18e46-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="18e46-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="18e46-137">Схема параметров криптографии</span><span class="sxs-lookup"><span data-stu-id="18e46-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="18e46-138">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="18e46-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="18e46-139">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="18e46-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="18e46-140">Отображение идентификаторов объектов на криптографические алгоритмы</span><span class="sxs-lookup"><span data-stu-id="18e46-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
