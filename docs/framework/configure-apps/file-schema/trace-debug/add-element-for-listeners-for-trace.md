---
title: <add> Элемент для <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089586"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="e122c-102">\<Добавить > элемент для \<прослушиватели > для \<трассировки ></span><span class="sxs-lookup"><span data-stu-id="e122c-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e122c-103">Добавляет прослушиватель **прослушиватели** коллекции.</span><span class="sxs-lookup"><span data-stu-id="e122c-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="e122c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e122c-104">\<configuration></span></span>  
<span data-ttu-id="e122c-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="e122c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e122c-106">\<трассировки ></span><span class="sxs-lookup"><span data-stu-id="e122c-106">\<trace></span></span>  
<span data-ttu-id="e122c-107">\<прослушиватели ></span><span class="sxs-lookup"><span data-stu-id="e122c-107">\<listeners></span></span>  
<span data-ttu-id="e122c-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e122c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e122c-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e122c-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e122c-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e122c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e122c-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e122c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e122c-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e122c-112">Attributes</span></span>  
  
|<span data-ttu-id="e122c-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e122c-113">Attribute</span></span>|<span data-ttu-id="e122c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="e122c-114">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="e122c-115">type</span><span class="sxs-lookup"><span data-stu-id="e122c-115">type</span></span>**|<span data-ttu-id="e122c-116">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e122c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e122c-117">Указывает тип прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="e122c-117">Specifies the type of the listener.</span></span> <span data-ttu-id="e122c-118">Необходимо использовать строку, которая соответствует требованиям, перечисленным в [Указание полных имен типов](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e122c-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|**<span data-ttu-id="e122c-119">initializeData</span><span class="sxs-lookup"><span data-stu-id="e122c-119">initializeData</span></span>**|<span data-ttu-id="e122c-120">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e122c-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e122c-121">Строка, передаваемая в конструктор для заданного класса.</span><span class="sxs-lookup"><span data-stu-id="e122c-121">The string passed to the constructor for the specified class.</span></span>|  
|**<span data-ttu-id="e122c-122">имя</span><span class="sxs-lookup"><span data-stu-id="e122c-122">name</span></span>**|<span data-ttu-id="e122c-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e122c-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e122c-124">Имя прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="e122c-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e122c-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e122c-125">Child Elements</span></span>  
  
|<span data-ttu-id="e122c-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="e122c-126">Element</span></span>|<span data-ttu-id="e122c-127">Описание</span><span class="sxs-lookup"><span data-stu-id="e122c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e122c-128">\<Фильтр ></span><span class="sxs-lookup"><span data-stu-id="e122c-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="e122c-129">Добавляет фильтр к прослушивателю в `Listeners` коллекции трассировки.</span><span class="sxs-lookup"><span data-stu-id="e122c-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e122c-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e122c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e122c-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="e122c-131">Element</span></span>|<span data-ttu-id="e122c-132">Описание</span><span class="sxs-lookup"><span data-stu-id="e122c-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e122c-133">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e122c-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e122c-134">Указывает прослушиватель, который собирает, хранилищ и направляет сообщения.</span><span class="sxs-lookup"><span data-stu-id="e122c-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e122c-135">Прослушиватели направляют выходные данные трассировки соответствующему целевому объекту.</span><span class="sxs-lookup"><span data-stu-id="e122c-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e122c-136">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e122c-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="e122c-137">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="e122c-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e122c-138">Примечания</span><span class="sxs-lookup"><span data-stu-id="e122c-138">Remarks</span></span>  
 <span data-ttu-id="e122c-139"><xref:System.Diagnostics.Debug> И <xref:System.Diagnostics.Trace> классы одного и того же **прослушиватели** коллекции.</span><span class="sxs-lookup"><span data-stu-id="e122c-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="e122c-140">Если добавить объект прослушивателя в коллекцию в одном из этих классов, другой класс использует этот же прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="e122c-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="e122c-141">Прослушиватель классы являются производными от <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="e122c-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="e122c-142">Если вы не укажете `name` атрибут прослушивателя трассировки, <xref:System.Diagnostics.TraceListener.Name%2A> трассировки прослушивателя, по умолчанию используется пустая строка (»»).</span><span class="sxs-lookup"><span data-stu-id="e122c-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="e122c-143">Если у приложения имеется только один прослушиватель, можно добавить его без указания имени и удалите его, указать пустую строку для имени.</span><span class="sxs-lookup"><span data-stu-id="e122c-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="e122c-144">Тем не менее, если у приложения есть несколько прослушивателей, необходимо указать уникальные имена для каждого прослушивателя трассировки, для идентификации и управления ими отдельные прослушиватели трассировки в <xref:System.Diagnostics.Debug.Listeners%2A> и <xref:System.Diagnostics.Trace.Listeners%2A> коллекций.</span><span class="sxs-lookup"><span data-stu-id="e122c-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e122c-145">Добавление более одного прослушивателя трассировки, того же типа и с тем же присвойте приводит только одного прослушивателя этого типа имя, а, добавляемый `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="e122c-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="e122c-146">Тем не менее, можно программно добавить несколько идентичных прослушивателей для `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="e122c-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="e122c-147">Значение для **initializeData** атрибута зависит от типа создании прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="e122c-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="e122c-148">Не все прослушиватели трассировки необходимо указать **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="e122c-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e122c-149">При использовании `initializeData` атрибут, может появиться предупреждение «атрибут «initializeData» не объявлен.» компилятора</span><span class="sxs-lookup"><span data-stu-id="e122c-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="e122c-150">Это предупреждение возникает, так как параметры конфигурации проверяются на соответствие абстрактный базовый класс <xref:System.Diagnostics.TraceListener>, который не распознает `initializeData` атрибута.</span><span class="sxs-lookup"><span data-stu-id="e122c-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="e122c-151">Как правило можно игнорировать это предупреждение для реализации прослушивателя трассировки, имеющих конструктор, принимающий параметр.</span><span class="sxs-lookup"><span data-stu-id="e122c-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="e122c-152">В следующей таблице перечислены прослушиватели трассировки, которые входят в состав .NET Framework и описаны значения их **initializeData** атрибуты.</span><span class="sxs-lookup"><span data-stu-id="e122c-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="e122c-153">Класс прослушивателя трассировки</span><span class="sxs-lookup"><span data-stu-id="e122c-153">Trace listener class</span></span>|<span data-ttu-id="e122c-154">значение атрибута initializeData</span><span class="sxs-lookup"><span data-stu-id="e122c-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-155">`useErrorStream` Значение <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> конструктор.</span><span class="sxs-lookup"><span data-stu-id="e122c-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="e122c-156">Задайте `initializeData` для атрибута "`true`" для записи трассировки и отладки вывода <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" для записи <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e122c-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-157">Имя файла <xref:System.Diagnostics.DelimitedListTraceListener> записывает.</span><span class="sxs-lookup"><span data-stu-id="e122c-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-158">Имя существующего источника журнала событий.</span><span class="sxs-lookup"><span data-stu-id="e122c-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-159">Имя файла, <xref:System.Diagnostics.EventSchemaTraceListener> записывает.</span><span class="sxs-lookup"><span data-stu-id="e122c-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-160">Имя файла, <xref:System.Diagnostics.TextWriterTraceListener> записывает.</span><span class="sxs-lookup"><span data-stu-id="e122c-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e122c-161">Имя файла, <xref:System.Diagnostics.XmlWriterTraceListener> записывает.</span><span class="sxs-lookup"><span data-stu-id="e122c-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e122c-162">Пример</span><span class="sxs-lookup"><span data-stu-id="e122c-162">Example</span></span>  
 <span data-ttu-id="e122c-163">В следующем примере показано, как использовать  **\<Добавить >** элементы для добавления прослушивателей `MyListener` и `MyEventListener` для **прослушиватели** коллекции.</span><span class="sxs-lookup"><span data-stu-id="e122c-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> `MyListener` <span data-ttu-id="e122c-164">Создает файл с именем `MyListener.log` и записывает выходные данные в файл.</span><span class="sxs-lookup"><span data-stu-id="e122c-164">creates a file called `MyListener.log` and writes the output to the file.</span></span> `MyEventListener` <span data-ttu-id="e122c-165">создает запись в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="e122c-165">creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e122c-166">См. также</span><span class="sxs-lookup"><span data-stu-id="e122c-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="e122c-167">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="e122c-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="e122c-168">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="e122c-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
