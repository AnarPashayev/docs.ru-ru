---
title: Метод IMetaDataImport2::GetPEKind
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91c80566ed284403ad559583a1e4f1025eb09985
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755315"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="647fc-102">Метод IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="647fc-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="647fc-103">Получает значение, идентифицирующее природу кода в переносимый исполняемый файл (PE) файла, обычно файл DLL или EXE-файла, который определен в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="647fc-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647fc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="647fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="647fc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="647fc-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="647fc-106">[out] Указатель на значение [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) перечисление, описывающее PE-файла.</span><span class="sxs-lookup"><span data-stu-id="647fc-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="647fc-107">[out] Указатель на значение, идентифицирующее архитектуры компьютера.</span><span class="sxs-lookup"><span data-stu-id="647fc-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="647fc-108">Возможные значения см.</span><span class="sxs-lookup"><span data-stu-id="647fc-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="647fc-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="647fc-109">Remarks</span></span>  
 <span data-ttu-id="647fc-110">Значение, найденное по `pdwMachine` параметр может принимать одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="647fc-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="647fc-111">Значение</span><span class="sxs-lookup"><span data-stu-id="647fc-111">Value</span></span>|<span data-ttu-id="647fc-112">Архитектура компьютера</span><span class="sxs-lookup"><span data-stu-id="647fc-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="647fc-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="647fc-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="647fc-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="647fc-114">0x014C</span></span>|<span data-ttu-id="647fc-115">x86</span><span class="sxs-lookup"><span data-stu-id="647fc-115">x86</span></span>|  
|<span data-ttu-id="647fc-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="647fc-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="647fc-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="647fc-117">0x0200</span></span>|<span data-ttu-id="647fc-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="647fc-118">Intel IPF</span></span>|  
|<span data-ttu-id="647fc-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="647fc-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="647fc-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="647fc-120">0x8664</span></span>|<span data-ttu-id="647fc-121">X64</span><span class="sxs-lookup"><span data-stu-id="647fc-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="647fc-122">Требования</span><span class="sxs-lookup"><span data-stu-id="647fc-122">Requirements</span></span>  
 <span data-ttu-id="647fc-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="647fc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="647fc-124">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="647fc-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="647fc-125">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="647fc-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="647fc-126">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="647fc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647fc-127">См. также</span><span class="sxs-lookup"><span data-stu-id="647fc-127">See also</span></span>

- [<span data-ttu-id="647fc-128">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="647fc-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="647fc-129">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="647fc-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="647fc-130">Перечисление CorPEKind</span><span class="sxs-lookup"><span data-stu-id="647fc-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
