---
title: Практическое руководство. Получение свойств объекта системы печати без отражения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335203"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="2e288-102">Практическое руководство. Получение свойств объекта системы печати без отражения</span><span class="sxs-lookup"><span data-stu-id="2e288-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="2e288-103">Использование отражения для перечисления свойств (и типов этих свойств) в объекте может снизить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="2e288-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="2e288-104"><xref:System.Printing.IndexedProperties> Пространство имен предоставляет средства для получение этой информации с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="2e288-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e288-105">Пример</span><span class="sxs-lookup"><span data-stu-id="2e288-105">Example</span></span>  
 <span data-ttu-id="2e288-106">Ниже приведены действия для этого.</span><span class="sxs-lookup"><span data-stu-id="2e288-106">The steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="2e288-107">Создайте экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="2e288-107">Create an instance of the type.</span></span> <span data-ttu-id="2e288-108">В следующем примере тип является <xref:System.Printing.PrintQueue> тип, который поставляется с Microsoft .NET Framework, но почти идентичный код должен работать для типов, производных от <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="2e288-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2. <span data-ttu-id="2e288-109">Создание <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> из типа <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e288-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="2e288-110"><xref:System.Collections.DictionaryEntry.Value%2A> Каждой записи в этом словаре является объектом одного из типов, производных от <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="2e288-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3. <span data-ttu-id="2e288-111">Перечисление элементов словаря.</span><span class="sxs-lookup"><span data-stu-id="2e288-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="2e288-112">Для каждого из них выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="2e288-112">For each of them, do the following.</span></span>  
  
4. <span data-ttu-id="2e288-113">Приведите значение каждого элемента в <xref:System.Printing.IndexedProperties.PrintProperty> и использовать его для создания <xref:System.Printing.IndexedProperties.PrintProperty> объекта.</span><span class="sxs-lookup"><span data-stu-id="2e288-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5. <span data-ttu-id="2e288-114">Получить тип <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> каждого из <xref:System.Printing.IndexedProperties.PrintProperty> объекта.</span><span class="sxs-lookup"><span data-stu-id="2e288-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="2e288-115">См. также</span><span class="sxs-lookup"><span data-stu-id="2e288-115">See also</span></span>

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="2e288-116">Документы в WPF</span><span class="sxs-lookup"><span data-stu-id="2e288-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="2e288-117">Общие сведения о печати</span><span class="sxs-lookup"><span data-stu-id="2e288-117">Printing Overview</span></span>](printing-overview.md)
