---
title: Динамические обновления объектов NodeList и NamedNodeMap
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 58dfde94c2f37b0a09ee795b9df20296c9f86da6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710977"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="542cf-102">Динамические обновления объектов NodeList и NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="542cf-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="542cf-103">Так как объекты **XmlNodeList** и **XmlNamedNodeMap** содержат набор узлов, но XML-документ загружается в память и изменяется, консорциум W3C требует, чтобы такие объекты, содержащие наборы узлов, были динамическими.</span><span class="sxs-lookup"><span data-stu-id="542cf-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="542cf-104">Это значит, что изменение базового документа должно вызывать изменение этих двух объектов.</span><span class="sxs-lookup"><span data-stu-id="542cf-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="542cf-105">Таким образом, если у вас есть объект **XmlNodeList**, содержащий все дочерние элементы некоторого элемента (например, элемента X), и затем в документ добавляется дополнительный элемент Q, дочерний относительно элемента X, то в коллекцию объекта **XmlNodeList** также должен быть добавлен новый элемент Q.</span><span class="sxs-lookup"><span data-stu-id="542cf-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="542cf-106">Правило работает и в обратном направлении:</span><span class="sxs-lookup"><span data-stu-id="542cf-106">The same is true in reverse.</span></span> <span data-ttu-id="542cf-107">если узел добавляется в объект **XmlNodeList**, необходимо обновить базовый документ.</span><span class="sxs-lookup"><span data-stu-id="542cf-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542cf-108">См. также</span><span class="sxs-lookup"><span data-stu-id="542cf-108">See also</span></span>

- [<span data-ttu-id="542cf-109">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="542cf-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
