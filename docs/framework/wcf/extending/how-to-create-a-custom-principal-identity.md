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
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797071"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Практическое руководство. Создание пользовательского идентификатора участника
<xref:System.Security.Permissions.PrincipalPermissionAttribute> является декларативным средством управления доступом к методам службы. При использовании данного атрибута перечисление <xref:System.ServiceModel.Description.PrincipalPermissionMode> указывает режим выполнения проверки авторизации. Если данный режим установлен как <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, пользователь может указать пользовательский класс <xref:System.Security.Principal.IPrincipal>, возвращаемый свойством <xref:System.Threading.Thread.CurrentPrincipal%2A>. В данном разделе описан сценарий, в котором <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> используется совместно с пользовательской политикой авторизации и пользовательским участником.  
  
 Дополнительные сведения об использовании <xref:System.Security.Permissions.PrincipalPermissionAttribute>см. в разделе как [ Ограничьте доступ с помощью класса](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.  
  
## <a name="example"></a>Пример  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для компиляции кода необходимы ссылки на следующие пространства имен.  
  
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
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Практическое руководство. Использование поставщика ролей ASP.NET со службой](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Практическое руководство. Ограничение доступа с помощью класса PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
