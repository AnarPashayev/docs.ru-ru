---
title: Метод ICLRDataTarget3::GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b43ab8cdeff3866bb51e8634f367cf86ee483d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089235"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="a51f6-102">Метод ICLRDataTarget3::GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="a51f6-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="a51f6-103">Вызывается службами доступа к данным среды CLR для извлечения записи контекста, связанной с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="a51f6-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="a51f6-104">Например, для целевого объекта дампа, это будет эквивалентно записи контекста, переданной через `ExceptionParam` аргумент [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) функции в Windows отладка библиотеки справки (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="a51f6-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51f6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a51f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a51f6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a51f6-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="a51f6-107">[в] Размер входного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="a51f6-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="a51f6-108">Он должен быть достаточно большим, чтобы вместить запись контекста.</span><span class="sxs-lookup"><span data-stu-id="a51f6-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="a51f6-109">[из] Указатель на тип `ULONG32`, который получает количество байтов, фактически записанных в буфер.</span><span class="sxs-lookup"><span data-stu-id="a51f6-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a51f6-110">[из] Указатель на буфер памяти, который получает копию записи контекста.</span><span class="sxs-lookup"><span data-stu-id="a51f6-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="a51f6-111">Запись исключения возвращается в виде [контекст](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) типа.</span><span class="sxs-lookup"><span data-stu-id="a51f6-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a51f6-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a51f6-112">Return Value</span></span>  
 <span data-ttu-id="a51f6-113">Возвращается значение `S_OK` при успешном выполнении или код ошибки `HRESULT` при сбое.</span><span class="sxs-lookup"><span data-stu-id="a51f6-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="a51f6-114">Коды `HRESULT` могут включать значения, приведенные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="a51f6-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="a51f6-115">Код возврата</span><span class="sxs-lookup"><span data-stu-id="a51f6-115">Return code</span></span>|<span data-ttu-id="a51f6-116">Описание</span><span class="sxs-lookup"><span data-stu-id="a51f6-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="a51f6-117">Метод успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="a51f6-117">Method succeeded.</span></span> <span data-ttu-id="a51f6-118">Запись контекста скопирована в буфер вывода.</span><span class="sxs-lookup"><span data-stu-id="a51f6-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="a51f6-119">Нет записей контекста, связанных с целевым объектом.</span><span class="sxs-lookup"><span data-stu-id="a51f6-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="a51f6-120">Размер входного буфера недостаточен для сохранения записи контекста.</span><span class="sxs-lookup"><span data-stu-id="a51f6-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a51f6-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="a51f6-121">Remarks</span></span>  
 <span data-ttu-id="a51f6-122">[КОНТЕКСТ](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) — это структура платформы, определенные в заголовки, предоставляемые пакетом SDK для Windows.</span><span class="sxs-lookup"><span data-stu-id="a51f6-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="a51f6-123">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="a51f6-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a51f6-124">Требования</span><span class="sxs-lookup"><span data-stu-id="a51f6-124">Requirements</span></span>  
 <span data-ttu-id="a51f6-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a51f6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a51f6-126">**Заголовок.** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a51f6-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a51f6-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a51f6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a51f6-128">**Версии платформы .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a51f6-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51f6-129">См. также</span><span class="sxs-lookup"><span data-stu-id="a51f6-129">See also</span></span>

- [<span data-ttu-id="a51f6-130">Интерфейс ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="a51f6-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="a51f6-131">Метод GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="a51f6-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="a51f6-132">Метод GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="a51f6-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
