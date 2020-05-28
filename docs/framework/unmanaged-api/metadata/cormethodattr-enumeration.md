---
title: Перечисление CorMethodAttr
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 779a8f88b7521aa4b0a75594552981b41714ee3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007680"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="0e14d-102">Перечисление CorMethodAttr</span><span class="sxs-lookup"><span data-stu-id="0e14d-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="0e14d-103">Содержит значения, описывающие возможности метода.</span><span class="sxs-lookup"><span data-stu-id="0e14d-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e14d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e14d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="0e14d-105">Участники</span><span class="sxs-lookup"><span data-stu-id="0e14d-105">Members</span></span>  
  
|<span data-ttu-id="0e14d-106">Член</span><span class="sxs-lookup"><span data-stu-id="0e14d-106">Member</span></span>|<span data-ttu-id="0e14d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0e14d-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="0e14d-108">Указывает доступ к члену.</span><span class="sxs-lookup"><span data-stu-id="0e14d-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="0e14d-109">Указывает, что элемент не может быть указан.</span><span class="sxs-lookup"><span data-stu-id="0e14d-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="0e14d-110">Указывает, что элемент доступен только для родительского типа.</span><span class="sxs-lookup"><span data-stu-id="0e14d-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="0e14d-111">Указывает, что элемент доступен только для подтипов в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="0e14d-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="0e14d-112">Указывает, что элемент акцессиблися любым пользователем в сборке.</span><span class="sxs-lookup"><span data-stu-id="0e14d-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="0e14d-113">Указывает, что элемент доступен только по типу и подтипам.</span><span class="sxs-lookup"><span data-stu-id="0e14d-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="0e14d-114">Указывает, что член доступен для производных классов и других типов в его сборке.</span><span class="sxs-lookup"><span data-stu-id="0e14d-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="0e14d-115">Указывает, что элемент доступен для всех типов с доступом к области.</span><span class="sxs-lookup"><span data-stu-id="0e14d-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="0e14d-116">Указывает, что член определен как часть типа, а не как член экземпляра.</span><span class="sxs-lookup"><span data-stu-id="0e14d-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="0e14d-117">Указывает, что метод не может быть переопределен.</span><span class="sxs-lookup"><span data-stu-id="0e14d-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="0e14d-118">Указывает, что метод может быть переопределен.</span><span class="sxs-lookup"><span data-stu-id="0e14d-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="0e14d-119">Указывает, что метод скрывается по имени и сигнатуре, а не просто по имени.</span><span class="sxs-lookup"><span data-stu-id="0e14d-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="0e14d-120">Указывает макет виртуальной таблицы.</span><span class="sxs-lookup"><span data-stu-id="0e14d-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="0e14d-121">Указывает, что необходимо повторно использовать слот, используемый для этого метода в виртуальной таблице.</span><span class="sxs-lookup"><span data-stu-id="0e14d-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="0e14d-122">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0e14d-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="0e14d-123">Указывает, что метод всегда получает новый слот в виртуальной таблице.</span><span class="sxs-lookup"><span data-stu-id="0e14d-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="0e14d-124">Указывает, что метод может быть переопределен теми же типами, для которых он является видимым.</span><span class="sxs-lookup"><span data-stu-id="0e14d-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="0e14d-125">Указывает, что метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="0e14d-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="0e14d-126">Указывает, что метод является специальным и что его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="0e14d-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="0e14d-127">Указывает, что реализация метода пересылается с помощью PInvoke.</span><span class="sxs-lookup"><span data-stu-id="0e14d-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="0e14d-128">Указывает, что метод является управляемым методом, экспортированным в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="0e14d-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="0e14d-129">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="0e14d-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="0e14d-130">Указывает, что среда CLR должна проверять кодировку имени метода.</span><span class="sxs-lookup"><span data-stu-id="0e14d-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="0e14d-131">Указывает, что метод имеет связанную с ним безопасность.</span><span class="sxs-lookup"><span data-stu-id="0e14d-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="0e14d-132">Указывает, что метод вызывает другой метод, содержащий код безопасности.</span><span class="sxs-lookup"><span data-stu-id="0e14d-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e14d-133">Требования</span><span class="sxs-lookup"><span data-stu-id="0e14d-133">Requirements</span></span>  
 <span data-ttu-id="0e14d-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e14d-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e14d-135">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="0e14d-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0e14d-136">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e14d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e14d-137">См. также статью</span><span class="sxs-lookup"><span data-stu-id="0e14d-137">See also</span></span>

- [<span data-ttu-id="0e14d-138">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="0e14d-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
