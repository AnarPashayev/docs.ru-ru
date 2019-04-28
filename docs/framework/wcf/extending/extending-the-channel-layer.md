---
title: Расширение уровня каналов
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: e60d8ef1a5191c6407b01eb1a2456a06aeeb1914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857913"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="fcb3d-102">Расширение уровня каналов</span><span class="sxs-lookup"><span data-stu-id="fcb3d-102">Extending the Channel Layer</span></span>
<span data-ttu-id="fcb3d-103">Уровень канала отвечает за обмен сообщениями между клиентами и службами.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="fcb3d-104">Расширения каналов могут реализовывать новые функциональные возможности протокола, такие как безопасность, или транспортные функциональные возможности, такие как реализация нового сетевого транспорта для передачи сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcb3d-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="fcb3d-105">In This Section</span></span>  
 [<span data-ttu-id="fcb3d-106">Общие сведения о модели каналов</span><span class="sxs-lookup"><span data-stu-id="fcb3d-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="fcb3d-107">Высокоуровневый обзор каналов, предоставляемых ими функций и принципов работы в службе и клиентском приложении.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="fcb3d-108">Разработка каналов</span><span class="sxs-lookup"><span data-stu-id="fcb3d-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="fcb3d-109">Подробное описание ролей, которые выполняют различные типы инфраструктуры каналов, принципов работы модуля состояния и жизненного цикла состояния, способов обработки исключений и ошибок, способов реализации поддержки метаданных и принципов работы каналов с кодировщиками сообщений.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="fcb3d-110">Пользовательские кодировщики</span><span class="sxs-lookup"><span data-stu-id="fcb3d-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="fcb3d-111">Описание роли, которую выполняют кодировщики сообщений в каналах, и способов ее создания.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="fcb3d-112">Пользовательские обновления потоков</span><span class="sxs-lookup"><span data-stu-id="fcb3d-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="fcb3d-113">Описание процесса обновления потоков, предоставляемых поточно-ориентированными транспортами.</span><span class="sxs-lookup"><span data-stu-id="fcb3d-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
