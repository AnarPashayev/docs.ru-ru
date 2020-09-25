---
title: <claimTypeRequirements> для <message>;
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: e70b036fddbc706c8c16de9a0834140f600aa5ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173800"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="fa199-102">\<claimTypeRequirements> для \<message>;</span><span class="sxs-lookup"><span data-stu-id="fa199-102">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="fa199-103">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="fa199-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="fa199-104">Коллекция используется службой, чтобы задать обязательные и необязательные утверждения, которые должны содержаться в выданном маркере, используемом клиентом для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="fa199-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="fa199-105">Служба предоставляет обязательные типы утверждений в метаданных, если публикация WDSL включена, но WCF не требует, чтобы выданный маркер содержал заданные типы утверждений.</span><span class="sxs-lookup"><span data-stu-id="fa199-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="fa199-106">Службы, для которых необходимо принудительное наличие обязательных типов утверждений, должны использовать политику авторизации.</span><span class="sxs-lookup"><span data-stu-id="fa199-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="fa199-107">В федеративных клиентах эта коллекция содержит список обязательных и необязательных утверждений, который отправляется службе маркеров безопасности в запросе клиента для выданного маркера.</span><span class="sxs-lookup"><span data-stu-id="fa199-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa199-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fa199-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
