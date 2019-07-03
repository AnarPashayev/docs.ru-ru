---
title: Peverify.exe (средство PEVerify)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e657b8e2a0a9dbe8db703ce97d41a3767191a26f
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833870"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="76d2c-102">Peverify.exe (средство PEVerify)</span><span class="sxs-lookup"><span data-stu-id="76d2c-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="76d2c-103">Средство PEVerify помогает разработчикам, создающим код на языке CIL — авторам компиляторов, обработчиков скриптов и т. д. — определить, соответствует ли этот код и связанные с ним метаданные требованиям безопасности типов.</span><span class="sxs-lookup"><span data-stu-id="76d2c-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="76d2c-104">Некоторые компиляторы создают проверяемый типобезопасный код только в том случае, если разработчик не применяет определенные языковые конструкции.</span><span class="sxs-lookup"><span data-stu-id="76d2c-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="76d2c-105">При работе с таким компилятором разработчику иногда требуется проверить, сохранена ли в коде безопасность типов.</span><span class="sxs-lookup"><span data-stu-id="76d2c-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="76d2c-106">В этом случае для проверки CIL и метаданных в файлах можно использовать инструмент PEVerify.</span><span class="sxs-lookup"><span data-stu-id="76d2c-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="76d2c-107">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76d2c-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="76d2c-108">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="76d2c-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="76d2c-109">Дополнительные сведения см. в разделе [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="76d2c-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="76d2c-110">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="76d2c-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d2c-111">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76d2c-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="76d2c-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="76d2c-112">Parameters</span></span>  
  
|<span data-ttu-id="76d2c-113">Аргумент</span><span class="sxs-lookup"><span data-stu-id="76d2c-113">Argument</span></span>|<span data-ttu-id="76d2c-114">ОПИСАНИЕ</span><span class="sxs-lookup"><span data-stu-id="76d2c-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="76d2c-115">*filename*</span><span class="sxs-lookup"><span data-stu-id="76d2c-115">*filename*</span></span>|<span data-ttu-id="76d2c-116">Переносимый исполняемый файл (PE-файл), который требуется проверить на корректность CIL и метаданных.</span><span class="sxs-lookup"><span data-stu-id="76d2c-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="76d2c-117">Параметр</span><span class="sxs-lookup"><span data-stu-id="76d2c-117">Option</span></span>|<span data-ttu-id="76d2c-118">ОПИСАНИЕ</span><span class="sxs-lookup"><span data-stu-id="76d2c-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="76d2c-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="76d2c-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="76d2c-120">Прекращает проверку, если число ошибок в файле достигло значения параметра *maxErrorCount*.</span><span class="sxs-lookup"><span data-stu-id="76d2c-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="76d2c-121">Этот параметр не поддерживается в .NET Framework 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="76d2c-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="76d2c-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="76d2c-122">**/clock**</span></span>|<span data-ttu-id="76d2c-123">Измеряет и выводит значения времени следующих проверок (в миллисекундах):</span><span class="sxs-lookup"><span data-stu-id="76d2c-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="76d2c-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="76d2c-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="76d2c-125">Цикл проверки метаданных</span><span class="sxs-lookup"><span data-stu-id="76d2c-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="76d2c-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="76d2c-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="76d2c-127">Чистое время проверки метаданных</span><span class="sxs-lookup"><span data-stu-id="76d2c-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="76d2c-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="76d2c-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="76d2c-129">Цикл проверки языка CIL</span><span class="sxs-lookup"><span data-stu-id="76d2c-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="76d2c-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="76d2c-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="76d2c-131">Чистое время проверки языка CIL</span><span class="sxs-lookup"><span data-stu-id="76d2c-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="76d2c-132">Значения **MD Val. cycle** и **IL Ver. cycle** включают время, затраченное на необходимые процедуры запуска и завершения проверки.</span><span class="sxs-lookup"><span data-stu-id="76d2c-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="76d2c-133">Значения **MD Val. pure** и **IL Ver pure** отражают время, требуемое только для проверки.</span><span class="sxs-lookup"><span data-stu-id="76d2c-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="76d2c-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="76d2c-134">**/help**</span></span>|<span data-ttu-id="76d2c-135">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="76d2c-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="76d2c-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="76d2c-136">**/hresult**</span></span>|<span data-ttu-id="76d2c-137">Отображает коды ошибок в шестнадцатеричном формате.</span><span class="sxs-lookup"><span data-stu-id="76d2c-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="76d2c-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="76d2c-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="76d2c-139">Игнорирует ошибки с заданными кодами.</span><span class="sxs-lookup"><span data-stu-id="76d2c-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="76d2c-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="76d2c-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="76d2c-141">Игнорирует ошибки с кодами, перечисленными в указанном файле ответов.</span><span class="sxs-lookup"><span data-stu-id="76d2c-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="76d2c-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="76d2c-142">**/il**</span></span>|<span data-ttu-id="76d2c-143">Проверяет безопасность типов CIL для методов, реализованных в сборке, указанной в параметре *filename*.</span><span class="sxs-lookup"><span data-stu-id="76d2c-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="76d2c-144">Если не задан параметр **/quiet**, средство выводит подробное описание всех обнаруженных проблем.</span><span class="sxs-lookup"><span data-stu-id="76d2c-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="76d2c-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="76d2c-145">**/md**</span></span>|<span data-ttu-id="76d2c-146">Проверяет метаданные в сборке, указанной в параметре *filename*.</span><span class="sxs-lookup"><span data-stu-id="76d2c-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="76d2c-147">Средство проверяет всю структуру метаданных в файле и выводит описание всех обнаруженных проблем.</span><span class="sxs-lookup"><span data-stu-id="76d2c-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="76d2c-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="76d2c-148">**/nologo**</span></span>|<span data-ttu-id="76d2c-149">Отключает отображение сведений о версии продукта и авторских правах.</span><span class="sxs-lookup"><span data-stu-id="76d2c-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="76d2c-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="76d2c-150">**/nosymbols**</span></span>|<span data-ttu-id="76d2c-151">В платформе .NET Framework версии 2.0 отключает номера строк для обеспечения обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="76d2c-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="76d2c-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="76d2c-152">**/quiet**</span></span>|<span data-ttu-id="76d2c-153">Задает тихий режим. Отключает вывод сообщений об обнаруженных проблемах.</span><span class="sxs-lookup"><span data-stu-id="76d2c-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="76d2c-154">Средство Peverify.exe все равно уведомляет, соблюдается ли безопасность типов в файле, однако не сообщает об обнаруженных проблемах.</span><span class="sxs-lookup"><span data-stu-id="76d2c-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="76d2c-155">Ограничивает проверку только прозрачными методами.</span><span class="sxs-lookup"><span data-stu-id="76d2c-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="76d2c-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="76d2c-156">**/unique**</span></span>|<span data-ttu-id="76d2c-157">Игнорирует повторяющиеся коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="76d2c-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="76d2c-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="76d2c-158">**/verbose**</span></span>|<span data-ttu-id="76d2c-159">В платформе .NET Framework версии 2.0 отображает дополнительные сведения в сообщениях проверки CIL.</span><span class="sxs-lookup"><span data-stu-id="76d2c-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="76d2c-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="76d2c-160">**/?**</span></span>|<span data-ttu-id="76d2c-161">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="76d2c-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76d2c-162">Примечания</span><span class="sxs-lookup"><span data-stu-id="76d2c-162">Remarks</span></span>  
 <span data-ttu-id="76d2c-163">В среде CLR реализация механизмов безопасности и изоляции основана на типобезопасном выполнении кода приложения.</span><span class="sxs-lookup"><span data-stu-id="76d2c-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="76d2c-164">Обычно код, для которого невозможно [проверить типобезопасность](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security), не выполняется, хотя можно настроить политику безопасности таким образом, чтобы допускалось выполнение доверенного непроверяемого кода.</span><span class="sxs-lookup"><span data-stu-id="76d2c-164">Normally, code that is not [verifiably type safe](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="76d2c-165">Если параметры **/md** и **/il** не заданы, Peverify.exe проверяет как CIL, так и метаданные.</span><span class="sxs-lookup"><span data-stu-id="76d2c-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="76d2c-166">Сначала Peverify.exe проверяет метаданные (параметр **/md**).</span><span class="sxs-lookup"><span data-stu-id="76d2c-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="76d2c-167">Если ошибок нет, выполняется проверка CIL (параметр **/il**).</span><span class="sxs-lookup"><span data-stu-id="76d2c-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="76d2c-168">Если задан и параметр **/md**, и параметр **/il**, проверка по параметру **/il** производится даже при наличии ошибок в метаданных.</span><span class="sxs-lookup"><span data-stu-id="76d2c-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="76d2c-169">Поэтому при отсутствии ошибок в метаданных команда **peverify** *имя_файла* эквивалентна команде **peverify** *имя_файла*  **/md**  **/il**.</span><span class="sxs-lookup"><span data-stu-id="76d2c-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="76d2c-170">Средство Peverify.exe осуществляет полную проверку CIL на основе анализа потоков данных и проверяет правильность метаданных на основе списка из нескольких сотен правил.</span><span class="sxs-lookup"><span data-stu-id="76d2c-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="76d2c-171">Дополнительные сведения о проверках, производимых Peverify.exe, см. в разделах, посвященных спецификации проверки метаданных и спецификации набора инструкций CIL в папке "Tools Developers Guide" в пакете Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="76d2c-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="76d2c-172">Обратите внимание, что в платформе .NET Framework 2.0 или более поздних версий поддерживается возврат проверяемых значений `byref`, заданных с использованием следующих инструкций CIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` и `unbox`.</span><span class="sxs-lookup"><span data-stu-id="76d2c-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76d2c-173">Примеры</span><span class="sxs-lookup"><span data-stu-id="76d2c-173">Examples</span></span>  
 <span data-ttu-id="76d2c-174">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="76d2c-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="76d2c-175">После успешного завершения обработки этого запроса Peverify.exe отображает следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="76d2c-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="76d2c-176">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="76d2c-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="76d2c-177">Средство отображает затраченное на проверку время.</span><span class="sxs-lookup"><span data-stu-id="76d2c-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="76d2c-178">После успешного завершения обработки этого запроса Peverify.exe отображает следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="76d2c-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="76d2c-179">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="76d2c-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="76d2c-180">Однако Peverify.exe останавливается, если число ошибок достигло максимального — то есть 100.</span><span class="sxs-lookup"><span data-stu-id="76d2c-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="76d2c-181">Средство также игнорирует ошибки с заданными кодами.</span><span class="sxs-lookup"><span data-stu-id="76d2c-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="76d2c-182">Следующая команда дает тот же результат, что и команда из предыдущего примера, но коды игнорируемых ошибок извлекаются из файла ответов `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="76d2c-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="76d2c-183">Файл ответов содержит список кодов ошибок, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="76d2c-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="76d2c-184">Ошибки в файле ответов можно также задавать по одной в строке.</span><span class="sxs-lookup"><span data-stu-id="76d2c-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="76d2c-185">См. также</span><span class="sxs-lookup"><span data-stu-id="76d2c-185">See also</span></span>

- [<span data-ttu-id="76d2c-186">Инструменты</span><span class="sxs-lookup"><span data-stu-id="76d2c-186">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="76d2c-187">Написание проверяемого типобезопасного кода</span><span class="sxs-lookup"><span data-stu-id="76d2c-187">Writing Verifiably Type-Safe Code</span></span>](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="76d2c-188">Безопасность типа и безопасность</span><span class="sxs-lookup"><span data-stu-id="76d2c-188">Type Safety and Security</span></span>](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="76d2c-189">Командные строки</span><span class="sxs-lookup"><span data-stu-id="76d2c-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
