---
title: Метод IMetaDataDispenser::OpenScopeOnMemory
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 732ec6cbb2158037252bc2ea4bf406f47f11da9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216630"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="7fbbb-102">Метод IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="7fbbb-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="7fbbb-103">Откроется область памяти, содержащую существующие метаданные.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="7fbbb-104">То есть этот метод открывает указанную область памяти, в которой существующие данные интерпретируются как метаданные.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fbbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7fbbb-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fbbb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7fbbb-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="7fbbb-107">[in] Указатель, который указывает начальный адрес области памяти.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7fbbb-108">[in] Размер области памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7fbbb-109">[in] Значение [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) перечисление для задания режима (чтение, запись и так далее) для открытия.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="7fbbb-110">[in] IID интерфейса новых метаданных должна быть возвращена. вызывающий объект будет использовать интерфейс для импорта (чтение) или выдачи метаданных (запись).</span><span class="sxs-lookup"><span data-stu-id="7fbbb-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="7fbbb-111">Значение `riid` необходимо указать один из интерфейсов «import» или «выдает».</span><span class="sxs-lookup"><span data-stu-id="7fbbb-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="7fbbb-112">Допустимые значения: IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 или IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7fbbb-113">[out] Указатель на возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fbbb-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="7fbbb-114">Remarks</span></span>  
 <span data-ttu-id="7fbbb-115">Копия в памяти метаданных можно запрашивать с помощью методов одного из интерфейсов «импорт», или добавить в методы одного из интерфейсов «выдает».</span><span class="sxs-lookup"><span data-stu-id="7fbbb-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="7fbbb-116">`OpenScopeOnMemory` Метод аналогичен методу [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) метода, за исключением того, что метаданные интерес уже существует в памяти, а не в файле на диске.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="7fbbb-117">Если целевая область памяти не содержит метаданных среды CLR (CLR), `OpenScopeOnMemory` метод завершится с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7fbbb-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fbbb-118">Требования</span><span class="sxs-lookup"><span data-stu-id="7fbbb-118">Requirements</span></span>  
 <span data-ttu-id="7fbbb-119">**Платформа:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fbbb-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fbbb-120">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7fbbb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7fbbb-121">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fbbb-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7fbbb-122">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fbbb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fbbb-123">См. также</span><span class="sxs-lookup"><span data-stu-id="7fbbb-123">See also</span></span>

- [<span data-ttu-id="7fbbb-124">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="7fbbb-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="7fbbb-125">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="7fbbb-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="7fbbb-126">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7fbbb-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="7fbbb-127">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="7fbbb-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7fbbb-128">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7fbbb-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7fbbb-129">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7fbbb-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="7fbbb-130">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7fbbb-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7fbbb-131">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7fbbb-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
