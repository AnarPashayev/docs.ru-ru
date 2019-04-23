---
title: Элемент <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdce2181490d32212cd2629e98267e43bbe0d334
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189408"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="e60a0-102">\<ThrowUnobservedTaskExceptions > элемент</span><span class="sxs-lookup"><span data-stu-id="e60a0-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="e60a0-103">Определяет, будут ли необработанные исключения задачи завершать выполняющийся процесс.</span><span class="sxs-lookup"><span data-stu-id="e60a0-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="e60a0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e60a0-104">\<configuration></span></span>  
<span data-ttu-id="e60a0-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="e60a0-105">\<runtime></span></span>  
<span data-ttu-id="e60a0-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="e60a0-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60a0-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e60a0-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e60a0-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e60a0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e60a0-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e60a0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e60a0-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e60a0-110">Attributes</span></span>  
  
|<span data-ttu-id="e60a0-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e60a0-111">Attribute</span></span>|<span data-ttu-id="e60a0-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e60a0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e60a0-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e60a0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e60a0-114">Указывает, должно ли прекратиться выполняющегося процесса необработанные исключения задачи.</span><span class="sxs-lookup"><span data-stu-id="e60a0-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e60a0-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="e60a0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e60a0-116">Значение</span><span class="sxs-lookup"><span data-stu-id="e60a0-116">Value</span></span>|<span data-ttu-id="e60a0-117">Описание</span><span class="sxs-lookup"><span data-stu-id="e60a0-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e60a0-118">Не прекращает выполнение запущенного процесса для необработанное исключение задачи.</span><span class="sxs-lookup"><span data-stu-id="e60a0-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="e60a0-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e60a0-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e60a0-120">Завершает работу выполняющегося процесса для необработанное исключение задачи.</span><span class="sxs-lookup"><span data-stu-id="e60a0-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e60a0-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e60a0-121">Child Elements</span></span>  
 <span data-ttu-id="e60a0-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e60a0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e60a0-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e60a0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e60a0-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="e60a0-124">Element</span></span>|<span data-ttu-id="e60a0-125">Описание</span><span class="sxs-lookup"><span data-stu-id="e60a0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e60a0-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e60a0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e60a0-127">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e60a0-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="e60a0-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="e60a0-128">Remarks</span></span>  
 <span data-ttu-id="e60a0-129">Если возникает исключение, с которым связан <xref:System.Threading.Tasks.Task> не было соблюдено, существует не <xref:System.Threading.Tasks.Task.Wait%2A> операции, родительский не подключен и <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> свойство не было считано, будет считаться непредвиденное исключение задачи.</span><span class="sxs-lookup"><span data-stu-id="e60a0-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="e60a0-130">В [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], по по умолчанию, если <xref:System.Threading.Tasks.Task> , имеет непредвиденное исключение удаляется сборщиком мусора, метод завершения создает исключение и завершает процесс.</span><span class="sxs-lookup"><span data-stu-id="e60a0-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="e60a0-131">Завершение процесса определяется временем мусора и финализация.</span><span class="sxs-lookup"><span data-stu-id="e60a0-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="e60a0-132">Чтобы облегчить разработчикам писать асинхронный код, основанный на задачах, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] изменяет это поведение по умолчанию для исключений без наблюдения.</span><span class="sxs-lookup"><span data-stu-id="e60a0-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="e60a0-133">Ненаблюдаемые исключения по-прежнему вызывать <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> событие, но по умолчанию не завершает процесс.</span><span class="sxs-lookup"><span data-stu-id="e60a0-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="e60a0-134">Вместо этого исключение игнорируется после события, независимо от того, обнаруживает ли обработчик событий, исключение.</span><span class="sxs-lookup"><span data-stu-id="e60a0-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="e60a0-135">В [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], можно использовать [ \<ThrowUnobservedTaskExceptions > элемент](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) в файле конфигурации приложения для включения [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] поведение возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="e60a0-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="e60a0-136">Можно также указать поведение исключений в одном из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="e60a0-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="e60a0-137">Переменной среды `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="e60a0-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="e60a0-138">Установив реестра DWORD значение ThrowUnobservedTaskExceptions = 1 в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Ключ NETFramework.</span><span class="sxs-lookup"><span data-stu-id="e60a0-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e60a0-139">Пример</span><span class="sxs-lookup"><span data-stu-id="e60a0-139">Example</span></span>  
 <span data-ttu-id="e60a0-140">В следующем примере показано включение возникновение исключений в задачах с помощью файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="e60a0-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e60a0-141">Пример</span><span class="sxs-lookup"><span data-stu-id="e60a0-141">Example</span></span>  
 <span data-ttu-id="e60a0-142">В следующем примере показано, как непредвиденное исключение из задачи.</span><span class="sxs-lookup"><span data-stu-id="e60a0-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="e60a0-143">Код должен выполняться как выпущенные программы работать правильно.</span><span class="sxs-lookup"><span data-stu-id="e60a0-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e60a0-144">См. также</span><span class="sxs-lookup"><span data-stu-id="e60a0-144">See also</span></span>

- [<span data-ttu-id="e60a0-145">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e60a0-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="e60a0-146">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e60a0-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
