---
title: Практическое руководство. Переопределение метода ToString (руководство по программированию на C#)
description: Узнайте, как переопределить метод ToString в C#. Каждый класс или структура наследует класс Object и получает метод ToString, который возвращает строковое представление этого объекта.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: de56ea10ea15f497f9375c2449acbae1d0c8978a
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099267"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Практическое руководство. Переопределение метода ToString (руководство по программированию на C#)

Каждый класс или структура в языке C# неявно наследует класс <xref:System.Object>. Поэтому каждый объект в языке C# получает метод <xref:System.Object.ToString%2A>, который возвращает строковое представление данного объекта. Например, все переменные типа `int` имеют метод `ToString`, который позволяет им возвращать их содержимое в виде строки:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 При создании пользовательского класса или структуры необходимо переопределить метод <xref:System.Object.ToString%2A>, чтобы передать информацию о типе клиентскому коду.  
  
 Дополнительные сведения об использовании строк форматирования и других типов пользовательского форматирования с методом `ToString` см. в разделе [Типы форматирования](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> При принятии решения относительно того, какая информация должна будет предоставляться посредством этого метода, подумайте, будет ли создаваемый класс или структура когда-либо использоваться ненадежным кодом. Постарайтесь не предоставлять информацию, которая может быть использована вредоносным кодом.  
  
Чтобы переопределить метод `ToString` в классе или структуре, выполните указанные ниже действия.
  
1. Объявите метод `ToString` со следующими модификаторами и типом возвращаемого значения:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Реализуйте этот метод таким образом, чтобы он возвращал строку.  
  
     В приведенном ниже примере возвращается не только имя класса, но и специфические данные для конкретного экземпляра класса.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Метод `ToString` можно проверить с помощью показанного ниже кода.  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>См. также

- <xref:System.IFormattable>
- [Руководство по программированию на C#](../index.md)
- [Классы и структуры](./index.md)
- [Строки](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Типы форматирования](../../../standard/base-types/formatting-types.md)
