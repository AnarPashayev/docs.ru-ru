---
title: Изменение элементов, атрибутов и узлов в дереве XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484230"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="20ba5-102">Изменение элементов, атрибутов и узлов в дереве XML</span><span class="sxs-lookup"><span data-stu-id="20ba5-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="20ba5-103">В следующей таблице приведена сводка методов и свойств, используемых для изменения элемента, его дочерних элементов или его атрибутов.</span><span class="sxs-lookup"><span data-stu-id="20ba5-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="20ba5-104">Следующие методы используются для изменения <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="20ba5-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="20ba5-105">Метод</span><span class="sxs-lookup"><span data-stu-id="20ba5-105">Method</span></span>|<span data-ttu-id="20ba5-106">Описание</span><span class="sxs-lookup"><span data-stu-id="20ba5-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-107">Заменяет элемент проанализированным XML.</span><span class="sxs-lookup"><span data-stu-id="20ba5-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-108">Удаляет все содержимое (дочерние узлы и атрибуты) элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-109">Удаляет атрибуты элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-110">Заменяет все содержимое (дочерние узлы и атрибуты) элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-111">Заменяет атрибуты элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-112">Устанавливает значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="20ba5-112">Sets the value of an attribute.</span></span> <span data-ttu-id="20ba5-113">Создает атрибут, если он не существует.</span><span class="sxs-lookup"><span data-stu-id="20ba5-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="20ba5-114">Если значение устанавливается в `null`, удаляет атрибут.</span><span class="sxs-lookup"><span data-stu-id="20ba5-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-115">Задает значение дочернего элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-115">Sets the value of a child element.</span></span> <span data-ttu-id="20ba5-116">Создает элемент, если он не существует.</span><span class="sxs-lookup"><span data-stu-id="20ba5-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="20ba5-117">Если значение устанавливается в `null`, удаляет элемент.</span><span class="sxs-lookup"><span data-stu-id="20ba5-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-118">Заменяет содержимое (дочерние узлы) элемента заданным текстом.</span><span class="sxs-lookup"><span data-stu-id="20ba5-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-119">Задает значение элемента.</span><span class="sxs-lookup"><span data-stu-id="20ba5-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="20ba5-120">Следующие методы используются для изменения <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20ba5-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="20ba5-121">Метод</span><span class="sxs-lookup"><span data-stu-id="20ba5-121">Method</span></span>|<span data-ttu-id="20ba5-122">Описание</span><span class="sxs-lookup"><span data-stu-id="20ba5-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-123">Устанавливает значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="20ba5-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-124">Устанавливает значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="20ba5-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="20ba5-125">Следующие методы предназначены для изменения <xref:System.Xml.Linq.XNode> (включая <xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="20ba5-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="20ba5-126">Метод</span><span class="sxs-lookup"><span data-stu-id="20ba5-126">Method</span></span>|<span data-ttu-id="20ba5-127">Описание</span><span class="sxs-lookup"><span data-stu-id="20ba5-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-128">Заменяет узел новым содержимым.</span><span class="sxs-lookup"><span data-stu-id="20ba5-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="20ba5-129">Следующие методы предназначены для изменения <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="20ba5-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="20ba5-130">Метод</span><span class="sxs-lookup"><span data-stu-id="20ba5-130">Method</span></span>|<span data-ttu-id="20ba5-131">Описание</span><span class="sxs-lookup"><span data-stu-id="20ba5-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="20ba5-132">Заменяет дочерние узлы новым содержимым.</span><span class="sxs-lookup"><span data-stu-id="20ba5-132">Replaces the children nodes with new content.</span></span>|  
