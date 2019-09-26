---
title: Структура COR_HEAPOBJECT
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274037"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="9a58d-102">Структура COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="9a58d-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="9a58d-103">Предоставляет сведения об объекте, находящемся в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="9a58d-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a58d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a58d-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="9a58d-105">Участники</span><span class="sxs-lookup"><span data-stu-id="9a58d-105">Members</span></span>  
  
|<span data-ttu-id="9a58d-106">Член</span><span class="sxs-lookup"><span data-stu-id="9a58d-106">Member</span></span>|<span data-ttu-id="9a58d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="9a58d-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="9a58d-108">Адрес объекта в памяти.</span><span class="sxs-lookup"><span data-stu-id="9a58d-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="9a58d-109">Общий размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="9a58d-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="9a58d-110">Токен [COR_TYPEID](cor-typeid-structure.md) , представляющий тип объекта.</span><span class="sxs-lookup"><span data-stu-id="9a58d-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a58d-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="9a58d-111">Remarks</span></span>  
 <span data-ttu-id="9a58d-112">`COR_HEAPOBJECT`экземпляры можно получить, перечисляя объект интерфейса [икордебугхеапенум](icordebugheapenum-interface.md) , который заполняется путем вызова метода [метод ICorDebugProcess5:: енумератехеап](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a58d-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="9a58d-113">`COR_HEAPOBJECT` Экземпляр предоставляет сведения об активном объекте в управляемой куче или об объекте, который не является корневым для какого-либо объекта, но еще не был собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="9a58d-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="9a58d-114">Для повышения производительности `COR_HEAPOBJECT.address` поле `CORDB_ADDRESS` является значением, а не значением интерфейса ICorDebugValue, которое используется в большинстве API отладки.</span><span class="sxs-lookup"><span data-stu-id="9a58d-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="9a58d-115">Чтобы получить объект ICorDebugValue для заданного адреса объекта, можно передать `CORDB_ADDRESS` значение в метод [метод ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a58d-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="9a58d-116">Для повышения производительности `COR_HEAPOBJECT.type` поле `COR_TYPEID` является значением, а не значением интерфейса ICorDebugType, которое используется в большинстве API отладки.</span><span class="sxs-lookup"><span data-stu-id="9a58d-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="9a58d-117">Чтобы получить объект ICorDebugType для заданного идентификатора типа, можно передать `COR_TYPEID` значение в метод [метод ICorDebugProcess5:: жеттипефортипеид](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a58d-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="9a58d-118">Структура `COR_HEAPOBJECT` включает в себя COM-интерфейс, подсчитанный по ссылке.</span><span class="sxs-lookup"><span data-stu-id="9a58d-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="9a58d-119">При извлечении `COR_HEAPOBJECT` экземпляра из перечислителя путем вызова метода [икордебугхеапенум:: Next](icordebugheapenum-next-method.md) необходимо впоследствии освободить ссылку.</span><span class="sxs-lookup"><span data-stu-id="9a58d-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a58d-120">Требования</span><span class="sxs-lookup"><span data-stu-id="9a58d-120">Requirements</span></span>  
 <span data-ttu-id="9a58d-121">**Платформ** См. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a58d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a58d-122">**Заголовок.** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a58d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a58d-123">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="9a58d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a58d-124">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a58d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a58d-125">См. также</span><span class="sxs-lookup"><span data-stu-id="9a58d-125">See also</span></span>

- [<span data-ttu-id="9a58d-126">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="9a58d-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="9a58d-127">Отладка</span><span class="sxs-lookup"><span data-stu-id="9a58d-127">Debugging</span></span>](index.md)
