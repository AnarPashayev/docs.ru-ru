---
title: Перечисление METAHOST_POLICY_FLAGS
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: 16fb112cf5b209091001872567c95bb0b3a8ab61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729997"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="6d669-102">Перечисление METAHOST_POLICY_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d669-102">METAHOST_POLICY_FLAGS Enumeration</span></span>

<span data-ttu-id="6d669-103">Предоставляет политики привязки, которые являются общими для большинства хостов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6d669-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="6d669-104">Это перечисление используется методом [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d669-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d669-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d669-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6d669-106">Члены</span><span class="sxs-lookup"><span data-stu-id="6d669-106">Members</span></span>  
  
|<span data-ttu-id="6d669-107">Член</span><span class="sxs-lookup"><span data-stu-id="6d669-107">Member</span></span>|<span data-ttu-id="6d669-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6d669-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="6d669-109">Определяет политику высокой совместимости, которая не учитывает среду CLR, которая загружается в текущий процесс.</span><span class="sxs-lookup"><span data-stu-id="6d669-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="6d669-110">Вместо этого он учитывает только установленные CLR и параметры компонента, как производные от самого файла сборки, объявленной встроенной версии или файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6d669-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="6d669-111">Применяет политику обновления к результату привязки к версии, если точное соответствие не найдено на основе содержимого HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . нетфрамеворк\полици\упградес.</span><span class="sxs-lookup"><span data-stu-id="6d669-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="6d669-112">Это тот же результат, что и [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6d669-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="6d669-113">Результаты привязки возвращаются, как если бы изображение, предоставленное для вызова, было запущено в новом процессе.</span><span class="sxs-lookup"><span data-stu-id="6d669-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="6d669-114">В настоящее время не `GetRequestedRuntime` учитывает набор сред выполнения, допускающих загрузку, и привязывает их к набору установленных сред выполнения.</span><span class="sxs-lookup"><span data-stu-id="6d669-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="6d669-115">Этот флаг позволяет узлу определить, к какой среде выполнения будет привязан EXE-файл при запуске.</span><span class="sxs-lookup"><span data-stu-id="6d669-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="6d669-116">Если `GetRequestedRuntime` приложению не удается найти среду выполнения, совместимую с входными параметрами, отображается диалоговое окно ошибки.</span><span class="sxs-lookup"><span data-stu-id="6d669-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="6d669-117">Начиная с .NET Framework 4,5, это диалоговое окно с сообщением об ошибке может иметь форму диалогового окна компонента Windows, в котором спрашивается, нужно ли пользователю включить соответствующую функцию.</span><span class="sxs-lookup"><span data-stu-id="6d669-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="6d669-118">`GetRequestedRuntime` использует образ процесса (и любой соответствующий файл конфигурации) в качестве дополнительных входных данных для процесса привязки.</span><span class="sxs-lookup"><span data-stu-id="6d669-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="6d669-119">По умолчанию не `GetRequestedRuntime` выполняет откат к пути образа процесса (как правило, к исполняемому файлу, который использовался для запуска процесса) при определении среды выполнения для привязки.</span><span class="sxs-lookup"><span data-stu-id="6d669-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="6d669-120">`GetRequestedRuntime` необходимо проверить, установлен ли соответствующий SKU, если в файле конфигурации нет доступных сведений.</span><span class="sxs-lookup"><span data-stu-id="6d669-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="6d669-121">Это позволяет приложениям, не имеющим файлов конфигурации, корректно завершать работу на более мелких SKU, чем установка по умолчанию .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d669-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="6d669-122">По умолчанию не `GetRequestedRuntime` проверяет, установлен ли соответствующий SKU, если атрибут sku не указан в элементе файла конфигурации `<supportedRuntime />` .</span><span class="sxs-lookup"><span data-stu-id="6d669-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="6d669-123">`GetRequestedRuntime` следует пропускать SEM_FAILCRITICALERRORS (который задается вызовом функции [функцию SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) и выводить диалоговое окно ошибки.</span><span class="sxs-lookup"><span data-stu-id="6d669-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="6d669-124">По умолчанию SEM_FAILCRITICALERRORS подавляет диалоговое окно ошибки.</span><span class="sxs-lookup"><span data-stu-id="6d669-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="6d669-125">Возможно, он был унаследован от другого процесса, и в вашем сценарии может быть нежелательным сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="6d669-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d669-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d669-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d669-127">Требования</span><span class="sxs-lookup"><span data-stu-id="6d669-127">Requirements</span></span>  

 <span data-ttu-id="6d669-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d669-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d669-129">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="6d669-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="6d669-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d669-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d669-131">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d669-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d669-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6d669-132">See also</span></span>

- [<span data-ttu-id="6d669-133">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="6d669-133">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="6d669-134">Метод GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="6d669-134">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
