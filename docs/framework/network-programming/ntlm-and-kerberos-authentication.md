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
# <a name="ntlm-and-kerberos-authentication"></a>проверка подлинности NTLM и Kerberos
При проверке подлинности NTLM и Kerberos по умолчанию используются учетные данные пользователя Microsoft Windows NT, связанные с вызывающим приложением, для проверки подлинности на сервере. Если используется отличная от установленной по умолчанию проверка подлинности NTLM, приложение устанавливает тип проверки подлинности NTLM и использует объект <xref:System.Net.NetworkCredential> для передачи имени пользователя, пароля и домена узлу, как показано в следующем примере.  
  
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
  
 Приложения, которым требуется подключение к службам Интернета с использованием учетных данных пользователя приложения, могут использовать для этого учетные данные пользователя по умолчанию, как показано в следующем примере.  
  
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
  
 Модуль проверки подлинности с согласованием определяет, использует ли удаленный сервер проверку подлинности NTLM или Kerberos, после чего отправляет соответствующий ответ.  
  
> [!NOTE]
>  Проверка подлинности NTLM не работает через прокси-сервер.  
  
## <a name="see-also"></a>См. также

- [Обычная и дайджест-аутентификация](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [Аутентификация в Интернете](../../../docs/framework/network-programming/internet-authentication.md)
