---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 16bfea37a5742ac5aaaabfacdcf03a2b5bedb6db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819285"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="f22a2-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f22a2-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="f22a2-103">Указывает ли 64-разрядный исполняемый файл или исполняемый файл, помеченный атрибутом [/Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) параметр компилятора поддерживает технологию Address Space макета Randomization (ASLR) с высокой энтропией.</span><span class="sxs-lookup"><span data-stu-id="f22a2-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f22a2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f22a2-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f22a2-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f22a2-105">Arguments</span></span>  
 <span data-ttu-id="f22a2-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f22a2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f22a2-107">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="f22a2-107">Optional.</span></span> <span data-ttu-id="f22a2-108">Параметр — off по умолчанию или если вы укажите `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="f22a2-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="f22a2-109">Параметр — Если вы укажите `-highentropyva` или `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="f22a2-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f22a2-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="f22a2-110">Remarks</span></span>  
 <span data-ttu-id="f22a2-111">Если этот параметр указан, совместимым версиям ядра Windows можно использовать более высокие степени энтропии, когда ядро случайный выбор из своего структуры адресного пространства процесса в рамках ASLR.</span><span class="sxs-lookup"><span data-stu-id="f22a2-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="f22a2-112">Если ядро использует более высокие степени энтропии, большее количество адресов может быть выделено для областей памяти как стеки и кучи.</span><span class="sxs-lookup"><span data-stu-id="f22a2-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="f22a2-113">Из-за этого сложнее подобрать расположение определенной области памяти.</span><span class="sxs-lookup"><span data-stu-id="f22a2-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="f22a2-114">При включен этот параметр, целевой исполняемый файл и все модули, на которых она зависит, должен быть способен обработать значения указателя, размер которых превышает 4 гигабайта (ГБ), если эти модули выполняются как 64-разрядных процессов.</span><span class="sxs-lookup"><span data-stu-id="f22a2-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22a2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f22a2-115">See also</span></span>

- [<span data-ttu-id="f22a2-116">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="f22a2-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f22a2-117">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="f22a2-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
