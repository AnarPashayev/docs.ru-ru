---
title: Интерфейс ICLRValidator
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762049"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="d2abb-102">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="d2abb-102">ICLRValidator Interface</span></span>
<span data-ttu-id="d2abb-103">Предоставляет методы для проверки переносимых исполняемых (PE) образов и создания отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="d2abb-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2abb-104">Методы</span><span class="sxs-lookup"><span data-stu-id="d2abb-104">Methods</span></span>  
  
|<span data-ttu-id="d2abb-105">Метод</span><span class="sxs-lookup"><span data-stu-id="d2abb-105">Method</span></span>|<span data-ttu-id="d2abb-106">Описание</span><span class="sxs-lookup"><span data-stu-id="d2abb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2abb-107">Метод FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="d2abb-107">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="d2abb-108">Возвращает подробное сообщение об указанной ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="d2abb-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="d2abb-109">Метод Validate</span><span class="sxs-lookup"><span data-stu-id="d2abb-109">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="d2abb-110">Проверяет переносимый исполняемый файл или язык MSIL в указанном файле.</span><span class="sxs-lookup"><span data-stu-id="d2abb-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2abb-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d2abb-111">Requirements</span></span>  
 <span data-ttu-id="d2abb-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2abb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2abb-113">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="d2abb-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d2abb-114">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2abb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2abb-115">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2abb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2abb-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d2abb-116">See also</span></span>

- [<span data-ttu-id="d2abb-117">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="d2abb-117">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="d2abb-118">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="d2abb-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d2abb-119">Кокласс CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d2abb-119">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
