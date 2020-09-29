---
title: Практическое руководство. Определение абстрактных свойств (руководство по программированию на C#)
description: Узнайте, как определять абстрактные свойства в C#. Объявление абстрактного свойства означает, что класс поддерживает свойство. Методы доступа реализуются в производных классах.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 01af1446097bbed25874b45d57a5dde85ae63891
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199163"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Практическое руководство. Определение абстрактных свойств (руководство по программированию на C#)

В следующем примере показано, как определять [абстрактные](../../language-reference/keywords/abstract.md) свойства. В объявлении абстрактного свойства не предоставляется реализация методов доступа к свойству. В нем объявляется, что класс поддерживает свойства, однако реализация методов доступа к ним передается в производные классы. В следующем примере показано, как реализовать абстрактные свойства, наследуемые от базового класса.  
  
 Этот пример включает три файла, каждый из которых компилируется отдельно в сборку, на которую задаются ссылки при последующей компиляции:  
  
- abstractshape.cs: класс `Shape`, который содержит абстрактное свойство `Area`.  
  
- shapes.cs: подклассы класса `Shape`.  
  
- shapetest.cs: тестовая программа для отображения областей некоторых объектов, производных от `Shape`.  
  
 Чтобы скомпилировать этот пример, используйте следующую команду:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 При этом будет создан исполняемый файл shapetest.exe.  
  
## <a name="example"></a>Пример  

 В этом файле объявляется класс `Shape`, который содержит свойство `Area` типа `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Модификаторы свойства помещаются в само объявление свойства. Пример:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- При объявлении абстрактного свойства, такого как `Area` в этом примере, вы просто указываете используемые методы доступа, но не реализуете их. В этом примере используется только метод доступа [get](../../language-reference/keywords/get.md), поэтому свойство будет доступно только для чтения.  
  
## <a name="example"></a>Пример  

 В следующем коде представлены три подкласса класса `Shape` и демонстрируется, как они переопределяют свойство `Area` для получения его собственной реализации.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Пример  

 В следующем коде показана тестовая программа, которая создает несколько производных от `Shape` объектов и печатает их области.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Классы и структуры](./index.md)
- [Абстрактные и запечатанные классы и члены классов](./abstract-and-sealed-classes-and-class-members.md)
- [Свойства](./properties.md)
