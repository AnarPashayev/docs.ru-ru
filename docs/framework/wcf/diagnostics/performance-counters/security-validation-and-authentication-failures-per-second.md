---
title: Количество сбоев при проверке безопасности и проверке подлинности в секунду
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 7d680e9a5b03943fdec212c509b6d80a2d60246c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559139"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="501ed-102">Количество сбоев при проверке безопасности и проверке подлинности в секунду</span><span class="sxs-lookup"><span data-stu-id="501ed-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="501ed-103">Имя счетчика: Security Validation and Authentication Failures Per Second.</span><span class="sxs-lookup"><span data-stu-id="501ed-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="501ed-104">Описание</span><span class="sxs-lookup"><span data-stu-id="501ed-104">Description</span></span>  
 <span data-ttu-id="501ed-105">Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized".</span><span class="sxs-lookup"><span data-stu-id="501ed-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="501ed-106">К таким проблемам относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="501ed-106">Such problems include:</span></span>  
  
- <span data-ttu-id="501ed-107">Невозможно прочесть в этом сообщении маркер клиента.</span><span class="sxs-lookup"><span data-stu-id="501ed-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="501ed-108">Маркер клиента не прошел проверку подлинности (например, неправильный пароль).</span><span class="sxs-lookup"><span data-stu-id="501ed-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="501ed-109">Сбой при проверке подписи (например, сообщение было искажено).</span><span class="sxs-lookup"><span data-stu-id="501ed-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="501ed-110">Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="501ed-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="501ed-111">Произошел сбой при расшифровке.</span><span class="sxs-lookup"><span data-stu-id="501ed-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="501ed-112">В сообщении отсутствуют некоторые обязательные элементы (например, отсутствует отметка времени или зашифрованный блок данных).</span><span class="sxs-lookup"><span data-stu-id="501ed-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="501ed-113">Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.</span><span class="sxs-lookup"><span data-stu-id="501ed-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="501ed-114">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="501ed-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="501ed-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="501ed-115">(N1-N0)/((D1-D0)/F)</span></span>
