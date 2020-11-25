---
title: Функция QualifierSet_Delete (Справочник по неуправляемым интерфейсам API)
description: Функция QualifierSet_Delete удаляет квалификатор по имени.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721157"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="fbed9-103">Функция QualifierSet_Delete</span><span class="sxs-lookup"><span data-stu-id="fbed9-103">QualifierSet_Delete function</span></span>

<span data-ttu-id="fbed9-104">Удаляет указанный квалификатор по имени.</span><span class="sxs-lookup"><span data-stu-id="fbed9-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fbed9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fbed9-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="fbed9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fbed9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fbed9-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="fbed9-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="fbed9-108">`ptr` окне Указатель на экземпляр [ивбемкуалифиерсет](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="fbed9-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="fbed9-109">`wszName` окне Имя удаляемого квалификатора.</span><span class="sxs-lookup"><span data-stu-id="fbed9-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="fbed9-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fbed9-110">Return value</span></span>

<span data-ttu-id="fbed9-111">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="fbed9-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fbed9-112">Константа</span><span class="sxs-lookup"><span data-stu-id="fbed9-112">Constant</span></span>  |<span data-ttu-id="fbed9-113">Значение</span><span class="sxs-lookup"><span data-stu-id="fbed9-113">Value</span></span>  |<span data-ttu-id="fbed9-114">Описание</span><span class="sxs-lookup"><span data-stu-id="fbed9-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fbed9-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fbed9-115">0x80041008</span></span> | <span data-ttu-id="fbed9-116">Параметр `wszName` является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="fbed9-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="fbed9-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="fbed9-117">0x80041016</span></span> | <span data-ttu-id="fbed9-118">Удаление этого квалификатора недопустимо.</span><span class="sxs-lookup"><span data-stu-id="fbed9-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="fbed9-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="fbed9-119">0x80041002</span></span> | <span data-ttu-id="fbed9-120">Указанный квалификатор не найден.</span><span class="sxs-lookup"><span data-stu-id="fbed9-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fbed9-121">0</span><span class="sxs-lookup"><span data-stu-id="fbed9-121">0</span></span> | <span data-ttu-id="fbed9-122">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="fbed9-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="fbed9-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="fbed9-123">0x40002</span></span> | <span data-ttu-id="fbed9-124">Локальное переопределение удалено, и исходный квалификатор из родительского объекта возобновил область.</span><span class="sxs-lookup"><span data-stu-id="fbed9-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fbed9-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="fbed9-125">Remarks</span></span>

<span data-ttu-id="fbed9-126">Эта функция создает оболочку для вызова метода [ивбемкуалифиерсет::D удалить](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .</span><span class="sxs-lookup"><span data-stu-id="fbed9-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="fbed9-127">Из-за правил распространения квалификаторов определенный квалификатор может быть унаследован от другого объекта и просто переопределен в текущем классе или экземпляре.</span><span class="sxs-lookup"><span data-stu-id="fbed9-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="fbed9-128">В этом случае `QualifierSet_Delete` метод сбрасывает квалификатор до исходного наследуемого значения.</span><span class="sxs-lookup"><span data-stu-id="fbed9-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="fbed9-129">Функция в этом случае возвращает код состояния `WBEM_S_RESET_TO_DEFAULT` .</span><span class="sxs-lookup"><span data-stu-id="fbed9-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbed9-130">Требования</span><span class="sxs-lookup"><span data-stu-id="fbed9-130">Requirements</span></span>  

 <span data-ttu-id="fbed9-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbed9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbed9-132">**Заголовок:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="fbed9-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fbed9-133">**.NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fbed9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbed9-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fbed9-134">See also</span></span>

- [<span data-ttu-id="fbed9-135">WMI и счетчики производительности (справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="fbed9-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
