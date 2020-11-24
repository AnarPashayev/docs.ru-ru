---
title: Объекты расширения XSLT
ms.date: 03/30/2017
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: fa9c8e0baa11d8c0e2d8099a6ddbe1c43c4d6b7f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818314"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="3f5db-102">Объекты расширения XSLT</span><span class="sxs-lookup"><span data-stu-id="3f5db-102">XSLT Extension Objects</span></span>
<span data-ttu-id="3f5db-103">Объекты расширения используются для расширения функциональности таблиц стилей.</span><span class="sxs-lookup"><span data-stu-id="3f5db-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="3f5db-104">Объекты расширения обслуживаются классом <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="3f5db-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="3f5db-105">Далее приведены преимущества использования объекта расширения в сравнении с внедренными скриптами.</span><span class="sxs-lookup"><span data-stu-id="3f5db-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="3f5db-106">Обеспечивает улучшенную инкапсуляцию и повторное использование классов.</span><span class="sxs-lookup"><span data-stu-id="3f5db-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="3f5db-107">Уменьшает размер и улучшает обслуживание таблиц стилей.</span><span class="sxs-lookup"><span data-stu-id="3f5db-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="3f5db-108">Объекты расширения XSLT добавляются в объект <xref:System.Xml.Xsl.XsltArgumentList> с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f5db-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="3f5db-109">В это время с объектом расширения связываются полное имя и URI-код пространства имен.</span><span class="sxs-lookup"><span data-stu-id="3f5db-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f5db-110">Чтобы вызвать метод <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>, необходим набор разрешений FullTrust.</span><span class="sxs-lookup"><span data-stu-id="3f5db-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="3f5db-111">См. дополнительные сведения об [управлении доступом к коду](../../../framework/misc/code-access-security.md) и [именованных наборах разрешений](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3f5db-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3f5db-112">Объекты расширения возвращают один из четырех базовых типов данных XPath: `number`, `string`, `Boolean` и `node set`.</span><span class="sxs-lookup"><span data-stu-id="3f5db-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="3f5db-113">Любой метод, который определен с ключевым словом `params`, позволяющим передавать точно не установленное количество параметров, в настоящее время не поддерживается классом <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3f5db-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3f5db-114">Таблицы стилей XSLT, которые используют любой метод, определенный с ключевым словом `params`, не будут работать правильно.</span><span class="sxs-lookup"><span data-stu-id="3f5db-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="3f5db-115">Дополнительные сведения см. в руководстве по [params](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="3f5db-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="3f5db-116">Использование объекта расширения XSLT</span><span class="sxs-lookup"><span data-stu-id="3f5db-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="3f5db-117">Создайте объект <xref:System.Xml.Xsl.XsltArgumentList> и добавьте объект расширения с помощью метода <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f5db-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="3f5db-118">Вызовите объект расширения из таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="3f5db-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="3f5db-119">Передайте объект <xref:System.Xml.Xsl.XsltArgumentList> методу <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f5db-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5db-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3f5db-120">See also</span></span>

- [<span data-ttu-id="3f5db-121">Преобразования XSLT</span><span class="sxs-lookup"><span data-stu-id="3f5db-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="3f5db-122">Рекомендации по безопасности XSLT</span><span class="sxs-lookup"><span data-stu-id="3f5db-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
