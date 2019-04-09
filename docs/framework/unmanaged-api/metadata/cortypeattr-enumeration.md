---
title: Перечисление CorTypeAttr
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e7c973ee22350f26b4f86bcc8b4c4c727291ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087291"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="7782d-102">Перечисление CorTypeAttr</span><span class="sxs-lookup"><span data-stu-id="7782d-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="7782d-103">Содержит значения, указывающие тип метаданных.</span><span class="sxs-lookup"><span data-stu-id="7782d-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7782d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7782d-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7782d-105">Участники</span><span class="sxs-lookup"><span data-stu-id="7782d-105">Members</span></span>  
  
|<span data-ttu-id="7782d-106">Член</span><span class="sxs-lookup"><span data-stu-id="7782d-106">Member</span></span>|<span data-ttu-id="7782d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7782d-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="7782d-108">Используется для сведения о видимости типа.</span><span class="sxs-lookup"><span data-stu-id="7782d-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="7782d-109">Указывает, что тип не открытую область видимости.</span><span class="sxs-lookup"><span data-stu-id="7782d-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="7782d-110">Указывает, что тип находится в общей области.</span><span class="sxs-lookup"><span data-stu-id="7782d-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="7782d-111">Указывает, что тип является вложенным с открытой областью видимости.</span><span class="sxs-lookup"><span data-stu-id="7782d-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="7782d-112">Указывает, что тип является вложенным с закрытой областью видимости.</span><span class="sxs-lookup"><span data-stu-id="7782d-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="7782d-113">Указывает, что тип является вложенным с областью видимости.</span><span class="sxs-lookup"><span data-stu-id="7782d-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="7782d-114">Указывает, что тип является вложенным с видимостью сборки.</span><span class="sxs-lookup"><span data-stu-id="7782d-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="7782d-115">Указывает, что тип является вложенным с областью видимости семейство и сборка.</span><span class="sxs-lookup"><span data-stu-id="7782d-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="7782d-116">Указывает, что тип является вложенным с областью видимости семейство или сборка.</span><span class="sxs-lookup"><span data-stu-id="7782d-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="7782d-117">Получает сведения о структуре для типа.</span><span class="sxs-lookup"><span data-stu-id="7782d-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="7782d-118">Указывает, что поля этого типа располагаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="7782d-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="7782d-119">Указывает, что поля этого типа располагаются последовательно.</span><span class="sxs-lookup"><span data-stu-id="7782d-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="7782d-120">Указывает, что этот макет поля задается явно.</span><span class="sxs-lookup"><span data-stu-id="7782d-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="7782d-121">Получает семантическую информацию о типе.</span><span class="sxs-lookup"><span data-stu-id="7782d-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="7782d-122">Указывает, что данный тип является классом.</span><span class="sxs-lookup"><span data-stu-id="7782d-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="7782d-123">Указывает, что данный тип является интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="7782d-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="7782d-124">Указывает, что данный тип является абстрактным.</span><span class="sxs-lookup"><span data-stu-id="7782d-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="7782d-125">Указывает, что тип не может быть расширен.</span><span class="sxs-lookup"><span data-stu-id="7782d-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="7782d-126">Указывает, что имя класса является специальным.</span><span class="sxs-lookup"><span data-stu-id="7782d-126">Specifies that the class name is special.</span></span> <span data-ttu-id="7782d-127">Указывает его имя как.</span><span class="sxs-lookup"><span data-stu-id="7782d-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="7782d-128">Указывает, что тип импортирован.</span><span class="sxs-lookup"><span data-stu-id="7782d-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="7782d-129">Указывает, что тип является сериализуемым.</span><span class="sxs-lookup"><span data-stu-id="7782d-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="7782d-130">Указывает, что этот тип является [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типа.</span><span class="sxs-lookup"><span data-stu-id="7782d-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="7782d-131">Получает сведения о способ кодирования и форматирования строк.</span><span class="sxs-lookup"><span data-stu-id="7782d-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="7782d-132">Указывает, что данный тип интерпретирует LPTSTR как ANSI.</span><span class="sxs-lookup"><span data-stu-id="7782d-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="7782d-133">Указывает, что данный тип интерпретирует LPTSTR как Юникод.</span><span class="sxs-lookup"><span data-stu-id="7782d-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="7782d-134">Указывает, что данный тип интерпретирует LPTSTR автоматически.</span><span class="sxs-lookup"><span data-stu-id="7782d-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="7782d-135">Указывает, что тип имеет нестандартной кодировкой, определяемом параметрами `CustomFormatMask`.</span><span class="sxs-lookup"><span data-stu-id="7782d-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="7782d-136">Эта маска используется для получения нестандартной кодировки для взаимодействия с машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="7782d-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="7782d-137">Смысл значений этих двух бит не определено.</span><span class="sxs-lookup"><span data-stu-id="7782d-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="7782d-138">Указывает, что тип должен быть инициализирован перед первая попытка получить доступ к статическому полю.</span><span class="sxs-lookup"><span data-stu-id="7782d-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="7782d-139">Указывает, что тип экспортирован и метод передачи типа.</span><span class="sxs-lookup"><span data-stu-id="7782d-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="7782d-140">Этот флаг и приведенные ниже флаги используются внутри среда CLR.</span><span class="sxs-lookup"><span data-stu-id="7782d-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="7782d-141">Указывает, что среда CLR должна проверять кодировку имени.</span><span class="sxs-lookup"><span data-stu-id="7782d-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="7782d-142">Указывает, что тип имеет безопасности, связанные с ней.</span><span class="sxs-lookup"><span data-stu-id="7782d-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7782d-143">Требования</span><span class="sxs-lookup"><span data-stu-id="7782d-143">Requirements</span></span>  
 <span data-ttu-id="7782d-144">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7782d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7782d-145">**Заголовок.** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7782d-145">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="7782d-146">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7782d-146">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7782d-147">См. также</span><span class="sxs-lookup"><span data-stu-id="7782d-147">See also</span></span>

- [<span data-ttu-id="7782d-148">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="7782d-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
