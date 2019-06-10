---
title: abstract. Справочник по C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 64f650df0a9f6e6279e21b9cbd5ff444ef5c7a49
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758433"
---
# <a name="abstract-c-reference"></a>abstract (Справочник по C#)
Модификатор `abstract` указывает, что изменяемый элемент имеет отсутствующую или неполную реализацию. Модификатор abstract можно использовать с классами, методами, свойствами, индексаторами и событиями. Используйте модификатор `abstract` в объявлении класса, чтобы указать, что класс предназначен только для использования в качестве базового класса для других классов и не должен быть создан сам по себе. Элементы с пометкой abstract должны быть реализованы классами, производными от абстрактного класса.
  
## <a name="example"></a>Пример  
 В этом примере класс `Square` должен обеспечивать реализацию `GetArea`, поскольку является производным от класса `Shape`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Абстрактные классы предоставляют следующие возможности:  
  
- Создавать экземпляры абстрактного класса нельзя.  
  
- Абстрактный класс может содержать абстрактные методы и методы доступа.  
  
- Изменить абстрактный класс с модификатором [sealed](../../../csharp/language-reference/keywords/sealed.md) нельзя, так как два этих модификатора имеют взаимоисключающие значения. Модификатор `sealed` запрещает наследование класса, в то время как модификатор `abstract` указывает, что класс обязан иметь производные классы.  
  
- Неабстрактный класс, производный от абстрактного класса, должен включать фактические реализации всех наследуемых абстрактных методов и методов доступа.  
  
 Модификатор `abstract` в объявлении метода или свойства позволяет указать, что этот метод или свойство не содержат реализации.  
  
 Абстрактные методы предоставляют следующие возможности:  
  
- Абстрактный метод неявно представляет собой виртуальный метод.  
  
- Объявления абстрактных методов допускаются только в абстрактных классах.  
  
- Поскольку объявление абстрактного метода не предоставляет фактической реализации, тело метода отсутствует, а объявление метода заканчивается точкой с запятой, и фигурных скобок ({ }) после подписи нет. Например:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Реализация предоставляется методом [override](../../../csharp/language-reference/keywords/override.md), который является членом неабстрактного класса.  
  
- В объявлении абстрактного метода нельзя использовать [статические](../../../csharp/language-reference/keywords/static.md) или [виртуальные](../../../csharp/language-reference/keywords/virtual.md) модификаторы.  
  
 Действие абстрактных свойств аналогично абстрактным методам, за исключением отличий в синтаксисе объявлений и вызовов.  
  
- Использование модификатора `abstract` в статическом свойстве является недопустимым.  
  
- Абстрактное наследуемое свойство можно переопределить в производном классе, включив объявление свойства, которое использует модификатор [override](../../../csharp/language-reference/keywords/override.md).  
  
 Дополнительные сведения об абстрактных классах см. в разделе [Абстрактные и запечатанные классы и члены классов](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Абстрактный класс должен предоставлять реализацию для всех членов интерфейса.  
  
 Абстрактный класс, реализующий интерфейс, может сопоставлять методы интерфейса с абстрактными методами. Например:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Пример  
 В следующем примере класс `DerivedClass` является производным от абстрактного класса `BaseClass`. Абстрактный класс содержит абстрактный метод, `AbstractMethod`, и два абстрактных свойства, `X` и `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 В предыдущем примере при попытке создать экземпляр абстрактного класса с помощью оператора вида:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Выдается сообщение об ошибке, указывающее, что компилятор не может создать экземпляр абстрактного класса BaseClass.  
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Модификаторы](../../../csharp/language-reference/keywords/modifiers.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [Ключевые слова в C#](../../../csharp/language-reference/keywords/index.md)
