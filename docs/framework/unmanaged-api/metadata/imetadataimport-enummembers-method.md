---
title: Метод IMetaDataImport::EnumMembers
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492063"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="d056a-102">Метод IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="d056a-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="d056a-103">Перечисляет токены MemberDef, представляющие члены указанного типа.</span><span class="sxs-lookup"><span data-stu-id="d056a-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d056a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d056a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d056a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d056a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d056a-106">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="d056a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="d056a-107">окне Токен TypeDef, представляющий тип, элементы которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="d056a-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="d056a-108">заполняет Массив, используемый для хранения маркеров Мембердеф.</span><span class="sxs-lookup"><span data-stu-id="d056a-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d056a-109">[in] Максимальный размер массива `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="d056a-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d056a-110">заполняет Фактическое число токенов Мембердеф, возвращаемых в `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="d056a-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d056a-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d056a-111">Return Value</span></span>  
  
|<span data-ttu-id="d056a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d056a-112">HRESULT</span></span>|<span data-ttu-id="d056a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d056a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d056a-114">`EnumMembers`успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d056a-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d056a-115">Нет токенов Мембердеф для перечисления.</span><span class="sxs-lookup"><span data-stu-id="d056a-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="d056a-116">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="d056a-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d056a-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="d056a-117">Remarks</span></span>  
 <span data-ttu-id="d056a-118">При перечислении коллекций элементов для класса `EnumMembers` возвращает только элементы (поля и методы, но **не** свойства или события), определенные непосредственно в классе.</span><span class="sxs-lookup"><span data-stu-id="d056a-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="d056a-119">Он не возвращает члены, наследуемые классом, даже если класс предоставляет реализацию для этих унаследованных членов.</span><span class="sxs-lookup"><span data-stu-id="d056a-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="d056a-120">Чтобы перечислить унаследованные члены, вызывающий объект должен явно пройти по цепочке наследования.</span><span class="sxs-lookup"><span data-stu-id="d056a-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="d056a-121">Обратите внимание, что правила для цепочки наследования могут различаться в зависимости от языка или компилятора, который выдал исходные метаданные.</span><span class="sxs-lookup"><span data-stu-id="d056a-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="d056a-122">Свойства и события не перечисляются с помощью `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="d056a-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="d056a-123">Чтобы перечислить их, используйте [енумпропертиес](imetadataimport-enumproperties-method.md) или [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="d056a-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d056a-124">Требования</span><span class="sxs-lookup"><span data-stu-id="d056a-124">Requirements</span></span>  
 <span data-ttu-id="d056a-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d056a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d056a-126">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="d056a-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d056a-127">**Библиотека:** Включается в качестве ресурса в библиотеку MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d056a-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d056a-128">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d056a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d056a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="d056a-129">See also</span></span>

- [<span data-ttu-id="d056a-130">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d056a-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d056a-131">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d056a-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
