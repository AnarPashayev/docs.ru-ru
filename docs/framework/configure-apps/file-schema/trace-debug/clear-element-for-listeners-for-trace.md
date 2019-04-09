---
title: <clear> Элемент для <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 97b18f9d6baa618b0f535955b232e2119c758b11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124895"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="93dc4-102">\<Очистить > элемент для \<прослушиватели > для \<трассировки ></span><span class="sxs-lookup"><span data-stu-id="93dc4-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="93dc4-103">Очищает коллекцию `Listeners` для трассировки.</span><span class="sxs-lookup"><span data-stu-id="93dc4-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="93dc4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="93dc4-104">\<configuration></span></span>  
<span data-ttu-id="93dc4-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="93dc4-105">\<system.diagnostics></span></span>  
<span data-ttu-id="93dc4-106">\<трассировки ></span><span class="sxs-lookup"><span data-stu-id="93dc4-106">\<trace></span></span>  
<span data-ttu-id="93dc4-107">\<прослушиватели ></span><span class="sxs-lookup"><span data-stu-id="93dc4-107">\<listeners></span></span>  
<span data-ttu-id="93dc4-108">\<Очистить ></span><span class="sxs-lookup"><span data-stu-id="93dc4-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93dc4-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="93dc4-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93dc4-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="93dc4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93dc4-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="93dc4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93dc4-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="93dc4-112">Attributes</span></span>  
 <span data-ttu-id="93dc4-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="93dc4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93dc4-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="93dc4-114">Child Elements</span></span>  
 <span data-ttu-id="93dc4-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="93dc4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93dc4-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="93dc4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="93dc4-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="93dc4-117">Element</span></span>|<span data-ttu-id="93dc4-118">Описание</span><span class="sxs-lookup"><span data-stu-id="93dc4-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="93dc4-119">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93dc4-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="93dc4-120">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="93dc4-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="93dc4-121">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="93dc4-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="93dc4-122">Содержит прослушиватели, сбора, хранения и маршрутизации сообщений.</span><span class="sxs-lookup"><span data-stu-id="93dc4-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="93dc4-123">Прослушиватели направляют выходные данные трассировки соответствующему целевому объекту.</span><span class="sxs-lookup"><span data-stu-id="93dc4-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93dc4-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="93dc4-124">Remarks</span></span>  
 <span data-ttu-id="93dc4-125">`<clear>` Элемент удаляет все прослушиватели `Listeners` коллекции для трассировки.</span><span class="sxs-lookup"><span data-stu-id="93dc4-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="93dc4-126">Можно использовать `<clear>` элемент перед использованием `<add>` элемент, чтобы быть уверенным, отсутствуют другие активные прослушиватели в коллекции.</span><span class="sxs-lookup"><span data-stu-id="93dc4-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="93dc4-127">Можно снять `Listeners` коллекцию программно, вызвав <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> метод <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> свойство (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="93dc4-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="93dc4-128">Этот элемент может использоваться в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="93dc4-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93dc4-129">`<clear>` Приводит к удалению <xref:System.Diagnostics.DefaultTraceListener> из `Listeners` коллекции, меняет поведение <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> методы.</span><span class="sxs-lookup"><span data-stu-id="93dc4-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="93dc4-130">Вызов `Assert` или `Fail` метод обычно приводит к отображению окна сообщения.</span><span class="sxs-lookup"><span data-stu-id="93dc4-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="93dc4-131">В окне сообщения тем не менее, не отображается, если <xref:System.Diagnostics.DefaultTraceListener> не находится в `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="93dc4-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93dc4-132">Пример</span><span class="sxs-lookup"><span data-stu-id="93dc4-132">Example</span></span>  
 <span data-ttu-id="93dc4-133">В следующем примере показано, как использовать `<clear>` элемент перед использованием `<add>` элемент, чтобы добавить прослушиватель `console` для `Listeners` коллекции для трассировки.</span><span class="sxs-lookup"><span data-stu-id="93dc4-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="93dc4-134">См. также</span><span class="sxs-lookup"><span data-stu-id="93dc4-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="93dc4-135">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="93dc4-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="93dc4-136">\<Удалить ></span><span class="sxs-lookup"><span data-stu-id="93dc4-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="93dc4-137">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="93dc4-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
