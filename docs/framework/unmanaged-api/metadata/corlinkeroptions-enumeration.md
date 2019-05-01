---
title: Перечисление CorLinkerOptions
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc0554ed89d21607978d059b26c4ad69e59a2d4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045803"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="3b0c3-102">Перечисление CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="3b0c3-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="3b0c3-103">Задает флаги для выбора параметров компоновщика метаданных.</span><span class="sxs-lookup"><span data-stu-id="3b0c3-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b0c3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3b0c3-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="3b0c3-105">Участники</span><span class="sxs-lookup"><span data-stu-id="3b0c3-105">Members</span></span>  
  
|<span data-ttu-id="3b0c3-106">Член</span><span class="sxs-lookup"><span data-stu-id="3b0c3-106">Member</span></span>|<span data-ttu-id="3b0c3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3b0c3-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="3b0c3-108">Закрытые типы и глобальные функции, не сохраняются.</span><span class="sxs-lookup"><span data-stu-id="3b0c3-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="3b0c3-109">Закрытые типы и глобальные функции сохраняются.</span><span class="sxs-lookup"><span data-stu-id="3b0c3-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b0c3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3b0c3-110">Requirements</span></span>  
 <span data-ttu-id="3b0c3-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b0c3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b0c3-112">**Заголовок.** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3b0c3-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3b0c3-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b0c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0c3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3b0c3-114">See also</span></span>

- [<span data-ttu-id="3b0c3-115">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="3b0c3-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
