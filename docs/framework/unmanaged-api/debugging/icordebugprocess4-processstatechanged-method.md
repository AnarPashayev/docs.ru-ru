---
title: Метод ICorDebugProcess4::ProcessStateChanged
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948814"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="88447-102">Метод ICorDebugProcess4::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="88447-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="88447-103">Уведомляет конвейера ICorDebug о том, что внепроцессные отладчик процесс продолжает выполнение отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="88447-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="88447-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="88447-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="88447-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="88447-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="88447-106">[in] Является членом [перечисление CorDebugStateChange](cordebugstatechange-enumeration.md) описывающие изменения в состоянии выполнения процесса.</span><span class="sxs-lookup"><span data-stu-id="88447-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="88447-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="88447-107">Remarks</span></span>

<span data-ttu-id="88447-108">Указанный метод является частью `ICorDebugProcess4` интерфейса и соответствует четвертый слот в таблице виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="88447-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="88447-109">Требования</span><span class="sxs-lookup"><span data-stu-id="88447-109">Requirements</span></span>

 <span data-ttu-id="88447-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88447-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="88447-111">**Заголовок.** Нет</span><span class="sxs-lookup"><span data-stu-id="88447-111">**Header:** None</span></span>

 <span data-ttu-id="88447-112">**Библиотека:** Нет</span><span class="sxs-lookup"><span data-stu-id="88447-112">**Library:** None</span></span>
 
 <span data-ttu-id="88447-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88447-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="88447-114">См. также</span><span class="sxs-lookup"><span data-stu-id="88447-114">See also</span></span>

- [<span data-ttu-id="88447-115">Интерфейс ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="88447-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="88447-116">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="88447-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="88447-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="88447-117">Debugging</span></span>](index.md)