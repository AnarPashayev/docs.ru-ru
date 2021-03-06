---
title: Устранимые ошибки XSLT
ms.date: 03/30/2017
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
ms.openlocfilehash: 2123ead435fe389693f3b141a26873700ba5647f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686778"
---
# <a name="recoverable-xslt-errors"></a>Устранимые ошибки XSLT

Рекомендация W3C по XSL-преобразованиям (XSLT) версии 1.0 включает в себя такие области, в которых поставщик реализации может решать, как обрабатывать ситуацию. Эти области считаются предоставленными на усмотрение поставщика. Например, в разделе 7.3 «Инструкции по обработке при создании» рекомендаций XSLT 1.0 указывается на ошибку, которая возникает, если при формировании экземпляра содержимого `xsl:processing-instruction` создаются узлы, отличные от текстовых. Для некоторых проблем в рекомендациях XSLT 1.0 указывается решение, которое следует принять, если обработчик решает устранить ошибку. Для проблемы, приведенной в разделе 7.3, W3C заявляет, что реализация может устранять эту ошибку, игнорируя узлы и их содержимое.  
  
## <a name="discretionary-behaviors"></a>Возможные поведения  

 В следующей таблице перечислены возможные поведения, разрешенные рекомендациями XSLT 1.0, и способы обработки этих поведений классом <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
- «Восстановление» указывает, что класс <xref:System.Xml.Xsl.XslCompiledTransform> устраняет эту ошибку. Событие <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> может быть использовано, чтобы сообщать о любых событиях из обработчика XSLT.  
  
- «Ошибка» указывает, что для этого условия формируется исключение.  
  
- Дополнительные сведения мс. в [рекомендациях консорциума W3C по преобразованиям XSLT версии 1.0](https://www.w3.org/TR/xslt) и [поправке к спецификации консорциума W3C по преобразованиям XSLT версии 1.0](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Условие XSLT|Раздел|Поведение XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Текстовый узел соответствует как `xsl:strip-space`, так и `xsl:preserve-space`.|3.4|Восстановление|  
|Исходный узел соответствует более одному правилу шаблона.|5.5|Восстановление|  
|URI-код пространства имен объявлен в качестве псевдонима для нескольких URI-кодов пространств имен, каждый из которых имеет одинаковый приоритет импорта.|7.1.1|Восстановление|  
|Атрибут `name` в узлах `xsl:attribute` и `xsl:element`, сформированный из значения атрибута, не является QName.|7.1.2, 7.1.3|Ошибка*|  
|Два набора атрибутов с одинаковым именем импорта и развернутым именем имеют общий атрибут, и не существует другого набора атрибутов, содержащего общий атрибут с таким же именем, имеющего большую важность.|7.1.4|Восстановление|  
|Добавление атрибута к элементу после добавления к нему потомков.|7.1.3|Ошибка*|  
|Создание атрибута с именем «xmlns»|7.1.3|Ошибка*|  
|Добавление атрибута к узлу, который не является элементом.|7.1.3|Ошибка*|  
|Создание узлов, отличных от текстовых узлов, во время создания экземпляра содержимого атрибута `xsl:attribute`.|7.1.3|Ошибка*|  
|Атрибут `name` в узле `xsl:processing-instruction` не содержит NCName и назначения инструкции по обработке.|7.3|Ошибка*|  
|При создании экземпляра содержимого `xsl:processing-instruction` создаются узлы, отличные от текстовых.|7.3|Ошибка*|  
|Результат создания экземпляра содержимого узла `xsl:processing-instruction` содержит строку "?>"|7.3|Восстановление|  
|Результат создания экземпляра содержимого узла `xsl:processing-instruction` содержит строку «--» или заканчивается на «-».|7.4|Восстановление|  
|Результат создания экземпляра содержимого узла `xsl:comment` создает узлы, отличные от текстовых узлов.|7.4|Ошибка*|  
|Шаблон внутри привязывающегося к переменной элемента возвращает узел атрибута или узел пространства имен.|11.2|Ошибка*|  
|Ошибка при извлечении ресурса по URI-идентификатору, переданного в функцию документа.|12.1|Ошибка|  
|URI-ссылка в функции документа содержит идентификатор фрагмента, и возникает ошибка обработки идентификатора фрагмента.|12.1|Восстановление*|  
|Существует несколько атрибутов с одним именем, но различными значениями, которые не являются именованными элементами cdata-section в узле `xsl:output` с тем же приоритетом импорта.|16|Восстановление|  
|Обработчик не поддерживает кодирование в атрибуте кодировки узла `xsl:output`.|16.1|Восстановление|  
|Отключение экранирования выхода для текстового узла, который используется в качестве узла, отличного от текстового, в дереве результатов.|16.4|Восстановление*|  
|Преобразование фрагмента дерева результатов в число или строку, если этот фрагмент содержит текстовый узел с включенным экранированием выходных данных.|16.4|Восстановление*|  
|Экранирование выхода отключено для символа, который нельзя представить в кодировке, используемой обработчиком XSLT для выхода.|16.4|Восстановление*|  
|Добавление узла пространства имен к элементу после того, как к нему был добавлен потомок или атрибуты.|поправка 25|Ошибка*|  
|Атрибут `value` в узле `xsl:number` имеет значение NAN, бесконечное или менее 0,5.|поправка 24|Восстановление|  
|Второй аргумент node-set функции документа пуст, поэтому URI-ссылка является относительной.|поправка 14|Восстановление|  
  
 <sup>*</sup>Это поведение отличается от класса <xref:System.Xml.Xsl.XslTransform>. См. дополнительные сведения по [реализации избирательного поведения в классе XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>См. также

- [Преобразования XSLT](xslt-transformations.md)
