---
title: Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)
description: Узнайте, как использовать свойства чтения и записи в C#. Этот пример содержит два свойства, каждое из которых имеет методы доступа get и set, и поэтому свойства доступны для чтения и записи.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899026"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)

Свойства имеют все преимущества открытых членов данных, но не связаны с рисками незащищенного, неконтролируемого и несанкционированного доступа к данным объекта. Это достигается благодаря применению *методов доступа*, которые представляют собой особые методы для присвоения и извлечения значений базового члена данных. Метод доступа [set](../../language-reference/keywords/set.md) присваивает значения членам данных, а метод доступа [get](../../language-reference/keywords/get.md) извлекает их.  
  
 Это можно продемонстрировать на примере класса `Person`, который содержит два свойства: `Name` (string) и `Age` (int). Для обоих свойств реализованы методы доступа `get` и `set`, благодаря чему они доступны и для чтения, и для записи.  
  
## <a name="example"></a>Пример  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a>Отказоустойчивость  

 В предыдущем примере свойства `Name` и `Age` являются [открытыми](../../language-reference/keywords/public.md) и содержат одновременно методы доступа `get` и `set`. Благодаря этому объект может считывать эти свойства и записывать их. Тем не менее в некоторых случаях необходимо исключить один из методов доступа. Например, свойство без метода доступа `set` будет доступно только для чтения:  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 Кроме того, можно сделать один метод доступа открытым, а другой оставить частным или защищенным. Дополнительные сведения см. в разделе [Асимметричные методы доступа](./restricting-accessor-accessibility.md).  
  
 После объявления свойств их можно использовать так же, как поля класса. Это позволяет получить естественный синтаксис извлечения и установки значения свойства, как показано на примере следующих операторов:  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 Обратите внимание, что в методе `set` свойства доступна специальная переменная `value`. Она содержит значение, заданное пользователем, например:  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 Обратите внимание на простой синтаксис приращения свойства `Age` для объекта `Person`:  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 Если для моделирования свойств использовать отдельные методы `set` и `get`, аналогичный код может иметь следующий вид:  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 В этом примере переопределяется метод `ToString`:  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 Обратите внимание, что метод `ToString` не используется в этой программе явно. Он вызывается по умолчанию при вызове `WriteLine`.  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Свойства](./properties.md)
- [Классы и структуры](./index.md)
