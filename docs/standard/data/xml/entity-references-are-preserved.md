---
title: Сохраняемые ссылки на сущности
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 484eb5c874c6de05acae7dcd87a477c186b81482
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687272"
---
# <a name="entity-references-are-preserved"></a>Сохраняемые ссылки на сущности

Если ссылки на сущности не разворачиваются, а сохраняются, модель XML DOM строит узел **XmlEntityReference**, когда обнаруживает ссылку на сущность.  
  
 Используя следующий XML-код,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Модель DOM строит узел **XmlEntityReference**, когда встречает ссылку `&publisher;`. Узел **XmlEntityReference** содержит дочерние узлы, которые копируются из содержимого декларации сущности. В предыдущем примере присутствует текст в декларации сущности, поэтому узел **XmlText** создается как дочерний узел для узла ссылки на сущность.  
  
 ![Древовидная структура для сохраненных ссылок на сущности](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Древовидная структура для сохраняемых ссылок на сущности  
  
 Дочерние узлы **XmlEntityReference** являются копиями всех дочерних узлов, созданных из узла **XmlEntity** в момент, когда была обнаружена декларация сущности.  
  
> [!NOTE]
> Узлы, копируемые из **XmlEntity**, не всегда остаются точными копиями после помещения в узел ссылки на сущность. Могут существовать пространства имен, лежащие в области узла ссылки на сущность, которые оказывают влияние на конечную конфигурацию дочерних узлов.  
  
 По умолчанию сохраняются сущности общего вида, такие как `&abc;`, и всегда создаются узлы **XmlEntityReference**.  
  
## <a name="see-also"></a>См. также

- [Модель объектов документов XML (DOM)](xml-document-object-model-dom.md)
