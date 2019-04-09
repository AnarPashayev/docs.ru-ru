---
title: <disableCommitThreadStack> Элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08ffd6ffcb9a8fa356d486f6d2ae1113de0fa682
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106519"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="3eade-102">\<disableCommitThreadStack > элемент</span><span class="sxs-lookup"><span data-stu-id="3eade-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="3eade-103">Указывает, фиксируется ли весь стек потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="3eade-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3eade-104">\<configuration></span></span>  
<span data-ttu-id="3eade-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="3eade-105">\<runtime></span></span>  
<span data-ttu-id="3eade-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="3eade-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eade-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3eade-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eade-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3eade-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3eade-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3eade-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eade-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3eade-110">Attributes</span></span>  
  
|<span data-ttu-id="3eade-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3eade-111">Attribute</span></span>|<span data-ttu-id="3eade-112">Описание</span><span class="sxs-lookup"><span data-stu-id="3eade-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3eade-113">enabled</span><span class="sxs-lookup"><span data-stu-id="3eade-113">enabled</span></span>|<span data-ttu-id="3eade-114">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="3eade-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3eade-115">Указывает, отключена ли фиксация всего стека потоков при запуске потока (режим по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3eade-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3eade-116">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="3eade-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3eade-117">Значение</span><span class="sxs-lookup"><span data-stu-id="3eade-117">Value</span></span>|<span data-ttu-id="3eade-118">Описание</span><span class="sxs-lookup"><span data-stu-id="3eade-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3eade-119">0</span><span class="sxs-lookup"><span data-stu-id="3eade-119">0</span></span>|<span data-ttu-id="3eade-120">Не отключать для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="3eade-121">1</span><span class="sxs-lookup"><span data-stu-id="3eade-121">1</span></span>|<span data-ttu-id="3eade-122">Отключить для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eade-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3eade-123">Child Elements</span></span>  
 <span data-ttu-id="3eade-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3eade-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eade-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3eade-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3eade-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="3eade-126">Element</span></span>|<span data-ttu-id="3eade-127">Описание</span><span class="sxs-lookup"><span data-stu-id="3eade-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3eade-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3eade-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="3eade-129">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="3eade-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eade-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="3eade-130">Remarks</span></span>  
 <span data-ttu-id="3eade-131">Режим по умолчанию для среды CLR заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="3eade-132">Если на сервере с ограниченным объемом памяти необходимо создать большое число потоков и большинство из этих потоков будут использовать очень небольшое пространство стека, сервер может работать лучше, если среда не фиксирует весь стек потоков сразу после запуска потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3eade-133">Неуправляемые узлы могут использовать флаг запуска `STARTUP_DISABLE_COMMITTHREADSTACK` в перечислении [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) для достижения такого же результата.</span><span class="sxs-lookup"><span data-stu-id="3eade-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eade-134">Пример</span><span class="sxs-lookup"><span data-stu-id="3eade-134">Example</span></span>  
 <span data-ttu-id="3eade-135">В следующем примере показано, как отключить для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="3eade-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eade-136">См. также</span><span class="sxs-lookup"><span data-stu-id="3eade-136">See also</span></span>

- [<span data-ttu-id="3eade-137">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="3eade-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3eade-138">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="3eade-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
