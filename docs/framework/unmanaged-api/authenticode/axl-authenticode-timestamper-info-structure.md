---
title: Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d82ed3299f967457fe967d096a238da6143751a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948925"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a>Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO
Определяет информацию об отметке времени Authenticode.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`cbSize`|Размер этой структуры.|  
|`dwError`|Код ошибки.|  
|`algHash`|Хэш-алгоритм.|  
|`ftTimestamp`|Время отметки времени.|  
|`pChainContext`|Контекст цепочки отметки времени.  См. в разделе [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) структуры.|  
  
## <a name="see-also"></a>См. также

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
