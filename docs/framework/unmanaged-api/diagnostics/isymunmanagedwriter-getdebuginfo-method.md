---
title: Метод ISymUnmanagedWriter::GetDebugInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8737885015055994bff3f6066bccb551f19f74f4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777317"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="b15d1-102">Метод ISymUnmanagedWriter::GetDebugInfo</span><span class="sxs-lookup"><span data-stu-id="b15d1-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="b15d1-103">Возвращает информацию, необходимую для компилятора, чтобы написать запись каталога отладки в заголовок переносимого исполняемого (PE) файла.</span><span class="sxs-lookup"><span data-stu-id="b15d1-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="b15d1-104">Модуль записи символов заполнения всех полей, за исключением `TimeDateStamp` и `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="b15d1-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="b15d1-105">(Компилятор отвечает за правильную настройку этих полей.)</span><span class="sxs-lookup"><span data-stu-id="b15d1-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="b15d1-106">Компилятор должен вызывать этот метод, порождаемого большой двоичный объект данных к PE-файлу, задайте `PointerToRawData` в IMAGE_DEBUG_DIRECTORY пункты порожденную данных и запись IMAGE_DEBUG_DIRECTORY PE-файл.</span><span class="sxs-lookup"><span data-stu-id="b15d1-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="b15d1-107">Компилятор также следует задать `TimeDateStamp` равным `TimeDateStamp` создаваемого PE-файла.</span><span class="sxs-lookup"><span data-stu-id="b15d1-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b15d1-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b15d1-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b15d1-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="b15d1-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="b15d1-110">[in, out] Указатель на IMAGE_DEBUG_DIRECTORY, заполняемой интерфейс записи символов.</span><span class="sxs-lookup"><span data-stu-id="b15d1-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="b15d1-111">[in] Объект `DWORD` , содержащий размер данных отладки.</span><span class="sxs-lookup"><span data-stu-id="b15d1-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="b15d1-112">[out] Указатель на `DWORD` , принимает размер буфера, требуемого для хранения данных отладки.</span><span class="sxs-lookup"><span data-stu-id="b15d1-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="b15d1-113">[out] Указатель на буфер, достаточно велик для хранения данных в хранилище символов отладки.</span><span class="sxs-lookup"><span data-stu-id="b15d1-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b15d1-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b15d1-114">Return Value</span></span>  
 <span data-ttu-id="b15d1-115">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="b15d1-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b15d1-116">Требования</span><span class="sxs-lookup"><span data-stu-id="b15d1-116">Requirements</span></span>  
 <span data-ttu-id="b15d1-117">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b15d1-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15d1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b15d1-118">See also</span></span>

- [<span data-ttu-id="b15d1-119">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b15d1-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
