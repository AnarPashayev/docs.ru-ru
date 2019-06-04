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
ms.openlocfilehash: 59565b28991f6d61ff2c6c77540eace92461aa89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490172"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE
Указывает на функцию, которая уведомляет основное приложение перекрывающегося (то есть асинхронный) завершения ввода-вывода на устройство.  
  
 Этот указатель функции был объявлен устаревшим в .NET Framework 4.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `dwErrorCode`  
 [in] Значение, является кодом ошибки, если устройство было закрыто; в противном случае это значение равно нулю.  
  
 Закрытие устройства приводит к немедленному завершению всех ожидающих операций ввода-вывода на устройстве.  
  
 `dwNumberOfBytesTransfered`  
 [in] Число байтов, переданных в операции ввода-вывода.  
  
 `lpOverlapped`  
 [in] Указатель на структуру, содержащую информацию, используемую для выполнения запроса ввода-вывода.  
  
## <a name="remarks"></a>Примечания  
 Функция, которая `LPOVERLAPPED_COMPLETION_ROUTINE` точки — это функция обратного вызова и должны быть реализованы модулем записи ведущего приложения. Функция обратного вызова позволяет основному приложению обработать выполненный запрос ввода-вывода.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** MSCorEE.h  
  
 **Библиотека:** "Mscorwks.dll"  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Устаревшие функции размещения CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
