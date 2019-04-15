---
title: Справочник по C#. Область доступности
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 529d256a553c4000c77bcd5096db1a4d943874ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141756"
---
# <a name="accessibility-domain-c-reference"></a>Область доступности (Справочник по C#)
Область доступности члена определяет, в каких разделах программы может присутствовать ссылка на этот член. Если член вложен в другой тип, его область доступности определяется как [уровнем доступности](../../../csharp/language-reference/keywords/accessibility-levels.md) самого члена, так и областью доступности типа, непосредственно содержащего вложенный тип.  
  
 Область доступности типа верхнего уровня — это по крайней мере текст программы проекта, в котором он объявлен. То есть область включает в себя все исходные файлы данного проекта. Область доступности вложенного типа — это по крайней мере текст программы типа, в котором он объявлен. Таким образом, областью является тело типа, включающее все вложенные типы. Область доступности вложенного типа никогда не выходит за пределы области доступности содержащего его типа. Эти принципы продемонстрированы в приведенном ниже примере.  
  
## <a name="example"></a>Пример  
 Этот пример содержит тип верхнего уровня `T1` и два вложенных класса: `M1` и `M2`. Классы содержат поля, имеющие различную объявленную доступность. В методе `Main` после каждого оператора следует комментарий, указывающий область доступности для каждого члена. Обратите внимание, что операторы, ссылающиеся на недоступные члены, закомментированы. Если необходимо просмотреть сообщения об ошибках, выдаваемые компилятором при попытке обращения к недоступному члену, удаляйте комментарии по одному.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Ключевые слова C#](../../../csharp/language-reference/keywords/index.md)
- [Модификаторы доступа](../../../csharp/language-reference/keywords/access-modifiers.md)
- [Уровни доступности](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [Ограничения на использование уровней доступности](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [Модификаторы доступа](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
