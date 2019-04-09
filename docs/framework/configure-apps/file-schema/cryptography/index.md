---
title: Схема параметров криптографии
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: 00b04cc2175f4bb4cc0b74602cd3c26f4a4e342f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184461"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="f209c-102">Схема параметров криптографии</span><span class="sxs-lookup"><span data-stu-id="f209c-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="f209c-103">Схема параметров шифрования содержит элементы, с помощью которых можно сопоставить понятные имена алгоритмов с классами, реализующими алгоритмы шифрования.</span><span class="sxs-lookup"><span data-stu-id="f209c-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [**<span data-ttu-id="f209c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f209c-104">\<configuration></span></span>**](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [**<span data-ttu-id="f209c-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="f209c-105">\<mscorlib></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [**<span data-ttu-id="f209c-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="f209c-106">\<cryptographySettings></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [**<span data-ttu-id="f209c-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="f209c-107">\<cryptoNameMapping></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [**<span data-ttu-id="f209c-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="f209c-108">\<cryptoClasses></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [**<span data-ttu-id="f209c-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="f209c-109">\<cryptoClass></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [**<span data-ttu-id="f209c-110">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="f209c-110">\<nameEntry></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [**<span data-ttu-id="f209c-111">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="f209c-111">\<oidMap></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [**<span data-ttu-id="f209c-112">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="f209c-112">\<oidEntry></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="f209c-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="f209c-113">Element</span></span>|<span data-ttu-id="f209c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="f209c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f209c-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="f209c-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="f209c-116">Содержит список криптографических классов, сопоставленных с понятными именами, указанными в элементе **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="f209c-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f209c-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="f209c-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="f209c-118">Содержит криптографический класс, сопоставленный с понятным именем, указанным в элементе **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="f209c-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f209c-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="f209c-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="f209c-120">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="f209c-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="f209c-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="f209c-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="f209c-122">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="f209c-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="f209c-123">**\<mscorlib >** элемент для параметров криптографии</span><span class="sxs-lookup"><span data-stu-id="f209c-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="f209c-124">Содержит элемент **\<cryptographySettings>**.</span><span class="sxs-lookup"><span data-stu-id="f209c-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**<span data-ttu-id="f209c-125">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="f209c-125">\<nameEntry></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="f209c-126">Сопоставляет имя класса с понятным именем алгоритма, что позволяет одному классу иметь несколько понятных имен.</span><span class="sxs-lookup"><span data-stu-id="f209c-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**<span data-ttu-id="f209c-127">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="f209c-127">\<oidEntry></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="f209c-128">Сопоставляет идентификатор объекта (OID) ASN.1 с понятным именем.</span><span class="sxs-lookup"><span data-stu-id="f209c-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**<span data-ttu-id="f209c-129">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="f209c-129">\<oidMap></span></span>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="f209c-130">Содержит сопоставления идентификатора объекта ASN.1 с классами.</span><span class="sxs-lookup"><span data-stu-id="f209c-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f209c-131">См. также</span><span class="sxs-lookup"><span data-stu-id="f209c-131">See also</span></span>

- [<span data-ttu-id="f209c-132">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f209c-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f209c-133">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="f209c-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
