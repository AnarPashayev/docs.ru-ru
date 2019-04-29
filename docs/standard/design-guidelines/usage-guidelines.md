---
title: Рекомендации по использованию
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778811"
---
# <a name="usage-guidelines"></a><span data-ttu-id="d1c30-102">Рекомендации по использованию</span><span class="sxs-lookup"><span data-stu-id="d1c30-102">Usage guidelines</span></span>

<span data-ttu-id="d1c30-103">Этот раздел содержит рекомендации по использованию распространенных типов в общедоступных API.</span><span class="sxs-lookup"><span data-stu-id="d1c30-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="d1c30-104">Он имеет дело с прямое использование объектов встроенных типов Framework (например, атрибуты сериализации) и перегрузка общих операторов.</span><span class="sxs-lookup"><span data-stu-id="d1c30-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="d1c30-105"><xref:System.IDisposable?displayProperty=nameWithType> Интерфейс в этом разделе не рассматривается, но рассматривается в [шаблон Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) раздел.</span><span class="sxs-lookup"><span data-stu-id="d1c30-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="d1c30-106">Инструкции и Дополнительные сведения о других типичных, встроенных типов .NET Framework, см. в разделе справочные разделы, в следующих целях: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1c30-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d1c30-107">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="d1c30-107">In this section</span></span>

[<span data-ttu-id="d1c30-108">Массивы</span><span class="sxs-lookup"><span data-stu-id="d1c30-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="d1c30-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d1c30-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="d1c30-110">Коллекции</span><span class="sxs-lookup"><span data-stu-id="d1c30-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="d1c30-111">Сериализация</span><span class="sxs-lookup"><span data-stu-id="d1c30-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="d1c30-112">Использование System.Xml</span><span class="sxs-lookup"><span data-stu-id="d1c30-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="d1c30-113">Операторы равенства</span><span class="sxs-lookup"><span data-stu-id="d1c30-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="d1c30-114">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="d1c30-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="d1c30-115">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d1c30-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d1c30-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d1c30-116">See also</span></span>

- [<span data-ttu-id="d1c30-117">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="d1c30-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
