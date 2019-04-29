---
title: Элемент <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: f9f12d9e61e2472b897169727bbb4fbf9833efd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701350"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="ca35d-102">\<прослушиватели > элемент для \<трассировки ></span><span class="sxs-lookup"><span data-stu-id="ca35d-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="ca35d-103">Указывает прослушиватель, который собирает, хранилищ и направляет сообщения.</span><span class="sxs-lookup"><span data-stu-id="ca35d-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="ca35d-104">Прослушиватели направляют выходные данные трассировки соответствующему целевому объекту.</span><span class="sxs-lookup"><span data-stu-id="ca35d-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="ca35d-105">\<Конфигурация > элемент</span><span class="sxs-lookup"><span data-stu-id="ca35d-105">\<configuration> Element</span></span>  
<span data-ttu-id="ca35d-106">\<System.Diagnostics > элемент</span><span class="sxs-lookup"><span data-stu-id="ca35d-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="ca35d-107">\<трассировки > элемент</span><span class="sxs-lookup"><span data-stu-id="ca35d-107">\<trace> Element</span></span>  
<span data-ttu-id="ca35d-108">\<прослушиватели > элемент для \<трассировки ></span><span class="sxs-lookup"><span data-stu-id="ca35d-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca35d-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca35d-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca35d-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ca35d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ca35d-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ca35d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca35d-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ca35d-112">Attributes</span></span>  
 <span data-ttu-id="ca35d-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ca35d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca35d-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ca35d-114">Child Elements</span></span>  
  
|<span data-ttu-id="ca35d-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="ca35d-115">Element</span></span>|<span data-ttu-id="ca35d-116">Описание</span><span class="sxs-lookup"><span data-stu-id="ca35d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca35d-117">\<add></span><span class="sxs-lookup"><span data-stu-id="ca35d-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="ca35d-118">Добавляет прослушиватель в коллекцию `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="ca35d-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ca35d-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="ca35d-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="ca35d-120">Очищает коллекцию `Listeners` для трассировки.</span><span class="sxs-lookup"><span data-stu-id="ca35d-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="ca35d-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="ca35d-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="ca35d-122">Удаляет прослушиватель из `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="ca35d-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca35d-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ca35d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ca35d-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="ca35d-124">Element</span></span>|<span data-ttu-id="ca35d-125">Описание</span><span class="sxs-lookup"><span data-stu-id="ca35d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca35d-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca35d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ca35d-127">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ca35d-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="ca35d-128">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="ca35d-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca35d-129">Примечания</span><span class="sxs-lookup"><span data-stu-id="ca35d-129">Remarks</span></span>  
 <span data-ttu-id="ca35d-130"><xref:System.Diagnostics.Debug> И <xref:System.Diagnostics.Trace> классы одного и того же **прослушиватели** коллекции.</span><span class="sxs-lookup"><span data-stu-id="ca35d-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="ca35d-131">Если добавить объект прослушивателя в коллекцию в одном из этих классов, другой класс использует этот же прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="ca35d-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="ca35d-132">Классы прослушивателя, поставлявшихся с .NET Framework являются производными от <xref:System.Diagnostics.TraceListener> класса.</span><span class="sxs-lookup"><span data-stu-id="ca35d-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ca35d-133">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="ca35d-133">Configuration File</span></span>  
 <span data-ttu-id="ca35d-134">Этот элемент может использоваться в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="ca35d-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca35d-135">Пример</span><span class="sxs-lookup"><span data-stu-id="ca35d-135">Example</span></span>  
 <span data-ttu-id="ca35d-136">В следующем примере показано, как использовать  **\<прослушиватели >** элемент для добавления прослушивателей `MyListener` и `MyEventListener` для **прослушиватели** коллекции.</span><span class="sxs-lookup"><span data-stu-id="ca35d-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="ca35d-137">`MyListener` Создает файл с именем `MyListener.log` и записывает выходные данные в файл.</span><span class="sxs-lookup"><span data-stu-id="ca35d-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="ca35d-138">`MyEventListener` создает запись в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="ca35d-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca35d-139">См. также</span><span class="sxs-lookup"><span data-stu-id="ca35d-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ca35d-140">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="ca35d-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
