---
title: Разрешение внешних ресурсов в ходе обработки XSLT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 5d50711eda266cecdb817c778f04aa845fa4c342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686648"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Разрешение внешних ресурсов в ходе обработки XSLT

Во время XSLT-преобразования может понадобиться несколько раз разрешать внешние ресурсы.  
  
## <a name="using-the-xmlresolver-class"></a>Использование класса XmlResolver  

 Класс <xref:System.Xml.XmlResolver> используется для разрешения внешних ресурсов. В следующей таблице описывается, когда класс <xref:System.Xml.XmlResolver> участвует в XSLT-обработке.  
  
|Задача XSLT|Зачем используется класс XmlResolver|  
|---------------|--------------------------------------|  
|Компиляция таблицы стилей|Разрешение URI таблицы стилей.<br /><br /> \- и -<br /><br /> Разрешение URI-ссылок в любых элементах `xsl:import` или `xsl:include`.|  
|Выполнение таблицы стилей.|Разрешение URI документа контекста.<br /><br /> \- и -<br /><br /> Разрешение URI-ссылок в любых функциях XSLT `document()`.|  
  
 Методы <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> и <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> включают в себя перегружаемые, принимающие объект <xref:System.Xml.XmlResolver> в качестве одного из аргументов. Если <xref:System.Xml.XmlResolver> не указан, используется <xref:System.Xml.XmlUrlResolver> по умолчанию без учетных данных.  
  
 Следующий список описывает, когда может потребоваться указать объект <xref:System.Xml.XmlResolver>:  
  
- Если процессу XSLT требуется доступ к сетевому ресурсу, требующему проверки подлинности, можно использовать <xref:System.Xml.XmlResolver> с необходимыми учетными данными.  
  
- Если необходимо ограничить ресурсы, к которым имеет доступ процесс XSLT, можно использовать <xref:System.Xml.XmlSecureResolver> с надлежащим набором разрешений. Использовать класс <xref:System.Xml.XmlSecureResolver> рекомендуется, если вам необходимо открыть ресурс, которым вы не управляете или к которому нет доверия.  
  
- Если необходимо настроить поведение особым образом, можно реализовать собственный класс <xref:System.Xml.XmlResolver> и использовать его для разрешения ресурсов.  
  
- Если необходимо убедиться в отсутствии доступа к внешним ресурсам, можно указать `null` в качестве значения аргумента <xref:System.Xml.XmlResolver>.  
  
## <a name="example"></a>Пример  

 В следующем примере компилируется таблица стилей, которая хранится на сетевом ресурсе. Объект <xref:System.Xml.XmlUrlResolver> задает учетные данные, необходимые для доступа к таблице стилей.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [Преобразования XSLT](xslt-transformations.md)
