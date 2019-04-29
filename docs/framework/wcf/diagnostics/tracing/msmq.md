---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663730"
---
# <a name="msmq"></a><span data-ttu-id="7b448-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="7b448-102">MSMQ</span></span>
<span data-ttu-id="7b448-103">В приложениях MSMQ никакие дополнительные действия не передаются из очереди канала в MSMQ и обратно.</span><span class="sxs-lookup"><span data-stu-id="7b448-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="7b448-104">Кроме того, в рамках трассировки очереди канала во время операции Send отслеживаются идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует).</span><span class="sxs-lookup"><span data-stu-id="7b448-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="7b448-105">Идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует) отслеживаются в рамках трассировки очереди канала во время операции Receive.</span><span class="sxs-lookup"><span data-stu-id="7b448-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="7b448-106">Необходимые действия по передаче во время операции Receive выполняются так же, в любом другом транспорте (получение байт -> Обработка сообщения -> операция).</span><span class="sxs-lookup"><span data-stu-id="7b448-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
