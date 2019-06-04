---
title: Функция LoadLibraryShim
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87ca5470fe5994d34d12a339c2d92a5f3917063d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490223"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="7a66b-102">Функция LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="7a66b-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="7a66b-103">Загружает указанную версию библиотеки DLL, включенный в распространяемый пакет .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a66b-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="7a66b-104">Эта функция является устаревшим в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7a66b-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="7a66b-105">Используйте [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="7a66b-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a66b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a66b-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a66b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a66b-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="7a66b-108">[in] Нулем строка, представляющая имя библиотеки DLL, загружаемых из библиотеки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a66b-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="7a66b-109">[in] Нулем строка, представляющая версию библиотеки DLL для загрузки.</span><span class="sxs-lookup"><span data-stu-id="7a66b-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="7a66b-110">Если `szVersion` имеет значение null, версии, для загрузки выбрана последняя версия указанной библиотеки DLL, которая меньше, чем версии 4.</span><span class="sxs-lookup"><span data-stu-id="7a66b-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="7a66b-111">То есть учитываются все версии, равно или больше, чем версии 4, если `szVersion` имеет значение null, и если установлена не версия ниже версии 4, библиотеки DLL не загружается.</span><span class="sxs-lookup"><span data-stu-id="7a66b-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="7a66b-112">Это гарантирует, что установка платформы .NET Framework 4 не влияет на существующие приложения или компоненты.</span><span class="sxs-lookup"><span data-stu-id="7a66b-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="7a66b-113">См. в записи [In-Proc SxS и быстрого запуска миграции](https://go.microsoft.com/fwlink/?LinkId=200329) в блоге группы CLR.</span><span class="sxs-lookup"><span data-stu-id="7a66b-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="7a66b-114">Зарезервировано для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="7a66b-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="7a66b-115">[out] Указатель на дескриптор модуля.</span><span class="sxs-lookup"><span data-stu-id="7a66b-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a66b-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7a66b-116">Return Value</span></span>  
 <span data-ttu-id="7a66b-117">Этот метод возвращает стандартные коды ошибок объектов модели компонентов (COM), как определено в файле WinError.h, помимо следующих значений.</span><span class="sxs-lookup"><span data-stu-id="7a66b-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7a66b-118">Код возврата</span><span class="sxs-lookup"><span data-stu-id="7a66b-118">Return code</span></span>|<span data-ttu-id="7a66b-119">Описание</span><span class="sxs-lookup"><span data-stu-id="7a66b-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a66b-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a66b-120">S_OK</span></span>|<span data-ttu-id="7a66b-121">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="7a66b-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="7a66b-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="7a66b-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="7a66b-123">Загрузка `szDllName` требуется загрузка общеязыковой среды выполнения (CLR) и необходимую версию среды CLR не удается загрузить.</span><span class="sxs-lookup"><span data-stu-id="7a66b-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a66b-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="7a66b-124">Remarks</span></span>  
 <span data-ttu-id="7a66b-125">Эта функция используется для загрузки библиотеки DLL, которые включаются в распространяемый пакет .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a66b-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="7a66b-126">Она не загружает библиотеки DLL, созданное пользователем.</span><span class="sxs-lookup"><span data-stu-id="7a66b-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a66b-127">Начиная с .NET Framework версии 2.0, загрузка Fusion.dll приводит к среде CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="7a66b-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="7a66b-128">Это обусловлено функций в Fusion.dll теперь являются оболочками, реализация которых предоставляются средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="7a66b-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a66b-129">Требования</span><span class="sxs-lookup"><span data-stu-id="7a66b-129">Requirements</span></span>  
 <span data-ttu-id="7a66b-130">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a66b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a66b-131">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a66b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a66b-132">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a66b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a66b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7a66b-133">See also</span></span>

- [<span data-ttu-id="7a66b-134">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="7a66b-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
