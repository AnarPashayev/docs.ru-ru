---
title: Метод IMetaDataImport::GetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729217"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="4f4fc-102">Метод IMetaDataImport::GetRVA</span><span class="sxs-lookup"><span data-stu-id="4f4fc-102">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="4f4fc-103">Возвращает относительный виртуальный адрес (RVA) и флаги реализации метода или поля, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f4fc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4f4fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f4fc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4f4fc-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="4f4fc-106">окне Токен метаданных MethodDef или FieldDef, представляющий объект кода, для которого возвращается RVA.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="4f4fc-107">Если токен является FieldDef, поле должно быть глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="4f4fc-108">заполняет Указатель на относительный виртуальный адрес объекта кода, представленного токеном.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="4f4fc-109">заполняет Указатель на флаги реализации для метода.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="4f4fc-110">Это значение является битовой маской из перечисления [кормесодимпл](cormethodimpl-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4f4fc-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="4f4fc-111">Значение `pdwImplFlags` допустимо только в том случае `tk` , если является токеном MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4f4fc-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f4fc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="4f4fc-112">Requirements</span></span>  

 <span data-ttu-id="4f4fc-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f4fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f4fc-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4f4fc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f4fc-115">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f4fc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f4fc-116">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f4fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f4fc-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4f4fc-117">See also</span></span>

- [<span data-ttu-id="4f4fc-118">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4f4fc-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4f4fc-119">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4f4fc-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
