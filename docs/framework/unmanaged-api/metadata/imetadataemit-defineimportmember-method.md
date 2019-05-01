---
title: Метод IMetaDataEmit::DefineImportMember
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81acda4d395563fc8e0000e38036d1aaa0f14471
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043226"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="9c9b9-102">Метод IMetaDataEmit::DefineImportMember</span><span class="sxs-lookup"><span data-stu-id="9c9b9-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="9c9b9-103">Создает ссылку к указанному члену типа или модуль, который определен за пределами текущей области и определяет маркер для этой ссылки.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9b9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c9b9-104">Syntax</span></span>  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c9b9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c9b9-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9c9b9-106">[in] [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) интерфейс, представляющий сборку, из которого импортируется целевому элементу.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9c9b9-107">[in] Массив, содержащий хэш-код для сборки, определяемой параметром `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9c9b9-108">[in] Число байтов в массиве `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="9c9b9-109">[in] [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) интерфейс, который представляет область метаданных, из которого импортируется целевому элементу.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="9c9b9-110">[in] Токен метаданных, указывающее целевой член.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="9c9b9-111">Маркер может быть `mdMethodDef` (для метода-члена), `mdProperty` (для свойства элемента), или `mdFieldDef` (для поля члена) токена.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9c9b9-112">[in] [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) интерфейс, представляющий сборку, в который импортируется целевому элементу.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="9c9b9-113">[in] `mdTypeRef` Или `mdModuleRef` токена для типа или модуля, соответственно, которому принадлежит целевому элементу.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="9c9b9-114">[out] `mdMemberRef` Маркер, который определен в текущей области для ссылки на член.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c9b9-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="9c9b9-115">Remarks</span></span>  
 <span data-ttu-id="9c9b9-116">`DefineImportMember` Метод выполняет поиск элемента, определяемого `mbMember`, который определен в другой области, определяемой `pImport`и извлекает его свойства.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="9c9b9-117">Он использует эти сведения для вызова [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) метод в текущей области, чтобы создать ссылку на элемент.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="9c9b9-118">Как правило, прежде чем использовать `DefineImportMember` метод, необходимо создать, в текущей области, ссылка на тип или ссылка на модуль для родительского класса, интерфейса или модуля целевого элемента.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="9c9b9-119">Маркер метаданных для этой ссылки затем передается в `tkParent` аргумент.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="9c9b9-120">Необходимо создать ссылку на родительский объект целевого члена, если она будет разрешена позже компилятора или компоновщика.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="9c9b9-121">Подведение итогов.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-121">To summarize:</span></span>  
  
- <span data-ttu-id="9c9b9-122">Если целевой член является полем или методом, используйте либо [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) или [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) метод, чтобы создать ссылку на тип, в текущей области, для родительский класс члена или родительского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="9c9b9-123">Если целевой член — это глобальная переменная или глобальная функция (то есть не является членом класса или интерфейса), используйте [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) метод для создания ссылки на модуль в текущей области, для родителя элемента модуль.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="9c9b9-124">Если родительский объект целевого члена будет разрешена позже компилятора или компоновщика, то передайте `mdTokenNil` в `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="9c9b9-125">Единственный сценарий, в котором применяется при глобальной функции или глобальной переменной импортируется из OBJ-файле, который в конечном счете будет связан с текущим модулем и слияние метаданных.</span><span class="sxs-lookup"><span data-stu-id="9c9b9-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c9b9-126">Требования</span><span class="sxs-lookup"><span data-stu-id="9c9b9-126">Requirements</span></span>  
 <span data-ttu-id="9c9b9-127">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c9b9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c9b9-128">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c9b9-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c9b9-129">**Библиотека:** Используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c9b9-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c9b9-130">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c9b9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9b9-131">См. также</span><span class="sxs-lookup"><span data-stu-id="9c9b9-131">See also</span></span>

- [<span data-ttu-id="9c9b9-132">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9c9b9-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9c9b9-133">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9c9b9-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
