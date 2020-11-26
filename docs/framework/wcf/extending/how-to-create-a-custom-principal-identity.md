---
title: Практическое руководство. Создание пользовательского идентификатора участника
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 6c50d6b0ac2baa2dc61431af4afb8dca3860456a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249310"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="adf02-102">Практическое руководство. Создание пользовательского идентификатора участника</span><span class="sxs-lookup"><span data-stu-id="adf02-102">How to: Create a Custom Principal Identity</span></span>

<span data-ttu-id="adf02-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> является декларативным средством управления доступом к методам службы.</span><span class="sxs-lookup"><span data-stu-id="adf02-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="adf02-104">При использовании данного атрибута перечисление <xref:System.ServiceModel.Description.PrincipalPermissionMode> указывает режим выполнения проверки авторизации.</span><span class="sxs-lookup"><span data-stu-id="adf02-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="adf02-105">Если данный режим установлен как <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, пользователь может указать пользовательский класс <xref:System.Security.Principal.IPrincipal>, возвращаемый свойством <xref:System.Threading.Thread.CurrentPrincipal%2A>.</span><span class="sxs-lookup"><span data-stu-id="adf02-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="adf02-106">В данном разделе описан сценарий, в котором <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> используется совместно с пользовательской политикой авторизации и пользовательским участником.</span><span class="sxs-lookup"><span data-stu-id="adf02-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="adf02-107">Дополнительные сведения об использовании <xref:System.Security.Permissions.PrincipalPermissionAttribute> см. в разделе [как ограничить доступ с помощью класса PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="adf02-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adf02-108">Пример</span><span class="sxs-lookup"><span data-stu-id="adf02-108">Example</span></span>  

 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="adf02-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="adf02-109">Compiling the Code</span></span>  

 <span data-ttu-id="adf02-110">Для компиляции кода необходимы ссылки на следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="adf02-110">References to the following namespaces are needed to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="adf02-111">См. также</span><span class="sxs-lookup"><span data-stu-id="adf02-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="adf02-112">Практическое руководство. Использование поставщика ролей ASP.NET со службой</span><span class="sxs-lookup"><span data-stu-id="adf02-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="adf02-113">Практическое руководство. Ограничение доступа с использованием класса PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="adf02-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
