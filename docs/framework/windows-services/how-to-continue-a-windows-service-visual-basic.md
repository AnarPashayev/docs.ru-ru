---
title: Практическое руководство. Возобновление выполнения службы Windows (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: c9a783c0e7df39381ad1d9a8fedd7419605fd241
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935544"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="47ef5-102">Практическое руководство. Возобновление выполнения службы Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ef5-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="47ef5-103">В этом примере для возобновления работы службы администрирования IIS на локальном компьютере используется компонент <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="47ef5-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ef5-104">Пример</span><span class="sxs-lookup"><span data-stu-id="47ef5-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="47ef5-105">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="47ef5-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="47ef5-106">В средстве выбора фрагмента кода он расположен в разделе **Операционная система Windows > Службы Windows**.</span><span class="sxs-lookup"><span data-stu-id="47ef5-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="47ef5-107">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="47ef5-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47ef5-108">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="47ef5-108">Compiling the Code</span></span>  
 <span data-ttu-id="47ef5-109">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="47ef5-109">This example requires:</span></span>  
  
- <span data-ttu-id="47ef5-110">Ссылка в проекте на System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="47ef5-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="47ef5-111">Доступ к членам пространства имен <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="47ef5-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="47ef5-112">Добавьте оператор `Imports`, если в коде не используются полные имена членов.</span><span class="sxs-lookup"><span data-stu-id="47ef5-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="47ef5-113">Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="47ef5-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="47ef5-114">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="47ef5-114">Robust Programming</span></span>  
 <span data-ttu-id="47ef5-115">Свойство <xref:System.ServiceProcess.ServiceController.MachineName%2A> класса <xref:System.ServiceProcess.ServiceController> — это по умолчанию локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="47ef5-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="47ef5-116">Чтобы указать ссылку на службы Windows на другом компьютере, укажите в свойстве <xref:System.ServiceProcess.ServiceController.MachineName%2A> имя другого компьютера.</span><span class="sxs-lookup"><span data-stu-id="47ef5-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="47ef5-117">Пока контроллер службы находится в состоянии <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, вызывать для службы метод <xref:System.ServiceProcess.ServiceController.Continue%2A> нельзя.</span><span class="sxs-lookup"><span data-stu-id="47ef5-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="47ef5-118">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="47ef5-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="47ef5-119">Не удалось возобновить работу службы.</span><span class="sxs-lookup"><span data-stu-id="47ef5-119">The service cannot be resumed.</span></span> <span data-ttu-id="47ef5-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="47ef5-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="47ef5-121">Произошла ошибка при обращении к API-интерфейсу системы.</span><span class="sxs-lookup"><span data-stu-id="47ef5-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="47ef5-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="47ef5-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="47ef5-123">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47ef5-123">.NET Framework Security</span></span>  
 <span data-ttu-id="47ef5-124">Чтобы ограничить управление службами на компьютере, с помощью перечисления <xref:System.ServiceProcess.ServiceControllerPermissionAccess> настройте в классе <xref:System.ServiceProcess.ServiceControllerPermission> необходимые разрешения.</span><span class="sxs-lookup"><span data-stu-id="47ef5-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="47ef5-125">Чтобы ограничить доступ к сведениям о службе, с помощью перечисления <xref:System.Security.Permissions.PermissionState> настройте в классе <xref:System.Security.Permissions.SecurityPermission> необходимые разрешения.</span><span class="sxs-lookup"><span data-stu-id="47ef5-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ef5-126">См. также</span><span class="sxs-lookup"><span data-stu-id="47ef5-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="47ef5-127">Практическое руководство. Приостановка выполнения службы Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ef5-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
