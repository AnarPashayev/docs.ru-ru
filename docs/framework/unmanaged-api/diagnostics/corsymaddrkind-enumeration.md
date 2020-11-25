---
title: Перечисление CorSymAddrKind
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: f71d8956e8706cdc71b94b6e6e2e8210e5b9161e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725239"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="f1627-102">Перечисление CorSymAddrKind</span><span class="sxs-lookup"><span data-stu-id="f1627-102">CorSymAddrKind Enumeration</span></span>

<span data-ttu-id="f1627-103">Указывает тип адреса памяти.</span><span class="sxs-lookup"><span data-stu-id="f1627-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1627-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1627-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="f1627-105">Члены</span><span class="sxs-lookup"><span data-stu-id="f1627-105">Members</span></span>  
  
|<span data-ttu-id="f1627-106">Член</span><span class="sxs-lookup"><span data-stu-id="f1627-106">Member</span></span>|<span data-ttu-id="f1627-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f1627-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="f1627-108">Указывает локальную переменную или индекс параметра промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="f1627-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="f1627-109">Указывает относительный виртуальный адрес в модуле.</span><span class="sxs-lookup"><span data-stu-id="f1627-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="f1627-110">Указывает регистр ЦП.</span><span class="sxs-lookup"><span data-stu-id="f1627-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="f1627-111">Указывает, что первый адрес является регистром, а второй — смещением.</span><span class="sxs-lookup"><span data-stu-id="f1627-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="f1627-112">Указывает смещение от базового адреса.</span><span class="sxs-lookup"><span data-stu-id="f1627-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="f1627-113">Указывает, что первый адрес является нижней частью регистра, а второй адрес — верхней частью.</span><span class="sxs-lookup"><span data-stu-id="f1627-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="f1627-114">Указывает, что первый адрес является нижней частью регистра, второй — верхней частью, а третья — смещением.</span><span class="sxs-lookup"><span data-stu-id="f1627-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="f1627-115">Указывает, что первый адрес является регистром, второй — смещением, а третье — старшая часть регистра.</span><span class="sxs-lookup"><span data-stu-id="f1627-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="f1627-116">Указывает, что первым адресом является начало поля, а вторым адресом является длина поля.</span><span class="sxs-lookup"><span data-stu-id="f1627-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="f1627-117">Указывает, что первый адрес является разделом, а второй — смещением.</span><span class="sxs-lookup"><span data-stu-id="f1627-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1627-118">Требования</span><span class="sxs-lookup"><span data-stu-id="f1627-118">Requirements</span></span>  

 <span data-ttu-id="f1627-119">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f1627-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1627-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f1627-120">See also</span></span>

- [<span data-ttu-id="f1627-121">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="f1627-121">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
