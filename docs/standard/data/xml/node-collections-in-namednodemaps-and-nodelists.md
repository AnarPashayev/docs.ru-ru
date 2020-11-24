---
title: Коллекции узлов в NamedNodeMap и NodeList
ms.date: 03/30/2017
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
ms.openlocfilehash: 2275d456253521caa43d843f3bc1a6b68bb77019
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820505"
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a><span data-ttu-id="8e740-102">Коллекции узлов в NamedNodeMap и NodeList</span><span class="sxs-lookup"><span data-stu-id="8e740-102">Node Collections in NamedNodeMaps and NodeLists</span></span>
<span data-ttu-id="8e740-103">Можно получить набор узлов и поместить его в упорядоченную или неупорядоченную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="8e740-103">You can retrieve a set of nodes and put it in an ordered or unordered collection.</span></span> <span data-ttu-id="8e740-104">Если набор узлов помещается в неупорядоченную коллекцию, он получает имя NamedNodeMap согласно спецификации консорциума W3C. В этом типе коллекции данные можно получить по имени или по индексу.</span><span class="sxs-lookup"><span data-stu-id="8e740-104">When putting a set of nodes into an unordered collection, the set is called a NamedNodeMap by the World Wide Web Consortium (W3C); you can retrieve the data by name or index in this type of collection.</span></span> <span data-ttu-id="8e740-105">Набор узлов, помещенный в упорядоченную коллекцию, согласно спецификации W3C называется NodeList, и данные можно получить по индексу, начинающемуся с нуля.</span><span class="sxs-lookup"><span data-stu-id="8e740-105">Putting a set of nodes in an ordered collection is called a NodeList by the W3C, and the data can be retrieved by a zero-based index.</span></span> <span data-ttu-id="8e740-106">Коллекции NamedNodeMap и NodeList описаны в документах W3C.</span><span class="sxs-lookup"><span data-stu-id="8e740-106">NamedNodeMaps and NodeLists are described by the W3C.</span></span> <span data-ttu-id="8e740-107">Реализацией коллекции NamedNodeMap в платформе Microsoft .NET Framework является класс **XmlNamedNodeMap**, а коллекция NodeList реализована в классе **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="8e740-107">The implementations in the Microsoft .NET Framework for the NamedNodeMap is the **XmlNamedNodeMap**, and the NodeList is implemented by the **XmlNodeList**.</span></span>  
  
 <span data-ttu-id="8e740-108">Дополнительные сведения о неупорядоченных коллекциях см. в руководстве по [получению неупорядоченных узлов по имени или индексу](unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="8e740-108">For information on the unordered collection, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span> <span data-ttu-id="8e740-109">Дополнительные сведения об упорядоченных коллекциях см. в руководстве по [получению упорядоченных узлов по индексу](ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="8e740-109">For information on the ordered collection, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e740-110">См. также</span><span class="sxs-lookup"><span data-stu-id="8e740-110">See also</span></span>

- [<span data-ttu-id="8e740-111">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="8e740-111">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
