---
title: Рекомендуется использовать XML-теги для комментариев документации (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940866"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Рекомендуется использовать XML-теги для комментариев документации (Visual Basic)
Компилятор Visual Basic может обработать комментарии документации в коде в XML-файл. Дополнительные средства можно использовать для обработки XML-файла в документации.  
  
 Комментарии XML разрешены в конструкциях кода, таких как типы и члены типов. Для разделяемых типов только одна часть типа может содержать комментарии XML, несмотря на то, что нет никаких ограничений на комментирование его членов.  
  
> [!NOTE]
>  Комментарии документации не может применяться к пространствам имен. Причина заключается в одно пространство имен может охватывать несколько сборок, что не все сборки должны загружаться в то же время.  
  
 Компилятор обрабатывает любой тег, допустимый XML-код. Следующие теги предоставляют часто используемые возможности в документации для пользователей.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<исключение >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<включить >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<PARAM >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<разрешение >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<см. в разделе >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> компилятор проверяет синтаксис.)  
  
> [!NOTE]
>  В текст комментария документации угловые скобки, используйте `&lt;` и `&gt;`. Например, строка `"&lt;text in angle brackets&gt;"` будет отображаться как `<text in angle brackets>`.  
  
## <a name="see-also"></a>См. также

- [Документирование кода с помощью XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Практическое руководство. Создание XML-документации](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
