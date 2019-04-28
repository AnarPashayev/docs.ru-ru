---
title: Элемент <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc26f9721e911e05c5b5d4092be21a4e1191c84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704756"
---
# <a name="supportportability-element"></a><span data-ttu-id="938c7-102">\<supportPortability > элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-102">\<supportPortability> Element</span></span>
<span data-ttu-id="938c7-103">Указывает, что приложение может ссылаться на ту же сборку в двух различных реализациях .NET Framework, отключая поведение по умолчанию, которое рассматривает сборки как эквивалент для переносимости приложения.</span><span class="sxs-lookup"><span data-stu-id="938c7-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="938c7-104">\<Конфигурация > элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-104">\<configuration> Element</span></span>  
<span data-ttu-id="938c7-105">\<Среда выполнения > элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-105">\<runtime> Element</span></span>  
<span data-ttu-id="938c7-106">\<assemblyBinding > элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="938c7-107">\<supportPortability > элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938c7-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="938c7-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="938c7-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="938c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="938c7-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="938c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="938c7-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="938c7-111">Attributes</span></span>  
  
|<span data-ttu-id="938c7-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="938c7-112">Attribute</span></span>|<span data-ttu-id="938c7-113">Описание</span><span class="sxs-lookup"><span data-stu-id="938c7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="938c7-114">PKT</span><span class="sxs-lookup"><span data-stu-id="938c7-114">PKT</span></span>|<span data-ttu-id="938c7-115">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="938c7-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="938c7-116">Указывает токен открытого ключа затрагиваемой сборки в виде строки.</span><span class="sxs-lookup"><span data-stu-id="938c7-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="938c7-117">enabled</span><span class="sxs-lookup"><span data-stu-id="938c7-117">enabled</span></span>|<span data-ttu-id="938c7-118">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="938c7-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="938c7-119">Указывает, следует ли включить поддержку для обеспечения переносимости между реализациями заданной сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="938c7-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="938c7-120">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="938c7-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="938c7-121">Значение</span><span class="sxs-lookup"><span data-stu-id="938c7-121">Value</span></span>|<span data-ttu-id="938c7-122">Описание</span><span class="sxs-lookup"><span data-stu-id="938c7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="938c7-123">true</span><span class="sxs-lookup"><span data-stu-id="938c7-123">true</span></span>|<span data-ttu-id="938c7-124">Включите поддержку для обеспечения переносимости между реализациями заданной сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="938c7-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="938c7-125">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="938c7-125">This is the default.</span></span>|  
|<span data-ttu-id="938c7-126">False</span><span class="sxs-lookup"><span data-stu-id="938c7-126">false</span></span>|<span data-ttu-id="938c7-127">Отключите поддержку переносимости между реализациями заданной сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="938c7-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="938c7-128">Это позволяет приложению иметь ссылки на несколько реализаций заданной сборки.</span><span class="sxs-lookup"><span data-stu-id="938c7-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="938c7-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="938c7-129">Child Elements</span></span>  
 <span data-ttu-id="938c7-130">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="938c7-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="938c7-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="938c7-131">Parent Elements</span></span>  
  
|<span data-ttu-id="938c7-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="938c7-132">Element</span></span>|<span data-ttu-id="938c7-133">Описание</span><span class="sxs-lookup"><span data-stu-id="938c7-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="938c7-134">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="938c7-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="938c7-135">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="938c7-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="938c7-136">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="938c7-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="938c7-137">Примечания</span><span class="sxs-lookup"><span data-stu-id="938c7-137">Remarks</span></span>  
 <span data-ttu-id="938c7-138">Начиная с версии [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], поддержка предоставляется автоматически для приложений, которые можно использовать один из двух реализаций .NET Framework, например либо реализации .NET Framework или .NET Framework для реализации Silverlight.</span><span class="sxs-lookup"><span data-stu-id="938c7-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="938c7-139">Две реализации определенной сборки .NET Framework рассматриваются как эквивалент средством привязки сборок.</span><span class="sxs-lookup"><span data-stu-id="938c7-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="938c7-140">В нескольких сценариях эта функция переносимости приложений вызывает проблемы.</span><span class="sxs-lookup"><span data-stu-id="938c7-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="938c7-141">В этих случаях `<supportPortability>` элемент может использоваться, чтобы отключить эту функцию.</span><span class="sxs-lookup"><span data-stu-id="938c7-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="938c7-142">Одним из таких сценариев — это сборка, ссылки реализации .NET Framework и .NET Framework для реализации Silverlight определенной ссылочной сборки.</span><span class="sxs-lookup"><span data-stu-id="938c7-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="938c7-143">Например конструктор XAML, записанных в Windows Presentation Foundation (WPF) может потребоваться Эталонная реализация оба рабочих стола WPF, для конструктора пользовательского интерфейса и для подмножества WPF, включенный в реализацию Silverlight.</span><span class="sxs-lookup"><span data-stu-id="938c7-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="938c7-144">По умолчанию отдельные ссылки вызывают ошибку компиляции, так как привязка сборки видит две эквивалентные сборки.</span><span class="sxs-lookup"><span data-stu-id="938c7-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="938c7-145">Этот элемент отключает поведение по умолчанию и позволяет завершить компиляцию.</span><span class="sxs-lookup"><span data-stu-id="938c7-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="938c7-146">Чтобы компилятор для передачи информации в логику с привязкой сборки среды CLR, необходимо использовать `/appconfig` параметр компилятора, чтобы указать расположение файла app.config, содержащего данный элемент.</span><span class="sxs-lookup"><span data-stu-id="938c7-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="938c7-147">Пример</span><span class="sxs-lookup"><span data-stu-id="938c7-147">Example</span></span>  
 <span data-ttu-id="938c7-148">В следующем примере включается приложению иметь ссылки на реализации .NET Framework и .NET Framework для реализации Silverlight любой сборки .NET Framework, существующей в обеих реализациях.</span><span class="sxs-lookup"><span data-stu-id="938c7-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="938c7-149">`/appconfig` Необходимо использовать параметр компилятора, чтобы указать расположение этого файла app.config.</span><span class="sxs-lookup"><span data-stu-id="938c7-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="938c7-150">См. также</span><span class="sxs-lookup"><span data-stu-id="938c7-150">See also</span></span>

- [<span data-ttu-id="938c7-151">/ appconfig (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="938c7-151">/appconfig (C# Compiler Options)</span></span>](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="938c7-152">[Общие сведения об унификации сборок .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="938c7-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
