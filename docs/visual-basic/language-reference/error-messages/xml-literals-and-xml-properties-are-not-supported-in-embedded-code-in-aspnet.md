---
title: XML литералы и XML свойства не поддерживаются во встроенном в ASP.NET коде
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 79be695478983055ae1f016cf841d733d3f4c430
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813929"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>XML литералы и XML свойства не поддерживаются во встроенном в ASP.NET коде
Литералы XML и свойства XML не поддерживаются во встроенном в ASP.NET коде. Чтобы использовать функции XML, переместите код для кода.  
  
 Литерал XML или свойство оси XML определен во встроенном коде (`<%= =>`) в файле ASP.NET.  
  
 **Идентификатор ошибки:** BC31200  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Переместите код, который содержит XML-литерала или свойства оси XML в файл фонового кода ASP.NET.  
  
## <a name="see-also"></a>См. также

- [XML-литералы](../../../visual-basic/language-reference/xml-literals/index.md)
- [Свойства оси XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
