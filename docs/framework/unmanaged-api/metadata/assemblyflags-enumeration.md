---
title: Перечисление AssemblyFlags
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009461"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="2d38d-102">Перечисление AssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="2d38d-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="2d38d-103">Содержит значения, описывающие функции времени выполнения сборки.</span><span class="sxs-lookup"><span data-stu-id="2d38d-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d38d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d38d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2d38d-105">Участники</span><span class="sxs-lookup"><span data-stu-id="2d38d-105">Members</span></span>  
  
|<span data-ttu-id="2d38d-106">Член</span><span class="sxs-lookup"><span data-stu-id="2d38d-106">Member</span></span>|<span data-ttu-id="2d38d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2d38d-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="2d38d-108">Указывает, что экспортированные определения типа являются неявными в файлах, составляющих сборку.</span><span class="sxs-lookup"><span data-stu-id="2d38d-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="2d38d-109">В .NET Framework версиях 1,0 и 1,1 это значение всегда считается установленным.</span><span class="sxs-lookup"><span data-stu-id="2d38d-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="2d38d-110">Указывает, что определения ресурсов являются неявными в файлах, составляющих сборку.</span><span class="sxs-lookup"><span data-stu-id="2d38d-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="2d38d-111">В .NET Framework 1,0 и 1,1 предполагается, что это значение всегда задано.</span><span class="sxs-lookup"><span data-stu-id="2d38d-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="2d38d-112">Указывает, что сборка не может выполняться с другими версиями, если они выполняются в одном домене приложения.</span><span class="sxs-lookup"><span data-stu-id="2d38d-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="2d38d-113">Указывает, что сборка не может выполняться с другими версиями, если они выполняются в одном процессе.</span><span class="sxs-lookup"><span data-stu-id="2d38d-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="2d38d-114">Указывает, что сборка не может выполняться с другими версиями, если они выполняются на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="2d38d-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d38d-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="2d38d-115">Remarks</span></span>  
 <span data-ttu-id="2d38d-116">Значения между 0x0010 и 0x0070 (включительно) используются для описания возможностей параллельной совместимости сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="2d38d-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="2d38d-117">Если ни одно из этих значений не задано, предполагается, что сборка совместима параллельно.</span><span class="sxs-lookup"><span data-stu-id="2d38d-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d38d-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2d38d-118">Requirements</span></span>  
 <span data-ttu-id="2d38d-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d38d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d38d-120">**Заголовок:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d38d-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="2d38d-121">**Библиотека:** Включается в качестве ресурса в библиотеку MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d38d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d38d-122">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d38d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d38d-123">См. также статью</span><span class="sxs-lookup"><span data-stu-id="2d38d-123">See also</span></span>

- [<span data-ttu-id="2d38d-124">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="2d38d-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="2d38d-125">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="2d38d-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
