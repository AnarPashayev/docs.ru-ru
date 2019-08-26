---
title: Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: bf0d6ae329c5a09986a4a7bf641fe6820387ff22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916560"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="f9181-102">Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9181-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="f9181-103">Хотя `My.Computer.Registry` должно хватать для удовлетворения основных потребностей при программировании в реестре, можно также использовать классы <xref:Microsoft.Win32.Registry> и <xref:Microsoft.Win32.RegistryKey> в пространстве имен <xref:Microsoft.Win32> платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9181-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="f9181-104">Разделы в классе Registry</span><span class="sxs-lookup"><span data-stu-id="f9181-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="f9181-105">Класс <xref:Microsoft.Win32.Registry> предоставляет основные разделы реестра, которые можно использовать для доступа к подразделам и их значениям.</span><span class="sxs-lookup"><span data-stu-id="f9181-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="f9181-106">Сами основные разделы доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="f9181-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="f9181-107">В следующей таблице перечислены и описаны семь разделов, предоставляемых классом <xref:Microsoft.Win32.Registry>.</span><span class="sxs-lookup"><span data-stu-id="f9181-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="f9181-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="f9181-108">**Key**</span></span>|<span data-ttu-id="f9181-109">**Описание**</span><span class="sxs-lookup"><span data-stu-id="f9181-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="f9181-110">Определяет типы документов и свойства, связанные с этими типами.</span><span class="sxs-lookup"><span data-stu-id="f9181-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="f9181-111">Содержит сведения о конфигурации оборудования, не относящиеся к пользователю.</span><span class="sxs-lookup"><span data-stu-id="f9181-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="f9181-112">Содержит сведения о текущих настройках пользователя, таких как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="f9181-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="f9181-113">Содержит динамические данные реестра, например, используемые драйверами виртуальных устройств.</span><span class="sxs-lookup"><span data-stu-id="f9181-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="f9181-114">Включает в себя пять подразделов (оборудование, SAM, безопасность, программное обеспечение и система), содержащих данные о конфигурации для локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="f9181-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="f9181-115">Содержит сведения о производительности для компонентов программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="f9181-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="f9181-116">Содержит сведения о настройках пользователя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f9181-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="f9181-117">Безопаснее записывать данные для текущего пользователя (<xref:Microsoft.Win32.Registry.CurrentUser>), чем для локального компьютера (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="f9181-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="f9181-118">Условие, которое обычно называют "захватом", возникает, если создаваемый вами раздел уже был создан другим, возможно вредоносным, процессом.</span><span class="sxs-lookup"><span data-stu-id="f9181-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="f9181-119">Чтобы предотвратить это, используйте такой метод, как <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, который возвращает `Nothing`, если ключ еще не существует.</span><span class="sxs-lookup"><span data-stu-id="f9181-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="f9181-120">Чтение значения из реестра</span><span class="sxs-lookup"><span data-stu-id="f9181-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="f9181-121">В следующем коде показано, как считать строку из раздела HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f9181-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="f9181-122">Следующий код считывает, увеличивает, а затем записывает строку в раздел HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f9181-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="f9181-123">См. также</span><span class="sxs-lookup"><span data-stu-id="f9181-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="f9181-124">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="f9181-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f9181-125">Чтение данных из реестра и запись в реестр</span><span class="sxs-lookup"><span data-stu-id="f9181-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="f9181-126">Безопасность и реестр</span><span class="sxs-lookup"><span data-stu-id="f9181-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
