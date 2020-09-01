---
description: -highentropyva (параметры компилятора C#)
title: -highentropyva (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125661"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="0c56b-103">-highentropyva (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="0c56b-103">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="0c56b-104">Параметр компилятора **-highentropyva** сообщает ядру Windows, поддерживает ли указанный исполняемый файл технологию Address Space Layout Randomization (ASLR) с высокой энтропией.</span><span class="sxs-lookup"><span data-stu-id="0c56b-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c56b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c56b-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c56b-106">Аргументы</span><span class="sxs-lookup"><span data-stu-id="0c56b-106">Arguments</span></span>  
 <span data-ttu-id="0c56b-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0c56b-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0c56b-108">Этот параметр указывает, что 64-битный исполняемый файл или исполняемый файл, отмеченный параметром компилятора [-platform:anycpu](./platform-compiler-option.md), поддерживает виртуальное адресное пространство с высокой энтропией.</span><span class="sxs-lookup"><span data-stu-id="0c56b-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="0c56b-109">Этот параметр отключен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0c56b-109">The option is disabled by default.</span></span> <span data-ttu-id="0c56b-110">Чтобы включить его, используйте параметр **-highentropyva+** или **-highentropyva**.</span><span class="sxs-lookup"><span data-stu-id="0c56b-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c56b-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c56b-111">Remarks</span></span>  
 <span data-ttu-id="0c56b-112">Параметр **-highentropyva** позволяет совместимым версиям ядра Windows использовать более высокие степени энтропии во время смешивания структуры адресного пространства процесса в рамках ASLR.</span><span class="sxs-lookup"><span data-stu-id="0c56b-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="0c56b-113">Использование более высоких степеней энтропии означает, что можно выделить больше адресов таким областям памяти, как стеки и кучи.</span><span class="sxs-lookup"><span data-stu-id="0c56b-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="0c56b-114">Из-за этого сложнее подобрать расположение определенной области памяти.</span><span class="sxs-lookup"><span data-stu-id="0c56b-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="0c56b-115">Если указан параметр компилятора **-highentropyva**, целевой исполняемый файл и все модули, от которых он зависит, должны быть способны обработать значения указателя, размер которых превышает 4 гигабайта (ГБ), если они выполняются как 64-разрядный процесс.</span><span class="sxs-lookup"><span data-stu-id="0c56b-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
