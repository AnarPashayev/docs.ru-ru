---
title: Элемент <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802110"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="2d6f4-102">Элемент \<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="2d6f4-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="2d6f4-103">Определяет, использует ли среда выполнения постоянный объем памяти для вычисления хэш-кодов методом <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2d6f4-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="2d6f4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d6f4-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d6f4-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2d6f4-105">Attributes and Elements</span></span>

<span data-ttu-id="2d6f4-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d6f4-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2d6f4-107">Attributes</span></span>

|<span data-ttu-id="2d6f4-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2d6f4-108">Attribute</span></span>|<span data-ttu-id="2d6f4-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="2d6f4-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2d6f4-110">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d6f4-111">Определяет, выделяет ли среда CLR постоянный объем памяти при вычислении хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2d6f4-112">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="2d6f4-112">enabled Attribute</span></span>

|<span data-ttu-id="2d6f4-113">Значение</span><span class="sxs-lookup"><span data-stu-id="2d6f4-113">Value</span></span>|<span data-ttu-id="2d6f4-114">Описание</span><span class="sxs-lookup"><span data-stu-id="2d6f4-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="2d6f4-115">0</span><span class="sxs-lookup"><span data-stu-id="2d6f4-115">0</span></span>|<span data-ttu-id="2d6f4-116">Среда CLR выделяет переменный объем памяти методу <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> для вычисления хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="2d6f4-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-117">This is the default.</span></span>|
|<span data-ttu-id="2d6f4-118">1</span><span class="sxs-lookup"><span data-stu-id="2d6f4-118">1</span></span>|<span data-ttu-id="2d6f4-119">Среда CLR выделяет постоянный объем памяти методу <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> для вычисления хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2d6f4-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2d6f4-120">Child Elements</span></span>

<span data-ttu-id="2d6f4-121">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d6f4-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2d6f4-122">Parent Elements</span></span>

|<span data-ttu-id="2d6f4-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="2d6f4-123">Element</span></span>|<span data-ttu-id="2d6f4-124">Описание</span><span class="sxs-lookup"><span data-stu-id="2d6f4-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2d6f4-125">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2d6f4-126">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d6f4-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="2d6f4-127">Remarks</span></span>

<span data-ttu-id="2d6f4-128">По умолчанию среда CLR выделяет переменный объем памяти для метода <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> и при попытке вычисления этим методом хэш-кодов очень больших строк (длиной свыше нескольких миллионов символов) может быть создано исключение <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="2d6f4-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="2d6f4-129">Добавив этот элемент в файл конфигурации приложения и присвоив его атрибуту `enabled` значение "1", можно определить, что метод <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> использует другой алгоритм, который выделяет для вычисления хэш-кодов постоянный объем памяти.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d6f4-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Элемент не используется в Windows 8 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="2d6f4-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d6f4-131">См. также</span><span class="sxs-lookup"><span data-stu-id="2d6f4-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2d6f4-132">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="2d6f4-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2d6f4-133">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="2d6f4-133">Configuration File Schema</span></span>](../index.md)
