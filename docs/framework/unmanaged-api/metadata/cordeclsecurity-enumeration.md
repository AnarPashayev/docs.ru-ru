---
title: Перечисление CorDeclSecurity
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136972"
---
# <a name="cordeclsecurity-enumeration"></a>Перечисление CorDeclSecurity
Указывает действия безопасности, которые можно выполнить с помощью декларативной безопасности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`dclActionMask`|Зарезервировано.|  
|`dclActionNil`|Зарезервировано.|  
|`dclRequest`|Зарезервировано.|  
|`dclDemand`|Всем вызывающим объектам выше в стеке вызовов должно быть предоставлено разрешение, заданное текущим объектом разрешений.|  
|`dclAssert`|Вызывающий код может получить доступ к ресурсу, определяемому текущим объектом разрешения, даже если вызывающим объектам выше в стеке вызовов не предоставлено разрешение на доступ к ресурсу|  
|`dclDeny`|Для доступа к ресурсу, указанному текущим объектом разрешения запрещен вызывающим объектам, даже если они имеют разрешения на доступ к нему.|  
|`dclPermitOnly`|Доступ можно получить только к ресурсам, указанным данным объектом разрешения, даже если коду предоставлено разрешение на доступ к другим ресурсам.|  
|`dclLinktimeCheck`|Непосредственный вызывающий оператор является обязательным, необходимо предоставить указанное разрешение для указанного периода времени.|  
|`dclInheritanceCheck`|Производного класса наследующему другой класс или переопределяющему метод, требуется получить указанное разрешение.|  
|`dclRequestMinimum`|Вызывающий объект может запросить минимальные разрешения, необходимые для выполнения кода. Это действие может использоваться только в пределах сборки.|  
|`dclRequestOptional`|Вызывающий объект может запросить дополнительные разрешения, которые не являются обязательными (не требуется для запуска). Этот запрос неявно отклоняет все прочие разрешения, не запрошенные специально. Это действие может использоваться только в пределах сборки.|  
|`dclRequestRefuse`|Не получат запрос вызывающей стороны для разрешения, которые могут быть неправильно использованы. Это действие может использоваться только в пределах сборки.|  
|`dclPrejitGrant`|Зарезервировано.|  
|`dclPrejitDenied`|Зарезервировано.|  
|`dclNonCasDemand`|Зарезервировано.|  
|`dclNonCasLinkDemand`|Указанное разрешение необходимо предоставить непосредственно вызывающему объекту.|  
|`dclNonCasInheritance`|Зарезервировано.|  
|`dclLinkDemandChoice`|Зарезервировано.|  
|`dclInheritanceDemandChoice`|Зарезервировано.|  
|`dclDemandChoice`|Зарезервировано.|  
|`dclMaximumValue`|Зарезервировано.|  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorHdr.h  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Перечисления метаданных](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
