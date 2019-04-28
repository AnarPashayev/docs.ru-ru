---
title: Элемент <system.codedom>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674804"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="4e66c-102">\<System.CodeDom > элемент</span><span class="sxs-lookup"><span data-stu-id="4e66c-102">\<system.codedom> Element</span></span>
<span data-ttu-id="4e66c-103">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="4e66c-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="4e66c-104">\<Конфигурация > элемент</span><span class="sxs-lookup"><span data-stu-id="4e66c-104">\<configuration> Element</span></span>  
<span data-ttu-id="4e66c-105">\<System.CodeDom > элемент</span><span class="sxs-lookup"><span data-stu-id="4e66c-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e66c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e66c-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e66c-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4e66c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4e66c-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4e66c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e66c-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4e66c-109">Attributes</span></span>  
 <span data-ttu-id="4e66c-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4e66c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e66c-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4e66c-111">Child Elements</span></span>  
  
|<span data-ttu-id="4e66c-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="4e66c-112">Element</span></span>|<span data-ttu-id="4e66c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4e66c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e66c-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="4e66c-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="4e66c-115">Контейнер для элементов конфигурации компилятора; содержит ноль элементов [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) или несколько.</span><span class="sxs-lookup"><span data-stu-id="4e66c-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e66c-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4e66c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4e66c-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="4e66c-117">Element</span></span>|<span data-ttu-id="4e66c-118">Описание</span><span class="sxs-lookup"><span data-stu-id="4e66c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e66c-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4e66c-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="4e66c-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e66c-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e66c-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="4e66c-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="4e66c-122">.NET framework версии 2.0</span><span class="sxs-lookup"><span data-stu-id="4e66c-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="4e66c-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) элемент содержит параметры конфигурации компилятора для поставщиков языков, установленных на компьютере помимо поставщиков по умолчанию, которые устанавливаются вместе с .NET Framework, такие как <xref:Microsoft.CSharp.CSharpCodeProvider> и <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="4e66c-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="4e66c-124">[ \<Компиляторы >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) элемент содержит ноль или более [ \<компилятора >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="4e66c-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="4e66c-125">Каждый [ \<компилятора >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4e66c-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="4e66c-126">Разработчики и поставщики компиляторов можно добавить параметры конфигурации в файле конфигурации компьютера (Machine.config) для нового <xref:System.CodeDom.Compiler.CodeDomProvider> реализации.</span><span class="sxs-lookup"><span data-stu-id="4e66c-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="4e66c-127">Используйте <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> метод программно перечислить поставщиков языков по умолчанию и поставщиков языков, идентифицируемый параметры конфигурации компилятора на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4e66c-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e66c-128">В .NET Framework версии 1.0 и 1.1, язык по умолчанию, поставщиков, предоставляемых платформой .NET Framework, определяются в [ \<компиляторы >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="4e66c-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="4e66c-129">В платформе .NET Framework версии 2.0 языка по умолчанию поставщики не распознаются в [ \<компиляторы >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) элемент, но могут быть перечислены с помощью <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="4e66c-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="4e66c-130">.NET framework версий 1.0 и 1.1</span><span class="sxs-lookup"><span data-stu-id="4e66c-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="4e66c-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) элемент содержит параметры конфигурации компилятора для поставщиков языков на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4e66c-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="4e66c-132">[ \<Компиляторы >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) элемент содержит ноль или более [ \<компилятора >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="4e66c-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="4e66c-133">Каждый [ \<компилятора >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4e66c-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="4e66c-134">В .NET Framework начальные параметры компилятора определены файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4e66c-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="4e66c-135">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="4e66c-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="4e66c-136">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4e66c-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4e66c-137">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="4e66c-137">Configuration File</span></span>  
 <span data-ttu-id="4e66c-138">Этот элемент может использоваться в файле конфигурации компьютера и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="4e66c-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e66c-139">Пример</span><span class="sxs-lookup"><span data-stu-id="4e66c-139">Example</span></span>  
 <span data-ttu-id="4e66c-140">В следующем примере показано типичная конфигурация компилятора.</span><span class="sxs-lookup"><span data-stu-id="4e66c-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e66c-141">См. также</span><span class="sxs-lookup"><span data-stu-id="4e66c-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="4e66c-142">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="4e66c-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4e66c-143">Схема параметров компилятора и поставщика языков</span><span class="sxs-lookup"><span data-stu-id="4e66c-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="4e66c-144">Элемент \<compiler></span><span class="sxs-lookup"><span data-stu-id="4e66c-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
