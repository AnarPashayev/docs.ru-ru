---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577309"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="f1364-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="f1364-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="f1364-103">Подтверждение безопасности с потенциальным соседним узлом завершилось неуспешно.</span><span class="sxs-lookup"><span data-stu-id="f1364-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f1364-104">Описание</span><span class="sxs-lookup"><span data-stu-id="f1364-104">Description</span></span>  
 <span data-ttu-id="f1364-105">Эта трассировка возникает при попытке установить безопасное соединение с соседним узлом.</span><span class="sxs-lookup"><span data-stu-id="f1364-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="f1364-106">Это может произойти из-за недостаточных или неправильных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="f1364-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="f1364-107">PeerChannel распознает один тип маркеров для строгой идентификации (сертификаты X.509), что обеспечивает строгую модель удостоверения, зависящую от типа проверки подлинности и авторизации, который может быть реализован.</span><span class="sxs-lookup"><span data-stu-id="f1364-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="f1364-108">PeerChannel также обеспечивает поддержку простых приложений посредством использования паролей.</span><span class="sxs-lookup"><span data-stu-id="f1364-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="f1364-109">Пароли могут использоваться только для разрешения входа в сеанс; их нельзя использовать для проверки подлинности сообщений.</span><span class="sxs-lookup"><span data-stu-id="f1364-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="f1364-110">Это связано с тем, что симметричный маркер, общий для участников одноранговой группы, сложно (и не следует) использовать для проверки подлинности источника.</span><span class="sxs-lookup"><span data-stu-id="f1364-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f1364-111">Диагностика</span><span class="sxs-lookup"><span data-stu-id="f1364-111">Troubleshooting</span></span>  
 <span data-ttu-id="f1364-112">Обеспечьте, чтобы все соседние узлы имели соответствующие учетные данные безопасности.</span><span class="sxs-lookup"><span data-stu-id="f1364-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1364-113">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="f1364-113">See also</span></span>

- [<span data-ttu-id="f1364-114">Безопасность одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="f1364-114">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="f1364-115">Трассировка</span><span class="sxs-lookup"><span data-stu-id="f1364-115">Tracing</span></span>](index.md)
- [<span data-ttu-id="f1364-116">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="f1364-116">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f1364-117">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="f1364-117">Administration and Diagnostics</span></span>](../index.md)
