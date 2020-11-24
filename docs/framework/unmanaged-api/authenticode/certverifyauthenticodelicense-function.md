---
title: Функция CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
ms.openlocfilehash: 388814d1c63f048c0aa231a1d0058a390cba9493
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674064"
---
# <a name="certverifyauthenticodelicense-function"></a>Функция CertVerifyAuthenticodeLicense

Проверяет правильность лицензии Authenticode XrML.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `pLicenseBlob`  
 [в] Лицензия Authenticode XrML должна быть проверена.  
  
 См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `dwFlags`  
 [в] Необязательно. Комбинация следующих значений:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [из] Для получения сведений о подписавшем. Если лицензия не подписана, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE. Он отвечает за освобождение ресурсов с помощью функции [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) после использования.  
  
 См. раздел [структура AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [из] Для получения сведений об отметке времени (если есть). Если отметки времени для лицензии не установлены, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE. Он отвечает за освобождение ресурсов с помощью функции [цертфриаусентикодетиместамперинфо](certfreeauthenticodetimestamperinfo-function.md) после использования.  
  
 См. раздел [структура AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Возвращаемое значение  

 Возвращает значение `S_OK` в случае успешного выполнения. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел

- [Authenticode](index.md)
- [Метод GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [Интерфейс ICLRStrongName](../hosting/iclrstrongname-interface.md)
