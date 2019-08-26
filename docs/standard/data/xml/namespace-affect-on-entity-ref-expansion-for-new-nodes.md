---
title: Влияние пространства имен на раскрытие ссылок на сущности для новых узлов, содержащих элементы и атрибуты
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a92f1b08719c926e6384c220e3695de26dbb4fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967331"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="c0a51-102">Влияние пространства имен на раскрытие ссылок на сущности для новых узлов, содержащих элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="c0a51-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="c0a51-103">Так как содержимое декларации сущности может содержать абсолютно все, существует вероятность, что содержимое может содержать элемент типа `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="c0a51-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="c0a51-104">Во время анализа XML элемент `&aname;` не раскрывается своим замененным содержимым.</span><span class="sxs-lookup"><span data-stu-id="c0a51-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="c0a51-105">Раскрывание XML не выполняется, так как разрешение пространства имен для элемента не может произойти, пока узел не размещается в документе.</span><span class="sxs-lookup"><span data-stu-id="c0a51-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="c0a51-106">До этого времени неизвестно, какое пространство имен расположено в области.</span><span class="sxs-lookup"><span data-stu-id="c0a51-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="c0a51-107">Когда узел помещается в документ, происходит разрешение пространства имен и результирующее содержимое сущности анализируется внутри соответствующих узлов.</span><span class="sxs-lookup"><span data-stu-id="c0a51-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0a51-108">После того, как раскрывание произошло в заново созданном узле ссылки сущности, оно никогда повторно не происходит.</span><span class="sxs-lookup"><span data-stu-id="c0a51-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="c0a51-109">Поэтому пространства имен, используемые в тексте замены для элемента, привязываются во время задания родительского узла.</span><span class="sxs-lookup"><span data-stu-id="c0a51-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="c0a51-110">Тем не менее пространство имен может быть изменено для существующих узлов ссылки сущности, и они могут быть вставлены куда-либо еще, или для узлов ссылки сущности, которые копируются с помощью метода **CloneNode**.</span><span class="sxs-lookup"><span data-stu-id="c0a51-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a51-111">См. также</span><span class="sxs-lookup"><span data-stu-id="c0a51-111">See also</span></span>

- [<span data-ttu-id="c0a51-112">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="c0a51-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
