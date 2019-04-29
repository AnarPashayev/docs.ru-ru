---
title: Элемент <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 2f3823265e358976f970cdfa36772d2251894280
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701363"
---
# <a name="assert-element"></a><span data-ttu-id="06631-102">\<Assert > элемент</span><span class="sxs-lookup"><span data-stu-id="06631-102">\<assert> Element</span></span>
<span data-ttu-id="06631-103">Определяет, должно ли выводиться окно сообщения при вызове метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. Кроме того, задает имя файла, в который записываются сообщения.</span><span class="sxs-lookup"><span data-stu-id="06631-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="06631-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="06631-104">\<configuration></span></span>  
<span data-ttu-id="06631-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="06631-105">\<system.diagnostics></span></span>  
<span data-ttu-id="06631-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="06631-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06631-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="06631-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06631-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="06631-108">Attributes and Elements</span></span>  
 <span data-ttu-id="06631-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="06631-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06631-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="06631-110">Attributes</span></span>  
  
|<span data-ttu-id="06631-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="06631-111">Attribute</span></span>|<span data-ttu-id="06631-112">Описание</span><span class="sxs-lookup"><span data-stu-id="06631-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="06631-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="06631-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="06631-114">Указывает, является ли чтобы отобразить окно сообщения при **Debug.Assert** метод, результатом которого является **false**.</span><span class="sxs-lookup"><span data-stu-id="06631-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="06631-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="06631-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="06631-116">Указывает имя файла для записи сообщения, если **Debug.Assert** принимает значение **false**.</span><span class="sxs-lookup"><span data-stu-id="06631-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="06631-117">assertuienabled атрибут</span><span class="sxs-lookup"><span data-stu-id="06631-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="06631-118">Значение</span><span class="sxs-lookup"><span data-stu-id="06631-118">Value</span></span>|<span data-ttu-id="06631-119">Описание</span><span class="sxs-lookup"><span data-stu-id="06631-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="06631-120">Отображает окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="06631-120">Displays the message box.</span></span> <span data-ttu-id="06631-121">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="06631-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="06631-122">Не отображает окно сообщения.</span><span class="sxs-lookup"><span data-stu-id="06631-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06631-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="06631-123">Child Elements</span></span>  
 <span data-ttu-id="06631-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="06631-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06631-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="06631-125">Parent Elements</span></span>  
  
|<span data-ttu-id="06631-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="06631-126">Element</span></span>|<span data-ttu-id="06631-127">Описание</span><span class="sxs-lookup"><span data-stu-id="06631-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="06631-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06631-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="06631-129">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="06631-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06631-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="06631-130">Remarks</span></span>  
 <span data-ttu-id="06631-131">Оба атрибута в  **\<assert >** являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="06631-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="06631-132">Вы можете отключить окон сообщений без указания файла для записи сообщений в, или можно указать файл для записи, что при этом не отключать окна сообщений.</span><span class="sxs-lookup"><span data-stu-id="06631-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06631-133">Пример</span><span class="sxs-lookup"><span data-stu-id="06631-133">Example</span></span>  
 <span data-ttu-id="06631-134">В следующем примере показано, как отключить отображение окон сообщений при вызове **Debug.Assert** и записи сообщений `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="06631-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06631-135">См. также</span><span class="sxs-lookup"><span data-stu-id="06631-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="06631-136">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="06631-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
