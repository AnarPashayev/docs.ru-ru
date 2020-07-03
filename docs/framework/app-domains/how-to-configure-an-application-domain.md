---
title: Практическое руководство. Настройка домена приложения
description: Настройка домена приложения в .NET. Сведения о настройке нового домена приложения среде CLR можно предоставить с помощью класса AppDomainSetup.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: 27afcf161bec74143fafb5dceb20597de73e23d4
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104856"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="2f693-104">Практическое руководство. Настройка домена приложения</span><span class="sxs-lookup"><span data-stu-id="2f693-104">How to: Configure an Application Domain</span></span>
<span data-ttu-id="2f693-105">Сведения о настройке нового домена приложения среде CLR можно предоставить с помощью класса <xref:System.AppDomainSetup>.</span><span class="sxs-lookup"><span data-stu-id="2f693-105">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="2f693-106">При создании собственных доменов приложений наиболее важным свойством является <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f693-106">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="2f693-107">Другие свойства **AppDomainSetup** используются главным образом узлами среды выполнения для настройки определенного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="2f693-107">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="2f693-108">Свойство **ApplicationBase** определяет корневой каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="2f693-108">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="2f693-109">Когда среде выполнения требуется разрешить запрос о типе, она выполняет поиск сборки, содержащей тип в каталоге, заданном свойством **ApplicationBase**.</span><span class="sxs-lookup"><span data-stu-id="2f693-109">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f693-110">Новый домен приложения наследует только свойство **ApplicationBase** своего создателя.</span><span class="sxs-lookup"><span data-stu-id="2f693-110">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="2f693-111">В следующем примере создается экземпляр класса **AppDomainSetup**, используемого для создания домена приложения, производится вывод данных на консоль и затем выгрузка домена приложения.</span><span class="sxs-lookup"><span data-stu-id="2f693-111">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f693-112">Пример</span><span class="sxs-lookup"><span data-stu-id="2f693-112">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2f693-113">См. также</span><span class="sxs-lookup"><span data-stu-id="2f693-113">See also</span></span>

- [<span data-ttu-id="2f693-114">Программирование с использованием доменов приложений</span><span class="sxs-lookup"><span data-stu-id="2f693-114">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="2f693-115">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="2f693-115">Using Application Domains</span></span>](use.md)
