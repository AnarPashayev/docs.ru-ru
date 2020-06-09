---
title: Согласование безопасности и тайм-ауты
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601001"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="b362c-102">Согласование безопасности и тайм-ауты</span><span class="sxs-lookup"><span data-stu-id="b362c-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="b362c-103">При проверке подлинности клиентов и служб Windows Communication Foundation (WCF) поддерживает режим, в котором учетные данные службы согласовываются как часть проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="b362c-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="b362c-104">В таких случаях между клиентом и службой может происходить взаимный обмен информацией для распространения учетных данных службы клиенту.</span><span class="sxs-lookup"><span data-stu-id="b362c-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="b362c-105">Продолжительность этого взаимного обмена определяется свойством <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="b362c-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="b362c-106">Однако это время ожидания применяется, только если обмен информацией фактически продолжается дольше одного цикла "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="b362c-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="b362c-107">Если согласование завершается за один цикл, время ожидания не используется.</span><span class="sxs-lookup"><span data-stu-id="b362c-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b362c-108">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="b362c-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="b362c-109">Практическое руководство. Установка максимальной разницы в показаниях часов</span><span class="sxs-lookup"><span data-stu-id="b362c-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
