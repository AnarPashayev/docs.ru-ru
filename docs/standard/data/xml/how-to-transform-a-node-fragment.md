---
title: Практическое руководство. Преобразование фрагмента узла
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: f5eb8e7826dd132fd46f6f476335416e7dd03269
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722691"
---
# <a name="how-to-transform-a-node-fragment"></a>Практическое руководство. Преобразование фрагмента узла

Во время преобразования данных, содержащихся в объекте <xref:System.Xml.XmlDocument> или <xref:System.Xml.XPath.XPathDocument>, преобразования XSLT применяются к документу в целом. Иными словами, если передать узел, отличный от корневого узла документа, это не помешает процессу преобразования обратиться ко всем узлам загружаемого документа. Чтобы преобразовать фрагмент узла, необходимо создать отдельный объект, содержащий только этот фрагмент, и передать его методу <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-transform-a-node-fragment"></a>Преобразование фрагмента узла  
  
1. Создайте объект, содержащий исходный документ.  
  
2. Определите расположение фрагмента узла для преобразования.  
  
3. Создайте отдельный объект, содержащий только фрагмент узла.  
  
4. Передайте фрагмент узла методу <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="example"></a>Пример  

 В следующем примере преобразуется фрагмент узла, а результаты выводятся на консоль.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Входные данные  
  
##### <a name="booksxml"></a>books.xml  

 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>single.xsl  

 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Вывод  

 Заголовок книги — The Confidence Man.  
  
## <a name="see-also"></a>См. также

- [Использование класса XslCompiledTransform](using-the-xslcompiledtransform-class.md)
