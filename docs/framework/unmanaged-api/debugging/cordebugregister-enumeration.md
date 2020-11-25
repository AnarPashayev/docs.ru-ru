---
title: Перечисление CorDebugRegister
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 85df98e83396c9439c28dd41a3ffa02b820c9c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726058"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="c4018-102">Перечисление CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="c4018-102">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="c4018-103">Указывает регистры, связанные с данной архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="c4018-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4018-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4018-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="c4018-105">Члены</span><span class="sxs-lookup"><span data-stu-id="c4018-105">Members</span></span>  
  
|<span data-ttu-id="c4018-106">Член</span><span class="sxs-lookup"><span data-stu-id="c4018-106">Member</span></span>|<span data-ttu-id="c4018-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c4018-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="c4018-108">Регистр указателя инструкции на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="c4018-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="c4018-109">Регистр указателя стека на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="c4018-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="c4018-110">Регистр указателя кадра на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="c4018-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="c4018-111">Регистр указателя инструкции на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="c4018-112">Регистр указателя стека на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="c4018-113">Регистр базового указателя на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="c4018-114">Регистр данных A на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="c4018-115">Регистр данных C на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="c4018-116">Регистр данных D на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="c4018-117">Регистр данных B на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="c4018-118">Регистр индекса источника на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="c4018-119">Регистр индекса назначения на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="c4018-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="c4018-120">Нулевой регистр стека на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="c4018-121">Регистр стека #1 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="c4018-122">Регистр стека #2 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="c4018-123">Регистр стека #3 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="c4018-124">Регистр стека #4 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="c4018-125">Регистр стека #5 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="c4018-126">Регистр стека #6 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="c4018-127">Регистр стека #7 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="c4018-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="c4018-128">Регистр указателя инструкции на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="c4018-129">Регистр указателя стека на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="c4018-130">Регистр базового указателя на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="c4018-131">Регистр данных A на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="c4018-132">Регистр данных C на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="c4018-133">Регистр данных D на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="c4018-134">Регистр данных B на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="c4018-135">Регистр индекса источника на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="c4018-136">Регистр индекса назначения на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="c4018-137">Регистр данных #8 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="c4018-138">Регистр данных #9 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="c4018-139">Регистр данных #10 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="c4018-140">Регистр данных #11 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="c4018-141">Регистр данных #12 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="c4018-142">Регистр данных #13 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="c4018-143">Регистр данных #14 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="c4018-144">Регистр данных #15 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="c4018-145">Регистр мультимедиа #0 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="c4018-146">Регистр мультимедиа #1 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="c4018-147">Регистр мультимедиа #2 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="c4018-148">Регистр мультимедиа #3 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="c4018-149">Регистр мультимедиа #4 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="c4018-150">Регистр мультимедиа #5 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="c4018-151">Регистр мультимедиа #6 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="c4018-152">Регистр мультимедиа #7 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="c4018-153">Регистр мультимедиа #8 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="c4018-154">Регистр мультимедиа #9 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="c4018-155">Регистр мультимедиа #10 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="c4018-156">Регистр мультимедиа #11 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="c4018-157">Регистр мультимедиа #12 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="c4018-158">Регистр мультимедиа #13 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="c4018-159">Регистр мультимедиа #14 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="c4018-160">Регистр мультимедиа #15 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="c4018-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="c4018-161">Регистр указателя стека на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4018-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="c4018-162">Регистр данных #0 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4018-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="c4018-163">Регистр данных с плавающей запятой #0 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4018-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="c4018-164">Регистр счетчика команд (R15) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="c4018-165">Регистр указателя стека (R13) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="c4018-166">Регистр данных R0 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="c4018-167">Регистр данных R1 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="c4018-168">Регистр данных R2 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="c4018-169">Регистр данных R3 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="c4018-170">Регистр R4 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="c4018-171">Регистр R5 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="c4018-172">Регистр R6 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="c4018-173">Регистр R7 (указатель кадра THUMB) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="c4018-174">Регистр R8 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="c4018-175">Регистр R9 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="c4018-176">Регистр R10 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="c4018-177">Указатель кадра на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="c4018-178">Регистр R12 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="c4018-179">Регистр связи (R14) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="c4018-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4018-180">Комментарии</span><span class="sxs-lookup"><span data-stu-id="c4018-180">Remarks</span></span>  

 <span data-ttu-id="c4018-181">На процессоре IA-64 имеются 128 регистров данных общего назначения и 128 регистров данных с плавающей запятой, но используются только значения `REGISTER_IA64_R0` и `REGISTER_IA64_F0`.</span><span class="sxs-lookup"><span data-stu-id="c4018-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="c4018-182">Другие значения можно определить следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4018-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="c4018-183">Добавьте номер регистра к `REGISTER_IA64_R0` для значений от `REGISTER_IA64_R1` до `REGISTER_IA64_R127`, которые соответствуют регистрам данных от #1 до #127 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4018-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="c4018-184">Добавьте номер регистра к `REGISTER_IA64_F0` для значений от `REGISTER_IA64_F1` до `REGISTER_IA64_F127`, которые соответствуют регистрам данных с плавающей запятой от #1 до #127 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4018-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="c4018-185">Например, если необходимо указать регистр данных #83 на процессоре IA-64, добавьте к `REGISTER_IA64_R0` число 83.</span><span class="sxs-lookup"><span data-stu-id="c4018-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4018-186">Требования</span><span class="sxs-lookup"><span data-stu-id="c4018-186">Requirements</span></span>  

 <span data-ttu-id="c4018-187">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-187">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4018-188">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4018-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4018-189">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4018-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4018-190">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4018-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4018-191">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c4018-191">See also</span></span>

- [<span data-ttu-id="c4018-192">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="c4018-192">Debugging Enumerations</span></span>](debugging-enumerations.md)
