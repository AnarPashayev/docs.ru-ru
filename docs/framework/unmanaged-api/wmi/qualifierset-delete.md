---
title: Функция QualifierSet_Delete (Справочник по неуправляемым API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798333"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="032df-103">Функция QualifierSet_Delete</span><span class="sxs-lookup"><span data-stu-id="032df-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="032df-104">Удаляет указанный квалификатор по имени.</span><span class="sxs-lookup"><span data-stu-id="032df-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="032df-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="032df-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="032df-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="032df-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="032df-107">окне Этот параметр не используется.</span><span class="sxs-lookup"><span data-stu-id="032df-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="032df-108">окне Указатель на экземпляр [ивбемкуалифиерсет](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="032df-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="032df-109">окне Имя удаляемого квалификатора.</span><span class="sxs-lookup"><span data-stu-id="032df-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="032df-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="032df-110">Return value</span></span>

<span data-ttu-id="032df-111">Следующие значения, возвращаемые этой функцией, определены в файле заголовка *вбемкли. h* , или их можно определить как константы в коде:</span><span class="sxs-lookup"><span data-stu-id="032df-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="032df-112">Константа</span><span class="sxs-lookup"><span data-stu-id="032df-112">Constant</span></span>  |<span data-ttu-id="032df-113">Значение</span><span class="sxs-lookup"><span data-stu-id="032df-113">Value</span></span>  |<span data-ttu-id="032df-114">Описание</span><span class="sxs-lookup"><span data-stu-id="032df-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="032df-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="032df-115">0x80041008</span></span> | <span data-ttu-id="032df-116">Недопустимый параметр `wszName`.</span><span class="sxs-lookup"><span data-stu-id="032df-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="032df-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="032df-117">0x80041016</span></span> | <span data-ttu-id="032df-118">Удаление этого квалификатора недопустимо.</span><span class="sxs-lookup"><span data-stu-id="032df-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="032df-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="032df-119">0x80041002</span></span> | <span data-ttu-id="032df-120">Указанный квалификатор не найден.</span><span class="sxs-lookup"><span data-stu-id="032df-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="032df-121">0</span><span class="sxs-lookup"><span data-stu-id="032df-121">0</span></span> | <span data-ttu-id="032df-122">Вызов функции выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="032df-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="032df-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="032df-123">0x40002</span></span> | <span data-ttu-id="032df-124">Локальное переопределение удалено, и исходный квалификатор из родительского объекта возобновил область.</span><span class="sxs-lookup"><span data-stu-id="032df-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="032df-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="032df-125">Remarks</span></span>

<span data-ttu-id="032df-126">Эта функция создает оболочку для вызова метода [ивбемкуалифиерсет::D удалить](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .</span><span class="sxs-lookup"><span data-stu-id="032df-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="032df-127">Из-за правил распространения квалификаторов определенный квалификатор может быть унаследован от другого объекта и просто переопределен в текущем классе или экземпляре.</span><span class="sxs-lookup"><span data-stu-id="032df-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="032df-128">В этом случае `QualifierSet_Delete` метод сбрасывает квалификатор до исходного наследуемого значения.</span><span class="sxs-lookup"><span data-stu-id="032df-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="032df-129">Функция в этом случае возвращает код `WBEM_S_RESET_TO_DEFAULT`состояния.</span><span class="sxs-lookup"><span data-stu-id="032df-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="032df-130">Требования</span><span class="sxs-lookup"><span data-stu-id="032df-130">Requirements</span></span>  
 <span data-ttu-id="032df-131">**Платформ** См. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="032df-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032df-132">**Заголовок.** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="032df-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="032df-133">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="032df-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032df-134">См. также</span><span class="sxs-lookup"><span data-stu-id="032df-134">See also</span></span>

- [<span data-ttu-id="032df-135">WMI и счетчики производительности (Справочник по неуправляемым интерфейсам API)</span><span class="sxs-lookup"><span data-stu-id="032df-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
