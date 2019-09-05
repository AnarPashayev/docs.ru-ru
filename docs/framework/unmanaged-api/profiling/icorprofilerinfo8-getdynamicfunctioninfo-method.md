---
title: 'ICorProfilerInfo8:: Жетдинамикфунктионинфо'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 45a40d49cea2dd5f881fbd47cc2fb4bd96e8f9ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243987"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="b3c9b-102">Метод ICorProfilerInfo8:: Жетдинамикфунктионинфо</span><span class="sxs-lookup"><span data-stu-id="b3c9b-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="b3c9b-103">Извлекает сведения о динамических методах.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3c9b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3c9b-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a><span data-ttu-id="b3c9b-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3c9b-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="b3c9b-106">окне Идентификатор функции, для которой требуется получить сведения.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-106">[in] The ID of the function for which to retrieve information.</span></span>

`moduleId` \
<span data-ttu-id="b3c9b-107">окне Указатель на модуль, в котором определен родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>

`ppvSig` \
<span data-ttu-id="b3c9b-108">заполняет Указатель на сигнатуру для функции.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-108">[out] A pointer to the signature for the function.</span></span>

`pbSig` \
<span data-ttu-id="b3c9b-109">заполняет Указатель на число байтов для сигнатуры функции.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-109">[out] A pointer to the count of bytes for the function signature.</span></span>

`cchName` \
<span data-ttu-id="b3c9b-110">[in] Максимальный размер массива `wszName`.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-110">[in] The maximum size of the `wszName` array.</span></span>

`pcchName` \
<span data-ttu-id="b3c9b-111">заполняет Число символов в `wszName` массиве.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-111">[out] The number of characters in the `wszName` array.</span></span>

`wszName` \
<span data-ttu-id="b3c9b-112">заполняет Массив `WCHAR` , содержащий имя функции, если таковое существует.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3c9b-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="b3c9b-113">Remarks</span></span>

<span data-ttu-id="b3c9b-114">Некоторые методы, такие как заглушки IL или LCG, не имеют связанных метаданных, которые можно извлечь с помощью интерфейсов API [IMetaDataImport](../metadata/imetadataimport-interface.md) и [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c9b-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="b3c9b-115">Такие методы могут быть обнаружены профилировщиками с помощью указателей инструкций или путем прослушивания [ICorProfilerCallback8::D инамикмесоджиткомпилатионстартед](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3c9b-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="b3c9b-116">Этот API можно использовать для получения сведений о динамических методах, включая понятное имя, если оно доступно.</span><span class="sxs-lookup"><span data-stu-id="b3c9b-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3c9b-117">Требования</span><span class="sxs-lookup"><span data-stu-id="b3c9b-117">Requirements</span></span>

<span data-ttu-id="b3c9b-118">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3c9b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b3c9b-119">**Заголовок.** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b3c9b-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b3c9b-120">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="b3c9b-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b3c9b-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c9b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c9b-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b3c9b-122">See also</span></span>

- [<span data-ttu-id="b3c9b-123">Интерфейс ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="b3c9b-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
