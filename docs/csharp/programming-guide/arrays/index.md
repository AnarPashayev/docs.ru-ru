---
title: Руководство по программированию на C#. Массивы
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 258ade63ab7c9008f6c892ed109bf5ea5ab974f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584611"
---
# <a name="arrays-c-programming-guide"></a>Массивы (Руководство по программированию на C#)

В структуре данных массива можно хранить несколько переменных одного типа. Чтобы объявить массив, следует указать тип его элементов.  
  
 `type[] arrayName;`  
  
 В следующих примерах создаются одномерные массивы, многомерные массивы и массивы массивов:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Общие сведения о массивах

 Массив имеет следующие свойства:  
  
- Массив может быть [одномерным](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [многомерным](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) или [массивом массивов](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
- Количество измерений и длина каждого из измерений задаются, когда создается экземпляр массива. Эти значения нельзя изменить во время существования экземпляра.  
  
- Используемые по умолчанию значения числовых элементов массива равны нулю, и элементам ссылки присвоено значение NULL.  
  
- В массиве массивов элементы являются ссылочными типами и инициализируются значением `null`.  
  
- Массивы индексируются от нуля: массив с `n` элементами индексируется от `0` до `n-1`.  
  
- Элементы массива могут иметь любой тип, в том числе тип массива.  
  
- Типы массивов — это [ссылочные типы](../../../csharp/language-reference/keywords/reference-types.md), производные от абстрактного базового типа <xref:System.Array>. Поскольку этот тип реализует <xref:System.Collections.IEnumerable> и <xref:System.Collections.Generic.IEnumerable%601>, вы можете просматривать в цикле [foreach](../../../csharp/language-reference/keywords/foreach-in.md) любые массивы C#.  
  
## <a name="related-sections"></a>Связанные разделы  
  
- [Массивы как объекты](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
- [Использование оператора foreach с массивами](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
- [Передача массивов в качестве аргументов](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>Спецификация языка C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Коллекции](../../../csharp/programming-guide/concepts/collections.md)
