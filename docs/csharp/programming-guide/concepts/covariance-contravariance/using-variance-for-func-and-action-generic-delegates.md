---
title: Использование вариативности в универсальных методах-делегатах Func и Action (C#)
description: Узнайте об использовании ковариации и контрвариантности в универсальных делегатах Func и Action для формирования более гибкого кода.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 613470d7870aa6a917d19904a92e56f0e61f1ed9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176348"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Использование вариативности в универсальных методах-делегатах Func и Action (C#)

Эти примеры показывают, как обеспечить возможность многократного использования методов и сделать код более гибким, используя ковариацию и контравариацию в универсальных методах-делегатах `Func` и `Action`.  
  
 Дополнительные сведения о ковариации и контравариации см. в разделе [Вариативность в делегатах (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Использование методов-делегатов с параметрами ковариантного типа  

 Следующий пример иллюстрирует преимущества поддержки ковариации в универсальных методах-делегатах `Func`. Метод `FindByTitle` принимает параметр типа `String` и возвращает объект типа `Employee`. При этом данный метод можно назначить методу-делегату `Func<String, Person>`, поскольку `Employee` наследует `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Использование методов-делегатов с параметрами контравариантного типа  

 Следующий пример иллюстрирует преимущества поддержки контравариации в универсальных методах-делегатах `Action`. Метод `AddToContacts` принимает параметр типа `Person`. При этом данный метод можно назначить методу-делегату `Action<Employee>`, поскольку `Employee` наследует `Person`.  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a>См. также

- [Ковариация и контрвариантность (C#)](./index.md)
- [Универсальные шаблоны](../../../../standard/generics/index.md)
