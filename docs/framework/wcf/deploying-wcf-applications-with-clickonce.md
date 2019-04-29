---
title: Развертывание приложений WCF с помощью ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 1820b00aa903633750f74f319f9cf8038ba2b043
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785097"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="81aa5-102">Развертывание приложений WCF с помощью ClickOnce</span><span class="sxs-lookup"><span data-stu-id="81aa5-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="81aa5-103">Клиентские приложения, использующие Windows Communication Foundation (WCF) могут быть развернуты с помощью технологии ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="81aa5-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="81aa5-104">Эта технология позволяет им использовать преимущества средств защиты среды выполнения, предоставляемых управлением доступом для кода, если приложения снабжены цифровой подписью с надежным сертификатом.</span><span class="sxs-lookup"><span data-stu-id="81aa5-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="81aa5-105">Сертификат, используемый для подписывания приложения ClickOnce, должен располагаться в хранилище надежных издателей, а локальная политика безопасности на клиентском компьютере должна быть настроена таким образом, чтобы предоставлять разрешения полного доверия приложениям, подписанным с использованием сертификата издателя.</span><span class="sxs-lookup"><span data-stu-id="81aa5-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="81aa5-106">Сведения о настройке приложений ClickOnce и надежных издателей, см. в разделе [Настройка надежных издателей ClickOnce](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="81aa5-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81aa5-107">См. также</span><span class="sxs-lookup"><span data-stu-id="81aa5-107">See also</span></span>

- [<span data-ttu-id="81aa5-108">Общие сведения о развертывании доверенных приложений</span><span class="sxs-lookup"><span data-stu-id="81aa5-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)
- [<span data-ttu-id="81aa5-109">Развертывание ClickOnce для Windows Forms в приложения</span><span class="sxs-lookup"><span data-stu-id="81aa5-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)
