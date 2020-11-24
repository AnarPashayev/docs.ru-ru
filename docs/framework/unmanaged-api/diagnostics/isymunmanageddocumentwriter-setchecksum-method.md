---
title: Метод ISymUnmanagedDocumentWriter::SetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: 58055d9ea56d7928729d289198965752985d8e0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688904"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="aa35e-102">Метод ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="aa35e-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="aa35e-103">Задает сведения о контрольной сумме.</span><span class="sxs-lookup"><span data-stu-id="aa35e-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa35e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa35e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa35e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="aa35e-105">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="aa35e-106">окне Идентификатор GUID, представляющий идентификатор алгоритма.</span><span class="sxs-lookup"><span data-stu-id="aa35e-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="aa35e-107">окне Значение типа `ULONG32` , указывающее размер буфера (в байтах) `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="aa35e-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="aa35e-108">окне Буфер, в котором хранятся сведения о контрольной сумме.</span><span class="sxs-lookup"><span data-stu-id="aa35e-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa35e-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="aa35e-109">Return Value</span></span>  

 <span data-ttu-id="aa35e-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="aa35e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa35e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="aa35e-111">Requirements</span></span>  

 <span data-ttu-id="aa35e-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="aa35e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa35e-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="aa35e-113">See also</span></span>

- [<span data-ttu-id="aa35e-114">Интерфейс ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="aa35e-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
