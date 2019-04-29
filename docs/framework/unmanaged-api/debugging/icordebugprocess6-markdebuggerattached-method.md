---
title: Метод ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948607"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="48e97-102">Метод ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="48e97-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="48e97-103">Изменяет внутреннее состояние отлаживаемого кода таким образом, что метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> в библиотеке классов платформы .NET Framework возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="48e97-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e97-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48e97-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48e97-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="48e97-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="48e97-106">`true`, если метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> должен указать, что отладчик присоединен; в противном случае, `false`.</span><span class="sxs-lookup"><span data-stu-id="48e97-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48e97-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="48e97-107">Return Value</span></span>  
 <span data-ttu-id="48e97-108">Метод может возвращать значения, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="48e97-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="48e97-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="48e97-109">Return value</span></span>|<span data-ttu-id="48e97-110">Описание</span><span class="sxs-lookup"><span data-stu-id="48e97-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="48e97-111">Отлаживаемый объект успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="48e97-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="48e97-112">Сборка, содержащая метод <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>, не загружена, или другие ошибки, например, отсутствующие метаданные не позволяют ее распознать.</span><span class="sxs-lookup"><span data-stu-id="48e97-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="48e97-113">Эта ошибка является общей и носит информационный характер.</span><span class="sxs-lookup"><span data-stu-id="48e97-113">This error is common and benign.</span></span> <span data-ttu-id="48e97-114">Метод следует вызвать снова при загрузке дополнительных сборок.</span><span class="sxs-lookup"><span data-stu-id="48e97-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="48e97-115">Другие ошибочные значения `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="48e97-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="48e97-116">Скорее всего, другие значения указывают некорректно работающие компоненты отладчика или компилятора.</span><span class="sxs-lookup"><span data-stu-id="48e97-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e97-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="48e97-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48e97-118">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="48e97-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e97-119">Требования</span><span class="sxs-lookup"><span data-stu-id="48e97-119">Requirements</span></span>  
 <span data-ttu-id="48e97-120">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e97-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e97-121">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48e97-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48e97-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e97-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e97-123">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e97-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e97-124">См. также</span><span class="sxs-lookup"><span data-stu-id="48e97-124">See also</span></span>

- [<span data-ttu-id="48e97-125">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="48e97-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="48e97-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="48e97-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
