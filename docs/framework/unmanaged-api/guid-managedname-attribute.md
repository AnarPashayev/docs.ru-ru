---
title: Атрибут GUID_ManagedName
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 0127b6894f1095521f1b24fc8c0424dc7db824b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721053"
---
# <a name="guid_managedname-attribute"></a>Атрибут GUID_ManagedName

Определяет настраиваемый атрибут интерфейса, указывающий имя управляемого пространства имен для библиотеки COM.  
  
## <a name="syntax"></a>Синтаксис  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Параметры  

 `value`  
 Имя управляемого пространства имен для библиотеки.  
  
## <a name="definition"></a>Определение  

 `GUID_ManagedName` определяется в COR. h следующим образом:  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Комментарии  

 Пользовательский атрибут интерфейса определяет метаданные для объекта в библиотеке типов.  
  
 Используйте <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> или <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> для получения управляемого имени из атрибута.  
  
 Дополнительные сведения см. в разделе [атрибуты интерфейса](/cpp/windows/attributes/interface-attributes) в справочной документации по Visual C++.  
  
## <a name="example"></a>Пример  

 В следующем примере показано определение библиотеки с помощью `GUID_ManagedName` атрибута.  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Требования  

 **Заголовок:** COR. h
