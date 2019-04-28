---
title: Элемент <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a467599084f01b1a48c95c5e25fb1f869156dffa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673892"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="aa1d6-102">Элемент \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="aa1d6-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="aa1d6-103">Определяет, использует ли среда CLR устаревший 64-разрядный JIT-компилятор для JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="aa1d6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa1d6-104">\<configuration></span></span>  
<span data-ttu-id="aa1d6-105">\<Среда выполнения ></span><span class="sxs-lookup"><span data-stu-id="aa1d6-105">\<runtime></span></span>  
<span data-ttu-id="aa1d6-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="aa1d6-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="aa1d6-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa1d6-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="aa1d6-108">Имя элемента `useLegacyJit` чувствителен к регистру.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa1d6-109">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="aa1d6-109">Attributes and elements</span></span>

<span data-ttu-id="aa1d6-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa1d6-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="aa1d6-111">Attributes</span></span>  
  
| <span data-ttu-id="aa1d6-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="aa1d6-112">Attribute</span></span> | <span data-ttu-id="aa1d6-113">Описание</span><span class="sxs-lookup"><span data-stu-id="aa1d6-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="aa1d6-114">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-114">Required attribute.</span></span><br><br><span data-ttu-id="aa1d6-115">Указывает, использует ли среда выполнения устаревший 64-разрядный компилятор JIT.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="aa1d6-116">атрибут Enabled</span><span class="sxs-lookup"><span data-stu-id="aa1d6-116">enabled attribute</span></span>  
  
| <span data-ttu-id="aa1d6-117">Значение</span><span class="sxs-lookup"><span data-stu-id="aa1d6-117">Value</span></span> | <span data-ttu-id="aa1d6-118">Описание</span><span class="sxs-lookup"><span data-stu-id="aa1d6-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="aa1d6-119">0</span><span class="sxs-lookup"><span data-stu-id="aa1d6-119">0</span></span>     | <span data-ttu-id="aa1d6-120">Среда CLR использует новый 64-разрядных JIT-компилятор, включенных в .NET Framework 4.6 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="aa1d6-121">1</span><span class="sxs-lookup"><span data-stu-id="aa1d6-121">1</span></span>     | <span data-ttu-id="aa1d6-122">Среда CLR использует старого 64-разрядных JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="aa1d6-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="aa1d6-123">Child elements</span></span>

<span data-ttu-id="aa1d6-124">Нет</span><span class="sxs-lookup"><span data-stu-id="aa1d6-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="aa1d6-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="aa1d6-125">Parent elements</span></span>  
  
| <span data-ttu-id="aa1d6-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="aa1d6-126">Element</span></span>         | <span data-ttu-id="aa1d6-127">Описание</span><span class="sxs-lookup"><span data-stu-id="aa1d6-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="aa1d6-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="aa1d6-129">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="aa1d6-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="aa1d6-130">Remarks</span></span>  

<span data-ttu-id="aa1d6-131">Начиная с .NET Framework 4.6, среда CLR использует новый 64-разрядный компилятор для компиляции эту задачу выполняет JIT по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="aa1d6-132">В некоторых случаях это может привести различия в поведении из кода приложения, который был JIT-компиляции в предыдущей версии 64-разрядный компилятор JIT.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="aa1d6-133">Установив `enabled` атрибут `<useLegacyJit>` элемент `1`, можно отключить новый 64-разрядный компилятор JIT и вместо компиляции приложения с помощью устаревший 64-разрядный компилятор JIT.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa1d6-134">`<useLegacyJit>` Элемента влияет на 64-разрядных JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="aa1d6-135">Компиляция с помощью 32-разрядный компилятор JIT не затрагивается.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="aa1d6-136">Вместо настройки файла конфигурации, вы можете включить устаревший 64-разрядный компилятор JIT двумя способами:</span><span class="sxs-lookup"><span data-stu-id="aa1d6-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="aa1d6-137">Настройка переменной среды</span><span class="sxs-lookup"><span data-stu-id="aa1d6-137">Setting an environment variable</span></span>

  <span data-ttu-id="aa1d6-138">Задайте `COMPLUS_useLegacyJit` переменной среды либо `0` (используйте новый 64-разрядный компилятор JIT) или `1` (использовать старые 64-разрядный компилятор JIT):</span><span class="sxs-lookup"><span data-stu-id="aa1d6-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="aa1d6-139">Переменная среды имеет *глобальной области*, что означает, что это влияет на все приложения выполняются на компьютере.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="aa1d6-140">Если задано, его можно переопределить с помощью параметра файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="aa1d6-141">Имя переменной среды не учитывается.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="aa1d6-142">Добавление раздела реестра</span><span class="sxs-lookup"><span data-stu-id="aa1d6-142">Adding a registry key</span></span>

  <span data-ttu-id="aa1d6-143">Вы можете включить устаревший 64-разрядных JIT-компилятор, добавив `REG_DWORD` значение либо `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` или `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` разделом реестра.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="aa1d6-144">Значение называется `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="aa1d6-145">Если значение равно 0, используется новый компилятор.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="aa1d6-146">Если значение равно 1, устаревший 64-разрядный компилятор JIT включен.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="aa1d6-147">Имя значения реестра не учитывается.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="aa1d6-148">Добавление значения к `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ключ влияет на все приложения, работающие на компьютере.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="aa1d6-149">Добавление значения к `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` ключ влияет на все приложения, запустите текущим пользователем.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="aa1d6-150">Если компьютер настроен с несколькими учетными записями, затрагиваются только приложений, выполните текущим пользователем, если только значение добавляется к разделам реестра для других пользователей, а также.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="aa1d6-151">Добавление `<useLegacyJit>` элемент в файл конфигурации переопределяет параметры реестра, если они присутствуют.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1d6-152">Пример</span><span class="sxs-lookup"><span data-stu-id="aa1d6-152">Example</span></span>  

<span data-ttu-id="aa1d6-153">В следующем файле конфигурации отключает компиляцию с помощью нового 64-разрядный компилятор JIT и вместо этого использует устаревший 64-разрядный компилятор JIT.</span><span class="sxs-lookup"><span data-stu-id="aa1d6-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa1d6-154">См. также</span><span class="sxs-lookup"><span data-stu-id="aa1d6-154">See also</span></span>

- [<span data-ttu-id="aa1d6-155">\<Среда выполнения > элемент</span><span class="sxs-lookup"><span data-stu-id="aa1d6-155">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [<span data-ttu-id="aa1d6-156">Элемент \<configuration></span><span class="sxs-lookup"><span data-stu-id="aa1d6-156">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [<span data-ttu-id="aa1d6-157">Устранение рисков. Новый 64-разрядный JIT-компилятор</span><span class="sxs-lookup"><span data-stu-id="aa1d6-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
