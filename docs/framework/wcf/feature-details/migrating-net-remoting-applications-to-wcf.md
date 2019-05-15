---
title: Перенос приложений удаленного взаимодействия .NET на платформу WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592865"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="9c7c7-102">Перенос приложений удаленного взаимодействия .NET на платформу WCF</span><span class="sxs-lookup"><span data-stu-id="9c7c7-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="9c7c7-103">**Этот раздел относится к технологии прежних версий, которая сохраняется для обеспечения обратной совместимости с существующими приложениями и не рекомендуется для разработки новых приложений. Теперь распределенные приложения следует разрабатывать с использованием WCF.**</span><span class="sxs-lookup"><span data-stu-id="9c7c7-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="9c7c7-104">Существует два способа, чтобы воспользоваться преимуществами WCF с существующими приложениями удаленного взаимодействия .NET: интеграция и миграция.</span><span class="sxs-lookup"><span data-stu-id="9c7c7-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="9c7c7-105">Интеграция позволяет иметь .NET Remoting 2.0 и WCF, выполняющиеся одновременно, что позволяет одновременно предоставлять же бизнес-объектов посредством обеих технологий без необходимости изменения существующего кода .NET Remoting 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c7c7-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="9c7c7-106">Интеграция требует, что выполняется в .NET Framework 2.0 или более.</span><span class="sxs-lookup"><span data-stu-id="9c7c7-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="9c7c7-107">Если вы хотите воспользоваться преимуществами функций WCF и не обязательно передачи совместимости с системами Remoting 2.0, можно перенести всей службы WCF.</span><span class="sxs-lookup"><span data-stu-id="9c7c7-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="9c7c7-108">Миграция из .NET Remoting 2.0 на платформу WCF требует внесения изменений в интерфейс удаленного объекта и его параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9c7c7-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="9c7c7-109">В этих разделах рассматриваются [из удаленного взаимодействия на платформу Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="9c7c7-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7c7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="9c7c7-110">See also</span></span>

- [<span data-ttu-id="9c7c7-111">Концептуальный обзор</span><span class="sxs-lookup"><span data-stu-id="9c7c7-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
