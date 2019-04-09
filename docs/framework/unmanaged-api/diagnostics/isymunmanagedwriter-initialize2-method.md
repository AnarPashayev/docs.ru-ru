---
title: Метод ISymUnmanagedWriter::Initialize2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e645f79018d4ad41451faa07eba860e68b917539
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187022"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="96979-102">Метод ISymUnmanagedWriter::Initialize2</span><span class="sxs-lookup"><span data-stu-id="96979-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="96979-103">Задает интерфейс включения метаданных, с которым будет связан этот модуль записи и задает имя выходного файла, в который записываются символы отладки.</span><span class="sxs-lookup"><span data-stu-id="96979-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="96979-104">Этот метод также позволяет задать конечное расположение файла базы данных (PDB) программы.</span><span class="sxs-lookup"><span data-stu-id="96979-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96979-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96979-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96979-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96979-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="96979-107">[in] Указатель на интерфейс включения метаданных.</span><span class="sxs-lookup"><span data-stu-id="96979-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="96979-108">[in] Указатель на `WCHAR` , содержащий имя файла, в который записываются символы отладки.</span><span class="sxs-lookup"><span data-stu-id="96979-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="96979-109">Если имя файла задано для модуля записи, который не использует имена файлов, этот параметр пропускается.</span><span class="sxs-lookup"><span data-stu-id="96979-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="96979-110">[in] Если указан, модуль записи символов выдает символы в заданной <xref:System.Runtime.InteropServices.ComTypes.IStream> , а не файл, указанный в `filename` параметра.</span><span class="sxs-lookup"><span data-stu-id="96979-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="96979-111">Параметр `pIStream` является необязательным.</span><span class="sxs-lookup"><span data-stu-id="96979-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="96979-112">[in] `true` Если это полное перестроение; `false` Если это добавочная компиляция.</span><span class="sxs-lookup"><span data-stu-id="96979-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="96979-113">[in] Указатель на `WCHAR` то есть строка пути в конечное расположение PDB-файл.</span><span class="sxs-lookup"><span data-stu-id="96979-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96979-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="96979-114">Return Value</span></span>  
 <span data-ttu-id="96979-115">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="96979-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96979-116">Требования</span><span class="sxs-lookup"><span data-stu-id="96979-116">Requirements</span></span>  
 <span data-ttu-id="96979-117">**Заголовок.** CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="96979-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96979-118">См. также</span><span class="sxs-lookup"><span data-stu-id="96979-118">See also</span></span>

- [<span data-ttu-id="96979-119">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="96979-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="96979-120">Метод Initialize</span><span class="sxs-lookup"><span data-stu-id="96979-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
