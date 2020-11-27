---
title: Подделка
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249804"
---
# <a name="tampering"></a><span data-ttu-id="0f9e6-102">Подделка</span><span class="sxs-lookup"><span data-stu-id="0f9e6-102">Tampering</span></span>

<span data-ttu-id="0f9e6-103">*Незаконное* изменение — это процесс изменения сообщения или доставки сообщения, а также использование измененного сообщения для назначения, отличного от того, для чего оно предназначено.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="0f9e6-104">Не отключайте WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="0f9e6-104">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="0f9e6-105">Спецификация WS-Addressing расставляет заголовки адресов на каждом сообщении, по которым получатель сообщения проверяет отправителя сообщения.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="0f9e6-106">Чтобы отключить эту возможность, необходимо задать для свойства <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="0f9e6-107">Если для режима безопасности задано значение Message и WS-Addressing отключена, злоумышленник сможет отправить запрос клиента другой службе, при этом вторая служба не сможет определить, что сообщение поступило от исходного клиента.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="0f9e6-108">Фактически, первая служба при взаимодействии со второй может выдавать себя за клиента.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="0f9e6-109">Во избежание этого никогда не задавайте свойству <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> и старайтесь не использовать <xref:System.ServiceModel.Channels.MessageVersion>, например статическое свойство <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A>, задающее свойству <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f9e6-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9e6-110">См. также</span><span class="sxs-lookup"><span data-stu-id="0f9e6-110">See also</span></span>

- [<span data-ttu-id="0f9e6-111">Вопросы безопасности</span><span class="sxs-lookup"><span data-stu-id="0f9e6-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="0f9e6-112">Раскрытие информации</span><span class="sxs-lookup"><span data-stu-id="0f9e6-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="0f9e6-113">Несанкционированное получение привилегий</span><span class="sxs-lookup"><span data-stu-id="0f9e6-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="0f9e6-114">Отказ в обслуживании</span><span class="sxs-lookup"><span data-stu-id="0f9e6-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="0f9e6-115">Неподдерживаемые сценарии</span><span class="sxs-lookup"><span data-stu-id="0f9e6-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="0f9e6-116">Атаки с повторением</span><span class="sxs-lookup"><span data-stu-id="0f9e6-116">Replay Attacks</span></span>](replay-attacks.md)
