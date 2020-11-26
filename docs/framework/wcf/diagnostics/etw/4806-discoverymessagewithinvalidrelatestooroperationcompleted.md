---
title: 4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted
ms.date: 03/30/2017
ms.assetid: 19e9a660-25f3-4332-b716-a12a59f2cbbb
ms.openlocfilehash: 46d71979e7b6bfcccc27064fd6fee626ea71dc1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242582"
---
# <a name="4806---discoverymessagewithinvalidrelatestooroperationcompleted"></a><span data-ttu-id="9f72b-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="9f72b-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="9f72b-103">Свойства</span><span class="sxs-lookup"><span data-stu-id="9f72b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f72b-104">ID</span><span class="sxs-lookup"><span data-stu-id="9f72b-104">ID</span></span>|<span data-ttu-id="9f72b-105">4806</span><span class="sxs-lookup"><span data-stu-id="9f72b-105">4806</span></span>|  
|<span data-ttu-id="9f72b-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="9f72b-106">Keywords</span></span>|<span data-ttu-id="9f72b-107">Обнаружение</span><span class="sxs-lookup"><span data-stu-id="9f72b-107">Discovery</span></span>|  
|<span data-ttu-id="9f72b-108">Level</span><span class="sxs-lookup"><span data-stu-id="9f72b-108">Level</span></span>|<span data-ttu-id="9f72b-109">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="9f72b-109">Warning</span></span>|  
|<span data-ttu-id="9f72b-110">Канал</span><span class="sxs-lookup"><span data-stu-id="9f72b-110">Channel</span></span>|<span data-ttu-id="9f72b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9f72b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9f72b-112">Описание</span><span class="sxs-lookup"><span data-stu-id="9f72b-112">Description</span></span>  

 <span data-ttu-id="9f72b-113">Это сообщение создается, если сообщение обнаружения было отброшено клиентом DiscoveryClient, поскольку выполнена соответствующая операция, либо значение relatesTo является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="9f72b-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because either the corresponding operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9f72b-114">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9f72b-114">Message</span></span>  

 <span data-ttu-id="9f72b-115">Сообщение %1 с messageId="%2" и relatesTo="%3" удалено клиентом DiscoveryClient, поскольку выполнена соответствующая операция %4 или значение relatesTo является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="9f72b-115">A %1 message with messageId='%2' and relatesTo='%3' was dropped by the DiscoveryClient because either the corresponding %4 operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9f72b-116">Подробнее</span><span class="sxs-lookup"><span data-stu-id="9f72b-116">Details</span></span>
