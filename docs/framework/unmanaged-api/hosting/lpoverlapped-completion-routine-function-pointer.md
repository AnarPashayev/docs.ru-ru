---
title: Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce2ce6dd1210eef94e77b5d6a2d58a35cf971e6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138779"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="56246-102">Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="56246-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="56246-103">Указывает на функцию, которая уведомляет основное приложение перекрывающегося (то есть асинхронный) завершения ввода-вывода на устройство.</span><span class="sxs-lookup"><span data-stu-id="56246-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="56246-104">Этот указатель функции был объявлен устаревшим в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56246-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56246-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="56246-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56246-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="56246-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="56246-107">[in] Значение, является кодом ошибки, если устройство было закрыто; в противном случае это значение равно нулю.</span><span class="sxs-lookup"><span data-stu-id="56246-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="56246-108">Закрытие устройства приводит к немедленному завершению всех ожидающих операций ввода-вывода на устройстве.</span><span class="sxs-lookup"><span data-stu-id="56246-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="56246-109">[in] Число байтов, переданных в операции ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="56246-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="56246-110">[in] Указатель на структуру, содержащую информацию, используемую для выполнения запроса ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="56246-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56246-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="56246-111">Remarks</span></span>  
 <span data-ttu-id="56246-112">Функция, которая `LPOVERLAPPED_COMPLETION_ROUTINE` точки — это функция обратного вызова и должны быть реализованы модулем записи ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="56246-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="56246-113">Функция обратного вызова позволяет основному приложению обработать выполненный запрос ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="56246-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56246-114">Требования</span><span class="sxs-lookup"><span data-stu-id="56246-114">Requirements</span></span>  
 <span data-ttu-id="56246-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56246-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56246-116">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56246-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56246-117">**Библиотека:** "Mscorwks.dll"</span><span class="sxs-lookup"><span data-stu-id="56246-117">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="56246-118">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="56246-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56246-119">См. также</span><span class="sxs-lookup"><span data-stu-id="56246-119">See also</span></span>

- [<span data-ttu-id="56246-120">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="56246-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
