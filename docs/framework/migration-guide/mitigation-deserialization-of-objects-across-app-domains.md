---
title: Устранение рисков. Десериализация объектов между доменами приложений
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbde11672dc17f80a45defc0a55bcf841e83c324
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325076"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="873d8-102">Устранение рисков. Десериализация объектов между доменами приложений</span><span class="sxs-lookup"><span data-stu-id="873d8-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="873d8-103">В некоторых случаях, когда приложение использует два или большее количество доменов с разными базовыми папками приложения, при попытке выполнить десериализацию объектов в логическом контексте вызова между доменами приложения возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="873d8-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="873d8-104">Диагностика проблемы</span><span class="sxs-lookup"><span data-stu-id="873d8-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="873d8-105">Проблема возникает при следующей последовательности условий.</span><span class="sxs-lookup"><span data-stu-id="873d8-105">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="873d8-106">Приложение использует два или большее количество доменов приложений с разными базовыми папками приложения.</span><span class="sxs-lookup"><span data-stu-id="873d8-106">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="873d8-107">Некоторые типы явно добавляются в <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> путем вызова метода, например <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> или <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="873d8-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="873d8-108">Эти типы не отмечены как сериализуемые и не сохраняются в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="873d8-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="873d8-109">Затем код, выполняющийся в домене приложения не по умолчанию, пытается считать значение из файла конфигурации или использовать XML для десериализации объекта.</span><span class="sxs-lookup"><span data-stu-id="873d8-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="873d8-110">Чтобы считать значение из файла конфигурации или десериализовать объект, объект <xref:System.Xml.XmlReader> пытается получить доступ к системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="873d8-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="873d8-111">Если система конфигурации еще не была инициализирована, это следует сделать.</span><span class="sxs-lookup"><span data-stu-id="873d8-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="873d8-112">Это означает, что, помимо прочего, среда выполнения должна создать стабильный путь для системы конфигурации, следующим образом.</span><span class="sxs-lookup"><span data-stu-id="873d8-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1.  <span data-ttu-id="873d8-113">Выполняется поиск сведений о том, что домен приложений не является доменом по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="873d8-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2.  <span data-ttu-id="873d8-114">Среда выполнения пытается вычислить свидетельство наличия домена приложений не по умолчанию, основываясь на домене приложений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="873d8-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3.  <span data-ttu-id="873d8-115">Вызов для получения свидетельства о наличии домена приложений по умолчанию активирует вызов домена для нескольких приложений из домена приложений не по умолчанию в домен приложений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="873d8-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4.  <span data-ttu-id="873d8-116">Являясь частью контракта домена для нескольких приложений в .NET Framework, содержимое логического контекста вызова также должно быть маршалировано за пределами границ домена приложений.</span><span class="sxs-lookup"><span data-stu-id="873d8-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="873d8-117">Поскольку типы логическом контексте вызова не могут быть разрешены в домене приложений по умолчанию, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="873d8-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="873d8-118">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="873d8-118">Mitigation</span></span>  
 <span data-ttu-id="873d8-119">Чтобы устранить эту проблему, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="873d8-119">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="873d8-120">При возникновении исключения найдите вызов `get_Evidence` в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="873d8-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="873d8-121">Может возникать любое исключение из подмножества исключений, включая <xref:System.IO.FileNotFoundException> и <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="873d8-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="873d8-122">Найдите в приложении место, где в логический контекст вызова не добавляются никакие объекты, и добавьте следующий код.</span><span class="sxs-lookup"><span data-stu-id="873d8-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="873d8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="873d8-123">See also</span></span>

- [<span data-ttu-id="873d8-124">Изменения в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="873d8-124">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
