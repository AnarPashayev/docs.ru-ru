---
title: Перечисление CorRefToDefCheck
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e7ce604acddb88d5a15844cbce2622b21e364cc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706116"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="09955-102">Перечисление CorRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="09955-102">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="09955-103">Задает флаги для элемента управления, на который ссылаются элементы, преобразуемые в их определения для оптимизации кода.</span><span class="sxs-lookup"><span data-stu-id="09955-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09955-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09955-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="09955-105">Члены</span><span class="sxs-lookup"><span data-stu-id="09955-105">Members</span></span>  
  
|<span data-ttu-id="09955-106">Член</span><span class="sxs-lookup"><span data-stu-id="09955-106">Member</span></span>|<span data-ttu-id="09955-107">Описание</span><span class="sxs-lookup"><span data-stu-id="09955-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="09955-108">Указывает, что ссылки на типы и ссылки на элементы должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="09955-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="09955-109">Это значение по умолчанию ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="09955-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="09955-110">Указывает, что все элементы, на которые указывают ссылки, должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="09955-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="09955-111">Указывает, что не нужно преобразовывать элементы, на которые имеются ссылки, в определения.</span><span class="sxs-lookup"><span data-stu-id="09955-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="09955-112">Указывает, что только ссылки на типы должны быть преобразованы в определения типов.</span><span class="sxs-lookup"><span data-stu-id="09955-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="09955-113">Указывает, что только ссылки на элементы должны быть преобразованы в определения.</span><span class="sxs-lookup"><span data-stu-id="09955-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="09955-114">То есть ссылки на элементы должны быть преобразованы в определения методов или определения полей.</span><span class="sxs-lookup"><span data-stu-id="09955-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09955-115">Требования</span><span class="sxs-lookup"><span data-stu-id="09955-115">Requirements</span></span>  

 <span data-ttu-id="09955-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09955-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09955-117">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="09955-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="09955-118">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09955-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09955-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="09955-119">See also</span></span>

- [<span data-ttu-id="09955-120">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="09955-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
