---
title: Встроенные типы для общих примитивов языка XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: feda058a9672a3150f7beb5c1bc124eee1eae9eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689714"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="03815-102">Встроенные типы для общих примитивов языка XAML</span><span class="sxs-lookup"><span data-stu-id="03815-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="03815-103">В XAML 2009 появилась поддержка уровня языка XAML для некоторых типов данных, которые являются часто используемыми примитивами в среде CLR и в других языках программирования.</span><span class="sxs-lookup"><span data-stu-id="03815-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="03815-104">В XAML 2009 добавлена поддержка следующих примитивов: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`и `x:Array`</span><span class="sxs-lookup"><span data-stu-id="03815-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="03815-105">Предыдущие способы использования примитивов языка в разметке XAML</span><span class="sxs-lookup"><span data-stu-id="03815-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="03815-106">В XAML для предыдущих версий WPF можно было ссылаться на примитивы языка среды CLR путем сопоставления сборки и пространства имен, содержащего класс определения примитивов CLR для платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03815-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="03815-107">Большинство из них содержатся в сборке mscorlib и пространстве имен <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="03815-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="03815-108">Например, чтобы использовать <xref:System.Int32>, можно объявить следующее сопоставление (с показанным ниже примером использования):</span><span class="sxs-lookup"><span data-stu-id="03815-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="03815-109">Примитивы языка XAML 2009</span><span class="sxs-lookup"><span data-stu-id="03815-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="03815-110">По соглашению примитивы языка XAML и все остальные элементы языка XAML отображаются с префиксом `x:` .</span><span class="sxs-lookup"><span data-stu-id="03815-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="03815-111">Таким образом, элементы языка XAML обычно используются в реальной разметке.</span><span class="sxs-lookup"><span data-stu-id="03815-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="03815-112">Это соглашение соблюдается в основной документации по XAML в WPF, а также в спецификации XAML.</span><span class="sxs-lookup"><span data-stu-id="03815-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="03815-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="03815-113">x:Object</span></span>  
 <span data-ttu-id="03815-114">Для резервирования CLR примитив `x:Object` соответствует <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="03815-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="03815-115">Этот примитив обычно не используется в разметке приложения, но может быть полезен в некоторых сценариях, таких как проверка возможности назначения в системе типов XAML.</span><span class="sxs-lookup"><span data-stu-id="03815-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="03815-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="03815-116">x:Boolean</span></span>  
 <span data-ttu-id="03815-117">Для резервирования CLR примитив `x:Boolean` соответствует <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="03815-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="03815-118">XAML анализирует значения `x:Boolean` без учета регистра.</span><span class="sxs-lookup"><span data-stu-id="03815-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="03815-119">Обратите внимание, что `x:Bool` не является допустимой альтернативой.</span><span class="sxs-lookup"><span data-stu-id="03815-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="03815-120">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.17 и 5.4.11 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="03815-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="03815-121">x:Char</span></span>  
 <span data-ttu-id="03815-122">Для резервирования CLR примитив `x:Char` соответствует <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="03815-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="03815-123">Строковые и символьные типы взаимодействуют со всей кодировкой файла на уровне XML.</span><span class="sxs-lookup"><span data-stu-id="03815-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="03815-124">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.7 и 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="03815-125">x:String</span><span class="sxs-lookup"><span data-stu-id="03815-125">x:String</span></span>  
 <span data-ttu-id="03815-126">Для резервирования CLR примитив `x:String` соответствует <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="03815-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="03815-127">Строковые и символьные типы взаимодействуют со всей кодировкой файла на уровне XML.</span><span class="sxs-lookup"><span data-stu-id="03815-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="03815-128">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] 5.2.6 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="03815-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="03815-129">x:Decimal</span></span>  
 <span data-ttu-id="03815-130">Для резервирования CLR примитив `x:Decimal` соответствует <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="03815-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="03815-131">Обратите внимание, что анализ XAML по существу выполняется в рамках языка и региональных параметров `en-US` .</span><span class="sxs-lookup"><span data-stu-id="03815-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="03815-132">В рамках языка и региональных параметров `en-US` правильным разделителем компонентов десятичного числа всегда является точка (`.`), независимо от региональных параметров среды разработки или конечного клиентского компьютера, на котором во время выполнения загружается XAML.</span><span class="sxs-lookup"><span data-stu-id="03815-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="03815-133">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.14 и 5.4.8 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="03815-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="03815-134">x:Single</span></span>  
 <span data-ttu-id="03815-135">Для резервирования CLR примитив `x:Single` соответствует <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="03815-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="03815-136">Помимо числовых значений текстовый синтаксис для `x:Single` также позволяет использовать токены `Infinity`, `-Infinity`и `NaN`.</span><span class="sxs-lookup"><span data-stu-id="03815-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="03815-137">Эти токены обрабатываются с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="03815-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="03815-138">`x:Single` может поддерживать значения в экспоненциальном представлении, если первый символ в текстовом синтаксисе `e` или `E`.</span><span class="sxs-lookup"><span data-stu-id="03815-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="03815-139">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.8 и 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="03815-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="03815-140">x:Double</span></span>  
 <span data-ttu-id="03815-141">Для резервирования CLR примитив `x:Double` соответствует <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="03815-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="03815-142">Помимо числовых значений текстовый синтаксис для `x:Double` позволяет использовать токены `Infinity`, `-Infinity`и `NaN`.</span><span class="sxs-lookup"><span data-stu-id="03815-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="03815-143">Эти токены обрабатываются с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="03815-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="03815-144">`x:Double` может поддерживать значения в экспоненциальном представлении.</span><span class="sxs-lookup"><span data-stu-id="03815-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="03815-145">Чтобы представить часть экспоненты, используйте символ `e` или `E` .</span><span class="sxs-lookup"><span data-stu-id="03815-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="03815-146">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.9 и 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="03815-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="03815-147">x:Int16</span></span>  
 <span data-ttu-id="03815-148">Для резервирования CLR примитив `x:Int16` , соответствующий <xref:System.Int16> и `x:Int16` , обрабатывается как имеющий знак.</span><span class="sxs-lookup"><span data-stu-id="03815-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="03815-149">В XAML отсутствие знака плюс (`+`) в текстовом синтаксисе означает положительное значение.</span><span class="sxs-lookup"><span data-stu-id="03815-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="03815-150">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.11 и 5.4.5 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="03815-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="03815-151">x:Int32</span></span>  
 <span data-ttu-id="03815-152">Для резервирования CLR примитив `x:Int32` соответствует <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="03815-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="03815-153">`x:Int32` рассматривается как имеющий знак.</span><span class="sxs-lookup"><span data-stu-id="03815-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="03815-154">В XAML отсутствие знака плюс (`+`) в текстовом синтаксисе означает положительное значение.</span><span class="sxs-lookup"><span data-stu-id="03815-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="03815-155">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.12 и 5.4.6 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="03815-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="03815-156">x:Int64</span></span>  
 <span data-ttu-id="03815-157">Для резервирования CLR примитив `x:Int64` соответствует <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="03815-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="03815-158">`x:Int64` рассматривается как имеющий знак.</span><span class="sxs-lookup"><span data-stu-id="03815-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="03815-159">В XAML отсутствие знака плюс (`+`) в текстовом синтаксисе означает положительное значение.</span><span class="sxs-lookup"><span data-stu-id="03815-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="03815-160">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.13 и 5.4.7 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="03815-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="03815-161">x:TimeSpan</span></span>  
 <span data-ttu-id="03815-162">Для резервирования CLR примитив `x:TimeSpan` соответствует <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="03815-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="03815-163">Обратите внимание, что анализ XAML для формата даты-времени по существу выполняется в рамках языка и региональных параметров `en-US` .</span><span class="sxs-lookup"><span data-stu-id="03815-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="03815-164">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.16 и 5.4.10 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="03815-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="03815-165">x:Uri</span></span>  
 <span data-ttu-id="03815-166">Для резервирования CLR примитив `x:Uri` соответствует <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="03815-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="03815-167">Проверка протоколов не является частью определения XAML для `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="03815-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="03815-168">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.15 и 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="03815-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="03815-169">x:Byte</span></span>  
 <span data-ttu-id="03815-170">Для резервирования CLR примитив `x:Byte` соответствует <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="03815-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="03815-171">Объект <xref:System.Byte>  /  `x:Byte` рассматривается как число без знака.</span><span class="sxs-lookup"><span data-stu-id="03815-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="03815-172">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] разделах 5.2.10 и 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="03815-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="03815-173">x:Array</span></span>  
 <span data-ttu-id="03815-174">Для резервирования CLR примитив `x:Array` соответствует <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="03815-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="03815-175">Можно определить массив в XAML 2006 г. с помощью синтаксиса расширения разметки; однако синтаксис XAML 2009 является определенным языком примитивом, которому не требуется доступ к расширению разметки.</span><span class="sxs-lookup"><span data-stu-id="03815-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="03815-176">Дополнительные сведения о поддержке XAML 2006 см. в разделе [x:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="03815-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="03815-177">Определение спецификации языка XAML см. в разделе [ \[MS-XAML\] 5.2.18 руководства](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="03815-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="03815-178">Поддержка WPF</span><span class="sxs-lookup"><span data-stu-id="03815-178">WPF Support</span></span>  
 <span data-ttu-id="03815-179">В WPF можно использовать возможности XAML 2009, но только для XAML, не скомпилированного с разметкой.</span><span class="sxs-lookup"><span data-stu-id="03815-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="03815-180">Скомпилированный с разметкой XAML и форма BAML кода XAML в настоящее время не поддерживают ключевые слова и компоненты XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="03815-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="03815-181">Сценарий, где можно использовать возможности XAML 2009 вместе с WPF, если разработчик выпустил свободный XAML, а вы затем загрузили этот XAML в среду выполнения WPF и граф объектов с <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03815-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="03815-182"><xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF и его <xref:System.Windows.Markup.XamlReader.Load%2A> может обрабатывать ключевые слова языка XAML 2009 и компоненты в правильное представление графа объектов.</span><span class="sxs-lookup"><span data-stu-id="03815-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
