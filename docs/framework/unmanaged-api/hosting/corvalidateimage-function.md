---
title: Функция _CorValidateImage
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 2d49a40610bd0e1a7629594e245bde9eacfcc06d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687981"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="44c67-102">Функция _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="44c67-102">_CorValidateImage Function</span></span>

<span data-ttu-id="44c67-103">Проверяет образы управляемого модуля и уведомляет загрузчик операционной системы после их загрузки.</span><span class="sxs-lookup"><span data-stu-id="44c67-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c67-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44c67-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44c67-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="44c67-105">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="44c67-106">окне Указатель на начальное расположение изображения для проверки в качестве управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="44c67-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="44c67-107">Образ уже должен быть загружен в память.</span><span class="sxs-lookup"><span data-stu-id="44c67-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="44c67-108">окне Имя файла образа.</span><span class="sxs-lookup"><span data-stu-id="44c67-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44c67-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44c67-109">Return Value</span></span>  

 <span data-ttu-id="44c67-110">Эта функция возвращает стандартные значения `E_INVALIDARG` ,, `E_OUTOFMEMORY` `E_UNEXPECTED` и, а `E_FAIL` также следующие значения.</span><span class="sxs-lookup"><span data-stu-id="44c67-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="44c67-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44c67-111">Return value</span></span>|<span data-ttu-id="44c67-112">Описание</span><span class="sxs-lookup"><span data-stu-id="44c67-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="44c67-113">Недопустимый образ.</span><span class="sxs-lookup"><span data-stu-id="44c67-113">The image is invalid.</span></span> <span data-ttu-id="44c67-114">Это значение имеет 0xC000007BL HRESULT.</span><span class="sxs-lookup"><span data-stu-id="44c67-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="44c67-115">Изображение является допустимым.</span><span class="sxs-lookup"><span data-stu-id="44c67-115">The image is valid.</span></span> <span data-ttu-id="44c67-116">Это значение равно HRESULT 0x00000000.</span><span class="sxs-lookup"><span data-stu-id="44c67-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c67-117">Комментарии</span><span class="sxs-lookup"><span data-stu-id="44c67-117">Remarks</span></span>  

 <span data-ttu-id="44c67-118">В Windows XP и более поздних версиях загрузчик операционной системы проверяет наличие управляемых модулей, проверяя бит каталога дескрипторов COM в заголовке COFF.</span><span class="sxs-lookup"><span data-stu-id="44c67-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="44c67-119">Заданный бит указывает на управляемый модуль.</span><span class="sxs-lookup"><span data-stu-id="44c67-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="44c67-120">Если загрузчик обнаруживает управляемый модуль, он загружает MsCorEE.dll и вызывает `_CorValidateImage` , который выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="44c67-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="44c67-121">Подтверждает, что образ является допустимым управляемым модулем.</span><span class="sxs-lookup"><span data-stu-id="44c67-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="44c67-122">Изменяет точку входа в образе на точку входа в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="44c67-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="44c67-123">Для 64-разрядных версий Windows изменяет образ, наявляющийся в памяти, преобразуя его из формат PE32 в формат формат PE32 +.</span><span class="sxs-lookup"><span data-stu-id="44c67-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="44c67-124">Возвращается загрузчику при загрузке образов управляемого модуля.</span><span class="sxs-lookup"><span data-stu-id="44c67-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="44c67-125">Для исполняемых образов загрузчик операционной системы затем вызывает функцию [_CorExeMain](corexemain-function.md) , независимо от точки входа, указанной в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="44c67-125">For executable images, the operating system loader then calls the [_CorExeMain](corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="44c67-126">Для образов сборки DLL загрузчик вызывает функцию [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="44c67-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="44c67-127">`_CorExeMain` или `_CorDllMain` выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="44c67-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="44c67-128">Инициализирует среду CLR.</span><span class="sxs-lookup"><span data-stu-id="44c67-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="44c67-129">Находит управляемую точку входа из заголовка CLR сборки.</span><span class="sxs-lookup"><span data-stu-id="44c67-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="44c67-130">Начинает выполнение.</span><span class="sxs-lookup"><span data-stu-id="44c67-130">Begins execution.</span></span>  
  
 <span data-ttu-id="44c67-131">Загрузчик вызывает функцию [_CorImageUnloading](corimageunloading-function.md) при выгрузке образов управляемых модулей.</span><span class="sxs-lookup"><span data-stu-id="44c67-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="44c67-132">Однако эта функция не выполняет никаких действий. Он просто возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="44c67-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44c67-133">Требования</span><span class="sxs-lookup"><span data-stu-id="44c67-133">Requirements</span></span>  

 <span data-ttu-id="44c67-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44c67-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44c67-135">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="44c67-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44c67-136">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44c67-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44c67-137">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44c67-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c67-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="44c67-138">See also</span></span>

- [<span data-ttu-id="44c67-139">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="44c67-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
