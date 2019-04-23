---
title: Элемент <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 744ef0d9bc58e6a0152dce53c40c24eb5283dc0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130524"
---
# <a name="compilers-element"></a><span data-ttu-id="99ff3-102">\<компиляторы > элемент</span><span class="sxs-lookup"><span data-stu-id="99ff3-102">\<compilers> Element</span></span>
<span data-ttu-id="99ff3-103">Контейнер для элементов конфигурации компилятора; содержит ноль элементов [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) или несколько.</span><span class="sxs-lookup"><span data-stu-id="99ff3-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="99ff3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="99ff3-104">\<configuration></span></span>  
<span data-ttu-id="99ff3-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="99ff3-105">\<system.codedom></span></span>  
<span data-ttu-id="99ff3-106">\<компиляторы > элемент</span><span class="sxs-lookup"><span data-stu-id="99ff3-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ff3-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99ff3-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99ff3-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="99ff3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99ff3-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="99ff3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99ff3-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="99ff3-110">Attributes</span></span>  
 <span data-ttu-id="99ff3-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="99ff3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99ff3-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="99ff3-112">Child Elements</span></span>  
  
|<span data-ttu-id="99ff3-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="99ff3-113">Element</span></span>|<span data-ttu-id="99ff3-114">Описание</span><span class="sxs-lookup"><span data-stu-id="99ff3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99ff3-115">Элемент \<compiler></span><span class="sxs-lookup"><span data-stu-id="99ff3-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="99ff3-116">Задает атрибуты конфигурации компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="99ff3-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99ff3-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="99ff3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="99ff3-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="99ff3-118">Element</span></span>|<span data-ttu-id="99ff3-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="99ff3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99ff3-120">Элемент \<configuration></span><span class="sxs-lookup"><span data-stu-id="99ff3-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="99ff3-121">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99ff3-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="99ff3-122">\<System.CodeDom > элемент</span><span class="sxs-lookup"><span data-stu-id="99ff3-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="99ff3-123">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="99ff3-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ff3-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="99ff3-124">Remarks</span></span>  
 <span data-ttu-id="99ff3-125">[ \<Компиляторы >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) элемент содержит параметры конфигурации компилятора для поставщиков языков на компьютере.</span><span class="sxs-lookup"><span data-stu-id="99ff3-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="99ff3-126">Каждый [ \<компилятора >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="99ff3-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="99ff3-127">.NET Framework определяет начальной компилятора и языковые параметры поставщика в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="99ff3-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="99ff3-128">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99ff3-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="99ff3-129">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="99ff3-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="99ff3-130">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="99ff3-130">Configuration File</span></span>  
 <span data-ttu-id="99ff3-131">Этот элемент может использоваться в файле конфигурации компьютера и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="99ff3-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99ff3-132">Пример</span><span class="sxs-lookup"><span data-stu-id="99ff3-132">Example</span></span>  
 <span data-ttu-id="99ff3-133">В приведенном ниже примере показан типичный элемент конфигурации компилятора.</span><span class="sxs-lookup"><span data-stu-id="99ff3-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99ff3-134">См. также</span><span class="sxs-lookup"><span data-stu-id="99ff3-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="99ff3-135">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="99ff3-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="99ff3-136">Схема параметров компилятора и поставщика языков</span><span class="sxs-lookup"><span data-stu-id="99ff3-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="99ff3-137">Элемент \<compiler></span><span class="sxs-lookup"><span data-stu-id="99ff3-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
