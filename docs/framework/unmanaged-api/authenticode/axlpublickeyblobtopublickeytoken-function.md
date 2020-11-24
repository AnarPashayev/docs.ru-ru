---
title: Функция _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 989e99198efd1519f607a2e3164ff4de584e88af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679888"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="59464-102">\_Функция Акслпубликкэйблобтопубликкэйтокен</span><span class="sxs-lookup"><span data-stu-id="59464-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="59464-103">Вычисляет токен открытого ключа строгого имени из формата CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="59464-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59464-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59464-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59464-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="59464-105">Parameters</span></span>  

 `pCspPublicKeyBlob`  
 <span data-ttu-id="59464-106">[в] Большой двоичный объект открытого ключа CSP.</span><span class="sxs-lookup"><span data-stu-id="59464-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="59464-107">[из] Указатель на WCHAR \* для получения шестнадцатеричного кодированного хэша открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="59464-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59464-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="59464-108">Return Value</span></span>  

 <span data-ttu-id="59464-109">`S_OK`, если функция выполняется успешно. В противном случае — `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="59464-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59464-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="59464-110">See also</span></span>

- [<span data-ttu-id="59464-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="59464-111">Authenticode</span></span>](index.md)
