---
title: 'Пример регулярных выражений: Поиск ссылок HREF'
description: Вы можете изучить пример регулярных выражений в .NET. В этом примере показан поиск в строке входных данных и вывод всех значений атрибута href, а также их позиций.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
ms.openlocfilehash: 36273901ac9afb762ac70ee5d6dcd80ff0ede11d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583496"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Пример регулярных выражений: Поиск ссылок HREF
В следующем примере показаны поиск и вывод всех значений href="...", а также их позиций в строке.  
  
## <a name="the-regex-object"></a>Объект Regex  
 Поскольку метод `DumpHRefs` может быть вызван из пользовательского кода несколько раз, он использует метод `static` (`Shared` в Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. Это позволяет обработчику регулярных выражений кэшировать регулярное выражение и избежать дополнительной нагрузки, связанной с созданием объекта <xref:System.Text.RegularExpressions.Regex> при каждом вызове метода. Затем объект <xref:System.Text.RegularExpressions.Match> выполняет итерацию по всем совпадениям в строке.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 В следующем примере показан вызов метода `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Возможные интерпретации шаблона регулярного выражения `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` показаны в следующей таблице.  
  
|Шаблон|Описание|  
|-------------|-----------------|  
|`href`|Совпадение с литеральной строкой "href". Сопоставление не учитывает регистр.|  
|`\s*`|Соответствует нулю или нескольким символам пробела.|  
|`=`|Соответствует знаку равенства.|  
|`\s*`|Соответствует нулю или нескольким символам пробела.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Соответствует одному из следующих символов, не назначая результат группе записи.<br /> <ul><li><p>Кавычки или апостроф, за которыми следует ноль или несколько любых символов, кроме кавычек или апострофа, за которыми следуют кавычки или апостроф. В этот шаблон включена группа с именем `1`.</p></li><li><p>Один или более символов, которые не являются пробелами. В этот шаблон включена группа с именем `1`.</p></li></ul>|  
|`(?<1>[^"']*)`|Присвоить ноль или несколько любых символов, кроме кавычки или апострофа, группе записи `1`.|  
|`(?<1>\S+)`|Присвоить один или несколько символов, отличных от пробела, захваченной группе с именем `1`.|  
  
## <a name="match-result-class"></a>Класс результата поиска  
 Результаты поиска сохраняются в классе <xref:System.Text.RegularExpressions.Match>, который предоставляет доступ ко всем подстрокам, извлеченным в ходе поиска. Также он запоминает искомую строку и использованное регулярное выражение, что позволяет вызвать метод <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> для продолжения поиска с того места, где закончился предыдущий.  
  
## <a name="explicitly-named-captures"></a>Явно именованные шаблоны  
 В обычных регулярных выражениях круглые скобки, обозначающие отдельные шаблоны, автоматически последовательно нумеруются. В связи с этим возникают две проблемы. Во-первых, если регулярное выражение изменяется из-за вставки или удаления пары круглых скобок, все части кода, которые ссылаются на нумерованные шаблоны, необходимо переписать, чтобы отразить новую нумерацию. Во-вторых, вследствие того, что различные пары круглых скобок часто используются для определения двух альтернативных выражений для поиска, трудно определить, какое из двух выражений в действительности вернуло результат.  
  
 Для решения этих проблем класс <xref:System.Text.RegularExpressions.Regex> поддерживает синтаксис `(?<name>…)`, с помощью которого найденное совпадение можно сохранить в указанной ячейке (которой можно присвоить строковое имя или целочисленное обозначение; числа при этом работают быстрее). Таким образом, если совпадение будет найдено повторно, оно попадет в ту же ячейку. В случае конфликта успешным является то совпадение, которое было помещено в ячейку последним. (Однако доступен и полный список совпадений для одной ячейки. Подробнее см. описание коллекции <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.)  
  
## <a name="see-also"></a>См. также

- [Регулярные выражения .NET](regular-expressions.md)
