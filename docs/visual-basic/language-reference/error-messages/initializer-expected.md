---
title: Ожидается инициализатор
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402841"
---
# <a name="initializer-expected"></a>Ожидается инициализатор
Предпринята попытка объявить экземпляр класса с помощью инициализатора объекта, в котором список инициализации пуст, как показано в следующем примере.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 В списке инициализаторов должно быть инициализировано по крайней мере одно поле или свойство, как показано в следующем примере.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Идентификатор ошибки:** BC30996  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Инициализируйте по крайней мере одно поле или свойство в инициализаторе или не используйте инициализатор объекта.  
  
## <a name="see-also"></a>См. также раздел

- [Инициализаторы объектов: именованные и анонимные типы](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Практическое руководство. Объявление объекта с помощью инициализатора объектов](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
