---
title: 'Устранение неполадок: невозможно установить приложение-службу'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: d04a0ddcef9ff7c31abd422f7f9fba34e804d2b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935415"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="27cba-102">Устранение неполадок: невозможно установить приложение-службу</span><span class="sxs-lookup"><span data-stu-id="27cba-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="27cba-103">Если приложение-служба не устанавливается надлежащим образом, убедитесь, что для свойства <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> класса службы задано значение, которое отображается в установщике этой службы.</span><span class="sxs-lookup"><span data-stu-id="27cba-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="27cba-104">Для правильной установки службы необходимо, чтобы эти значения совпадали.</span><span class="sxs-lookup"><span data-stu-id="27cba-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27cba-105">Сведения о ходе установки также можно найти в журналах установки.</span><span class="sxs-lookup"><span data-stu-id="27cba-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="27cba-106">Также убедитесь, что у вас не установлена другая служба с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="27cba-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="27cba-107">Для успешной установки необходимо, чтобы у каждой службы было уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="27cba-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cba-108">См. также</span><span class="sxs-lookup"><span data-stu-id="27cba-108">See also</span></span>

- [<span data-ttu-id="27cba-109">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="27cba-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
