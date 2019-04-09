---
title: Перечисление CorOpenFlags
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108525"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="f32df-102">Перечисление CorOpenFlags</span><span class="sxs-lookup"><span data-stu-id="f32df-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="f32df-103">Содержит значения флага, которые управляют поведением метаданных при открытии файлов манифеста.</span><span class="sxs-lookup"><span data-stu-id="f32df-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32df-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f32df-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f32df-105">Участники</span><span class="sxs-lookup"><span data-stu-id="f32df-105">Members</span></span>  
  
|<span data-ttu-id="f32df-106">Член</span><span class="sxs-lookup"><span data-stu-id="f32df-106">Member</span></span>|<span data-ttu-id="f32df-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f32df-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="f32df-108">Указывает, что файл следует открывать только для чтения.</span><span class="sxs-lookup"><span data-stu-id="f32df-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="f32df-109">Указывает, что файл следует открывать для записи.</span><span class="sxs-lookup"><span data-stu-id="f32df-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="f32df-110">При использовании флага `ofWrite` во время открытия файла .WINMD также следует передавать флаг `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="f32df-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="f32df-111">Маска для чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="f32df-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="f32df-112">Указывает, что файл следует считывать в память.</span><span class="sxs-lookup"><span data-stu-id="f32df-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="f32df-113">Метаданным следует создавать свою собственную копию.</span><span class="sxs-lookup"><span data-stu-id="f32df-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="f32df-114">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="f32df-114">Obsolete.</span></span> <span data-ttu-id="f32df-115">Этот флаг отклонен.</span><span class="sxs-lookup"><span data-stu-id="f32df-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="f32df-116">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="f32df-116">Obsolete.</span></span> <span data-ttu-id="f32df-117">Этот флаг отклонен.</span><span class="sxs-lookup"><span data-stu-id="f32df-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="f32df-118">Указывает, что файл должен быть открыт для чтения, а вызов `QueryInterface` для [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) нельзя сделать.</span><span class="sxs-lookup"><span data-stu-id="f32df-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="f32df-119">Указывает, что память была выделена с помощью вызова [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) и будет освобождена метаданными.</span><span class="sxs-lookup"><span data-stu-id="f32df-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="f32df-120">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="f32df-120">Obsolete.</span></span> <span data-ttu-id="f32df-121">Этот флаг отклонен.</span><span class="sxs-lookup"><span data-stu-id="f32df-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="f32df-122">Указывает, что автоматические преобразования из файла .WINMD следует отключить.</span><span class="sxs-lookup"><span data-stu-id="f32df-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="f32df-123">Другими словами, проекцию типа среды выполнения Windows на тип платформы .NET Framework следует отключить.</span><span class="sxs-lookup"><span data-stu-id="f32df-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="f32df-124">Дополнительные сведения см. в разделе [среды выполнения Windows и среда CLR - под представление о внутренней работе с .NET и среды выполнения Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="f32df-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="f32df-125">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="f32df-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="f32df-126">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="f32df-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="f32df-127">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="f32df-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f32df-128">Требования</span><span class="sxs-lookup"><span data-stu-id="f32df-128">Requirements</span></span>  
 <span data-ttu-id="f32df-129">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f32df-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f32df-130">**Заголовок.** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f32df-130">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="f32df-131">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f32df-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f32df-132">См. также</span><span class="sxs-lookup"><span data-stu-id="f32df-132">See also</span></span>

- [<span data-ttu-id="f32df-133">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="f32df-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
