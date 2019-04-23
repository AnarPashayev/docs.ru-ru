---
title: Перечисление CorNotificationForTokenMovement
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189434"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="4332c-102">Перечисление CorNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="4332c-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="4332c-103">Указывает уведомления, которые будут отправляться клиенту метаданных API, когда происходит новое сопоставление маркеров.</span><span class="sxs-lookup"><span data-stu-id="4332c-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4332c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4332c-104">Syntax</span></span>  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="4332c-105">Участники</span><span class="sxs-lookup"><span data-stu-id="4332c-105">Members</span></span>  
  
|<span data-ttu-id="4332c-106">Член</span><span class="sxs-lookup"><span data-stu-id="4332c-106">Member</span></span>|<span data-ttu-id="4332c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="4332c-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="4332c-108">Отправить уведомление при `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, или `mdFieldDef` токенов перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="4332c-109">Уведомлять о перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="4332c-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="4332c-110">Не уведомлять о перемещении маркера.</span><span class="sxs-lookup"><span data-stu-id="4332c-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="4332c-111">Уведомлять, если `mdMethodDef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="4332c-112">Уведомлять, если `mdMemberRef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="4332c-113">Уведомлять, если `mdFieldDef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="4332c-114">Уведомлять, если `mdTypeRef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="4332c-115">Уведомлять, если `mdTypeDef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="4332c-116">Уведомлять, если `mdParamDef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="4332c-117">Уведомлять, если `mdInterfaceImpl` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="4332c-118">Уведомлять, если `mdProperty` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="4332c-119">Уведомлять, если `mdEvent` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="4332c-120">Уведомлять, если `mdSignature` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="4332c-121">Уведомлять, если `mdTypeSpec` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="4332c-122">Уведомлять, если `mdCustomAttribute` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="4332c-123">Уведомлять, если `mdSecurityValue` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="4332c-124">Уведомлять, если `mdPermission` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="4332c-125">Уведомлять, если `mdModuleRef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="4332c-126">Уведомлять, если `mdNameSpace` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="4332c-127">Уведомлять, если `mdAssemblyRef` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="4332c-128">Уведомлять, если `mdFile` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="4332c-129">Уведомлять, если `mdExportedType` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="4332c-130">Уведомлять, если `mdManifestResource` маркер перемещения.</span><span class="sxs-lookup"><span data-stu-id="4332c-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4332c-131">Примечания</span><span class="sxs-lookup"><span data-stu-id="4332c-131">Remarks</span></span>  
 <span data-ttu-id="4332c-132">Маркер может быть повторно сопоставлен (которые перемещаются) во время слияния метаданных.</span><span class="sxs-lookup"><span data-stu-id="4332c-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4332c-133">Требования</span><span class="sxs-lookup"><span data-stu-id="4332c-133">Requirements</span></span>  
 <span data-ttu-id="4332c-134">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4332c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4332c-135">**Заголовок.** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4332c-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4332c-136">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4332c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4332c-137">См. также</span><span class="sxs-lookup"><span data-stu-id="4332c-137">See also</span></span>

- [<span data-ttu-id="4332c-138">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="4332c-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
