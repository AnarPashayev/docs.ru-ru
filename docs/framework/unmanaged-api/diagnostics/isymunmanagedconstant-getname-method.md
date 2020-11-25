---
title: Метод ISymUnmanagedConstant::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: fca7b11a83b5a695feae82fe5f25218f87afbce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732896"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="6546a-102">Метод ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="6546a-102">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="6546a-103">Возвращает имя константы.</span><span class="sxs-lookup"><span data-stu-id="6546a-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6546a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6546a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6546a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6546a-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="6546a-106">окне Длина буфера, `szName` на который указывает параметр.</span><span class="sxs-lookup"><span data-stu-id="6546a-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6546a-107">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения имени, включая завершение нулевого значения.</span><span class="sxs-lookup"><span data-stu-id="6546a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="6546a-108">заполняет Буфер, в котором хранится имя.</span><span class="sxs-lookup"><span data-stu-id="6546a-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6546a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6546a-109">Return Value</span></span>  

 <span data-ttu-id="6546a-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6546a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6546a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6546a-111">Requirements</span></span>  

 <span data-ttu-id="6546a-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="6546a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6546a-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6546a-113">See also</span></span>

- [<span data-ttu-id="6546a-114">Интерфейс ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="6546a-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="6546a-115">Метод GetSignature</span><span class="sxs-lookup"><span data-stu-id="6546a-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="6546a-116">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="6546a-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
