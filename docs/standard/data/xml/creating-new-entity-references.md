---
title: Создание новых ссылок на сущности
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8d4e9e1e2dfd9882504c935912bcf235608485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965899"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="4df29-102">Создание новых ссылок на сущности</span><span class="sxs-lookup"><span data-stu-id="4df29-102">Creating New Entity References</span></span>
<span data-ttu-id="4df29-103">Метод **CreateEntityReference** создает новый узел **XmlEntityReference**.</span><span class="sxs-lookup"><span data-stu-id="4df29-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="4df29-104">Модель DOM определяет, было ли уже декларировано имя сущности, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="4df29-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="4df29-105">Если было, то дочерние узлы узла **XmlEntityReference** копируются из узла декларации сущности.</span><span class="sxs-lookup"><span data-stu-id="4df29-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="4df29-106">Если совпадающая декларация сущности отсутствует, пустой текстовый узел прикрепляется как единственный дочерний узел узла ссылки на сущность.</span><span class="sxs-lookup"><span data-stu-id="4df29-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="4df29-107">Так как дочерние узлы узла **XmlEntityReference** являются копиями других узлов, они доступны только для чтения и не могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="4df29-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="4df29-108">При копировании узлов в области в точке ссылки на сущность может быть пространство имен.</span><span class="sxs-lookup"><span data-stu-id="4df29-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="4df29-109">Это пространство имен влияет на конфигурацию всех формируемых элементов или узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="4df29-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4df29-110">Модель DOM добавляет дочерние узлы к узлу **EntityReference** только при вставке в документ узла **EntityReference**.</span><span class="sxs-lookup"><span data-stu-id="4df29-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="4df29-111">Вновь созданные узлы **EntityReference** не имеют дочерних узлов.</span><span class="sxs-lookup"><span data-stu-id="4df29-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="4df29-112">Хотя класс **XmlDataDocument** является производным от класса **XmlDocument**, класс **XmlDataDocument** не поддерживает создание ссылок на сущности.</span><span class="sxs-lookup"><span data-stu-id="4df29-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="4df29-113">Это связано с тем, что дочерние узлы **EntityReference** доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="4df29-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="4df29-114">Дочерние узлы узла **EntityReference** могут принадлежать к нескольким областям.</span><span class="sxs-lookup"><span data-stu-id="4df29-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="4df29-115">В этом случае часть строки, связанная с областью, которая содержит часть узла **EntityReference**, будет доступна только для чтения.</span><span class="sxs-lookup"><span data-stu-id="4df29-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df29-116">См. также</span><span class="sxs-lookup"><span data-stu-id="4df29-116">See also</span></span>

- [<span data-ttu-id="4df29-117">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="4df29-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
