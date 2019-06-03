---
title: Руководство по программированию на C#. Универсальные методы-делегаты
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423505"
---
# <a name="generic-delegates-c-programming-guide"></a>Универсальные делегаты. (Руководство по программированию на C#)
[Делегат](../../../csharp/language-reference/keywords/delegate.md) может определять собственные параметры типа. В коде, который ссылается на универсальный делегат, можно указать аргумент типа для создания закрытого сконструированного типа. Это будет аналогично созданию экземпляра универсального класса или вызову универсального метода, как показано в следующем примере:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 В C# версии 2.0 представлена новая функция группового преобразования методов, которая применяется как к конкретным, так и к универсальным типам делегатов, и позволяет записать приведенную выше строку с использованием упрощенного синтаксиса:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Делегаты, определенные в универсальном классе, могут использовать параметры класса универсального типа таким же образом, как это делают методы класса.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 В коде, который ссылается на делегат, необходимо указать аргумент типа содержащего класса, как показано ниже:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Универсальные делегаты особенно полезны при определении событий, основанных на типовых шаблонах разработки, поскольку аргумент отправителя может быть строго типизирован и больше не требует приведения к <xref:System.Object> и из него.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Collections.Generic>
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Введение в универсальные шаблоны](../../../csharp/programming-guide/generics/index.md)
- [Универсальные методы](../../../csharp/programming-guide/generics/generic-methods.md)
- [Универсальные классы](../../../csharp/programming-guide/generics/generic-classes.md)
- [Универсальные интерфейсы](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [Делегаты](../../../csharp/programming-guide/delegates/index.md)
- [Универсальные шаблоны](~/docs/standard/generics/index.md)
