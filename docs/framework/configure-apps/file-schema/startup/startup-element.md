---
title: Элемент <startup>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e40ca31ddc40cccbeb3b8dda1d148ddec5032d7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489550"
---
# <a name="startup-element"></a><span data-ttu-id="d3ad5-102">\<Startup > элемент</span><span class="sxs-lookup"><span data-stu-id="d3ad5-102">\<startup> element</span></span>

<span data-ttu-id="d3ad5-103">Указывает информация запуска среды CLR.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="d3ad5-104">\<Конфигурация > \<startup ></span><span class="sxs-lookup"><span data-stu-id="d3ad5-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="d3ad5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3ad5-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3ad5-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="d3ad5-106">Attributes and elements</span></span>

 <span data-ttu-id="d3ad5-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3ad5-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d3ad5-108">Attributes</span></span>

|<span data-ttu-id="d3ad5-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d3ad5-109">Attribute</span></span>|<span data-ttu-id="d3ad5-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d3ad5-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="d3ad5-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d3ad5-112">Указывает, следует ли включить [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] политике активации среды выполнения или использовать политику активации .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d3ad5-113">атрибут useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d3ad5-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="d3ad5-114">Значение</span><span class="sxs-lookup"><span data-stu-id="d3ad5-114">Value</span></span>|<span data-ttu-id="d3ad5-115">Описание</span><span class="sxs-lookup"><span data-stu-id="d3ad5-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="d3ad5-116">Включить [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] политике активации среды выполнения для выбранной среды выполнения, используемого для привязки методы активации старой среды выполнения (таких как [функция CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) в среду выполнения, выбранный из файла конфигурации вместо ограничивая их в среде CLR версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="d3ad5-117">Таким образом Если вы выбрали CLR версии 4 или более поздней версии из файла конфигурации, смешанных сборок, созданных в более ранних версиях платформы .NET Framework, загружаются с выбранной версией среды CLR.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="d3ad5-118">Установка этого значения предотвращает CLR версии 1.1 или среду CLR версии 2.0 загрузку в одном процессе, эффективно отключение функции-process side-by-side.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="d3ad5-119">Используйте политику активации по умолчанию для .NET Framework 4 и более поздних версий, чтобы разрешить старой среды выполнения методов активации для загрузки в процесс среды CLR версии 1.1 или 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="d3ad5-120">Установка этого значения предотвращает смешанной сборки от загрузки в .NET Framework 4 или более поздней версии, если они были созданы с помощью .NET Framework 4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="d3ad5-121">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d3ad5-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d3ad5-122">Child elements</span></span>

|<span data-ttu-id="d3ad5-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="d3ad5-123">Element</span></span>|<span data-ttu-id="d3ad5-124">Описание</span><span class="sxs-lookup"><span data-stu-id="d3ad5-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3ad5-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="d3ad5-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="d3ad5-126">Указывает, что приложение поддерживает только версию 1.0 среды CLR.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d3ad5-127">Приложения, созданные с помощью среды выполнения версии 1.1 или более поздней, должны использовать  **\<supportedRuntime >** элемент.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="d3ad5-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="d3ad5-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="d3ad5-129">Указывает, какие версии среды CLR поддерживает приложение.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3ad5-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d3ad5-130">Parent elements</span></span>

|<span data-ttu-id="d3ad5-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="d3ad5-131">Element</span></span>|<span data-ttu-id="d3ad5-132">Описание</span><span class="sxs-lookup"><span data-stu-id="d3ad5-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d3ad5-133">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3ad5-134">Примечания</span><span class="sxs-lookup"><span data-stu-id="d3ad5-134">Remarks</span></span>

 <span data-ttu-id="d3ad5-135">**\<SupportedRuntime>** элемент должен использоваться всеми приложениями, собранными с применением версии 1.1 или более поздней версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="d3ad5-136">Приложения, созданные для поддержки только версии 1.0 среды выполнения, должны использовать  **\<requiredRuntime >** элемент.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="d3ad5-137">Код запуска для приложения, размещенного в Internet Explorer не учитывает  **\<startup >** элемент и его дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d3ad5-138">Атрибут useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d3ad5-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="d3ad5-139">Этот атрибут полезен, если приложение использует устаревшие активации пути, такие как [функция CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), и нужно, чтобы эти пути для активации версии 4 среды CLR вместо более ранней версии, или если приложение созданные с помощью .NET Framework 4, но имеет зависимость от сборки смешанного режима, созданных с помощью более ранней версии платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="d3ad5-140">В этих сценариях, задать для атрибута `true`.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="d3ad5-141">Присвоение атрибуту `true` предотвращает загрузку в одном процессе, эффективно отключение функции-process side-by-side CLR версии 1.1 или среду CLR версии 2.0 (см. в разделе [Side-by-Side выполнение для COM-взаимодействия](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="d3ad5-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="d3ad5-142">Пример</span><span class="sxs-lookup"><span data-stu-id="d3ad5-142">Example</span></span>

 <span data-ttu-id="d3ad5-143">Приведенный ниже показано, как указать версию среды выполнения в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d3ad5-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d3ad5-144">См. также</span><span class="sxs-lookup"><span data-stu-id="d3ad5-144">See also</span></span>

- [<span data-ttu-id="d3ad5-145">Схема параметров запуска</span><span class="sxs-lookup"><span data-stu-id="d3ad5-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d3ad5-146">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="d3ad5-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d3ad5-147">Практическое руководство. Настройка приложения для включения поддержки .NET Framework версии 4 и выше</span><span class="sxs-lookup"><span data-stu-id="d3ad5-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="d3ad5-148">[Выполнение Side-by-Side COM-взаимодействия](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3ad5-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="d3ad5-149">Внутрипроцессное параллельное выполнение</span><span class="sxs-lookup"><span data-stu-id="d3ad5-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
