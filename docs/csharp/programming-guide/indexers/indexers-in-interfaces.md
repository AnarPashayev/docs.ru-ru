---
title: Руководство по программированию на C#. Индексаторы в интерфейсах
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: f277758a10b045a6365adfe931ce95d64eb8e445
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608578"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Индексаторы в интерфейсах (Руководство по программированию в C#)
Индексаторы можно объявлять для [интерфейса](../../../csharp/language-reference/keywords/interface.md). Методы доступа индексаторов интерфейса отличаются от методов доступа индексаторов [класса](../../../csharp/language-reference/keywords/class.md) следующим образом:  
  
- Методы доступа интерфейса не используют модификаторы.  
  
- Метод доступа интерфейса не имеет тела.  
  
 Таким образом, методы доступа нужны, чтобы указать, доступен ли индексатор для чтения и записи, только для чтения или только для записи.  
  
 Ниже показан пример метода доступа индексатора для интерфейса:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Сигнатура индексатора должна отличаться от сигнатур любых других индексаторов, объявленных в том же интерфейсе.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует реализацию индексаторов интерфейса.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 В приведенном выше примере можно использовать явную реализацию члена интерфейса с помощью полного имени члена интерфейса. Например:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Тем не менее полное имя требуется только в целях устранения неоднозначности, если класс реализует более одного интерфейса с одинаковой сигнатурой индексатора. Например, если класс `Employee` реализует два интерфейса (`ICitizen` и `IEmployee`), оба из которых имеют одинаковую сигнатуру индексатора, требуется явная реализация члена интерфейса. Это значит, что потребуется следующее объявление индексатора:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 реализует индексатор в интерфейсе `IEmployee`, тогда как следующее объявление:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 реализует индексатор в интерфейсе `ICitizen`.  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Индексаторы](../../../csharp/programming-guide/indexers/index.md)
- [Свойства](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Интерфейсы](../../../csharp/programming-guide/interfaces/index.md)
