---
title: Метод ICorProfilerInfo::GetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 484fb5b8398e3ebd61d1c300afec1536ee1dc0c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780602"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="efd44-102">Метод ICorProfilerInfo::GetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="efd44-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="efd44-103">Получает указатель в теле метода в код MSIL (MSIL), начиная с его заголовка.</span><span class="sxs-lookup"><span data-stu-id="efd44-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd44-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="efd44-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd44-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="efd44-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="efd44-106">[in] Идентификатор модуля, в которой находится функция.</span><span class="sxs-lookup"><span data-stu-id="efd44-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="efd44-107">[in] Токен метаданных для метода.</span><span class="sxs-lookup"><span data-stu-id="efd44-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="efd44-108">[out] Указатель на заголовок метода.</span><span class="sxs-lookup"><span data-stu-id="efd44-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="efd44-109">[out] Целое число, указывающее размер метода.</span><span class="sxs-lookup"><span data-stu-id="efd44-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efd44-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="efd44-110">Remarks</span></span>  
 <span data-ttu-id="efd44-111">Метод ограничивается модуля, в котором он находится.</span><span class="sxs-lookup"><span data-stu-id="efd44-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="efd44-112">Так как `GetILFunctionBody` метод предназначен для предоставления доступа для кода на языке MSIL, прежде чем он был загружен с общеязыковой среды выполнения (CLR), для поиска требуемого экземпляра используется токен метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="efd44-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="efd44-113">`GetILFunctionBody` может возвращать CORPROF_E_FUNCTION_NOT_IL HRESULT, если `methodId` указывает на метод без любой MSIL кода (например, абстрактный метод или платформа вызова метода (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="efd44-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd44-114">Требования</span><span class="sxs-lookup"><span data-stu-id="efd44-114">Requirements</span></span>  
 <span data-ttu-id="efd44-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd44-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd44-116">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efd44-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efd44-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efd44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efd44-118">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd44-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd44-119">См. также</span><span class="sxs-lookup"><span data-stu-id="efd44-119">See also</span></span>

- [<span data-ttu-id="efd44-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="efd44-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
