---
title: проверка подлинности NTLM и Kerberos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: 2efb2d25e1b7566e3405a699be1795b37d549091
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183369"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="6ffec-102">проверка подлинности NTLM и Kerberos</span><span class="sxs-lookup"><span data-stu-id="6ffec-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="6ffec-103">При проверке подлинности NTLM и Kerberos по умолчанию используются учетные данные пользователя Microsoft Windows NT, связанные с вызывающим приложением, для проверки подлинности на сервере.</span><span class="sxs-lookup"><span data-stu-id="6ffec-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="6ffec-104">Если используется отличная от установленной по умолчанию проверка подлинности NTLM, приложение устанавливает тип проверки подлинности NTLM и использует объект <xref:System.Net.NetworkCredential> для передачи имени пользователя, пароля и домена узлу, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6ffec-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="6ffec-105">Приложения, которым требуется подключение к службам Интернета с использованием учетных данных пользователя приложения, могут использовать для этого учетные данные пользователя по умолчанию, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6ffec-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="6ffec-106">Модуль проверки подлинности с согласованием определяет, использует ли удаленный сервер проверку подлинности NTLM или Kerberos, после чего отправляет соответствующий ответ.</span><span class="sxs-lookup"><span data-stu-id="6ffec-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ffec-107">Проверка подлинности NTLM не работает через прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="6ffec-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffec-108">См. также</span><span class="sxs-lookup"><span data-stu-id="6ffec-108">See also</span></span>

- [<span data-ttu-id="6ffec-109">Обычная и дайджест-аутентификация</span><span class="sxs-lookup"><span data-stu-id="6ffec-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [<span data-ttu-id="6ffec-110">Аутентификация в Интернете</span><span class="sxs-lookup"><span data-stu-id="6ffec-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
