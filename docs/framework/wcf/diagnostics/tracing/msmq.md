---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 7ef31a188e1564da47ea1e7323cdd4cd5ef5be60
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236680"
---
# <a name="msmq"></a><span data-ttu-id="8f2cd-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="8f2cd-102">MSMQ</span></span>

<span data-ttu-id="8f2cd-103">В приложениях MSMQ никакие дополнительные действия не передаются из очереди канала в MSMQ и обратно.</span><span class="sxs-lookup"><span data-stu-id="8f2cd-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="8f2cd-104">Кроме того, в рамках трассировки очереди канала во время операции Send отслеживаются идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует).</span><span class="sxs-lookup"><span data-stu-id="8f2cd-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="8f2cd-105">Идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует) отслеживаются в рамках трассировки очереди канала во время операции Receive.</span><span class="sxs-lookup"><span data-stu-id="8f2cd-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="8f2cd-106">Необходимые передачи для операции получения выполняются аналогично любому другому транспортному потоку (Receive Bytes->Process > операции).</span><span class="sxs-lookup"><span data-stu-id="8f2cd-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
