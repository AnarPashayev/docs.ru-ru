---
title: Элемент <xmlSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2919e8d4c1af858973ff3d2b58b4d3bc4f925527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018073"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="8a77d-102">\<xmlSerializer > элемент</span><span class="sxs-lookup"><span data-stu-id="8a77d-102">\<xmlSerializer> Element</span></span>
<span data-ttu-id="8a77d-103">Указывает, выполнена ли дополнительная проверка хода выполнения <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8a77d-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="8a77d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8a77d-104">\<configuration></span></span>  
<span data-ttu-id="8a77d-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="8a77d-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a77d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a77d-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a77d-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8a77d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8a77d-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8a77d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a77d-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8a77d-109">Attributes</span></span>  
  
|<span data-ttu-id="8a77d-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8a77d-110">Attribute</span></span>|<span data-ttu-id="8a77d-111">Описание</span><span class="sxs-lookup"><span data-stu-id="8a77d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a77d-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="8a77d-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="8a77d-113">Указывает, выполнена ли проверка хода выполнения <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8a77d-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="8a77d-114">Присвойте атрибуту значение "true" или "false".</span><span class="sxs-lookup"><span data-stu-id="8a77d-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="8a77d-115">Значение по умолчанию - "true".</span><span class="sxs-lookup"><span data-stu-id="8a77d-115">The default is "true".</span></span>|  
|<span data-ttu-id="8a77d-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="8a77d-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="8a77d-117">Укажите, следует ли объекту <xref:System.Xml.Serialization.XmlSerializer> использовать установленную сериализацию прежней версии, которая создает сборки путем написания кода на C# в файле и компиляции его в сборку.</span><span class="sxs-lookup"><span data-stu-id="8a77d-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="8a77d-118">Значение по умолчанию — **false**.</span><span class="sxs-lookup"><span data-stu-id="8a77d-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a77d-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8a77d-119">Child Elements</span></span>  
 <span data-ttu-id="8a77d-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8a77d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a77d-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8a77d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8a77d-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="8a77d-122">Element</span></span>|<span data-ttu-id="8a77d-123">Описание</span><span class="sxs-lookup"><span data-stu-id="8a77d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a77d-124">Элемент \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="8a77d-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="8a77d-125">Содержит параметры конфигурации для классов <xref:System.Xml.Serialization.XmlSerializer> и <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="8a77d-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a77d-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="8a77d-126">Remarks</span></span>  
 <span data-ttu-id="8a77d-127">По умолчанию <xref:System.Xml.Serialization.XmlSerializer> обеспечивает дополнительный уровень безопасности в отношении возможных атак типа "отказ в обслуживании" во время десериализации ненадежных данных.</span><span class="sxs-lookup"><span data-stu-id="8a77d-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="8a77d-128">Такие атаки отслеживаются путем определения бесконечных циклов во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="8a77d-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="8a77d-129">При обнаружении таких условий, исключение со следующим сообщением: «Внутренняя ошибка: сбой десериализации при перемещении по базовому потоку.»</span><span class="sxs-lookup"><span data-stu-id="8a77d-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="8a77d-130">Такое сообщение еще не означает, что система подвергается атаке типа "отказ в обслуживании".</span><span class="sxs-lookup"><span data-stu-id="8a77d-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="8a77d-131">В редких случаях механизм определения бесконечного цикла сообщает о ложном положительном результате, и выдается исключение для допустимых входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="8a77d-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="8a77d-132">Если обнаружится, что некоторые допустимые сообщения приложения отклоняются из-за использования такого дополнительного уровня защиты, задайте атрибут **checkDeserializeAdvances** со значением false.</span><span class="sxs-lookup"><span data-stu-id="8a77d-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a77d-133">Пример</span><span class="sxs-lookup"><span data-stu-id="8a77d-133">Example</span></span>  
 <span data-ttu-id="8a77d-134">В приведенном ниже примере кода атрибут **checkDeserializeAdvances** задан как false.</span><span class="sxs-lookup"><span data-stu-id="8a77d-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a77d-135">См. также</span><span class="sxs-lookup"><span data-stu-id="8a77d-135">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="8a77d-136">Элемент \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="8a77d-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="8a77d-137">Сериализация XML и SOAP</span><span class="sxs-lookup"><span data-stu-id="8a77d-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
