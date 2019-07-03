---
title: Отложенная подпись сборки
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb055285af7365536f7e1ad7c7d9290e51be50db
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832870"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="39717-102">Отложенная подпись сборки</span><span class="sxs-lookup"><span data-stu-id="39717-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="39717-103">Организация может располагать тщательно оберегаемой парой ключей, повседневный доступ к которой разработчикам не предоставляется.</span><span class="sxs-lookup"><span data-stu-id="39717-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="39717-104">Открытый ключ часто является доступным, но доступ к закрытому ключу предоставляется лишь отдельным лицам.</span><span class="sxs-lookup"><span data-stu-id="39717-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="39717-105">При разработке сборок со строгими именами каждая сборка, в которой имеется ссылка на другую сборку со строгим именем, должна содержать маркер открытого ключа, использованного для присвоения строгого имени второй сборке.</span><span class="sxs-lookup"><span data-stu-id="39717-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="39717-106">Данный подход требует, чтобы открытый ключ был доступен во время процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="39717-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="39717-107">Во время компоновки сборки можно использовать отложенную или частичную подпись для того, чтобы зарезервировать в переносимом исполняемом файле (PE-файле) место для подписи строгого имени, а применение полноценной подписи отложить и выполнить на следующем этапе (обычно непосредственно перед поставкой сборки).</span><span class="sxs-lookup"><span data-stu-id="39717-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="39717-108">В приведенной ниже последовательности шагов отражены основные этапы отложенного подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="39717-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1. <span data-ttu-id="39717-109">Получите открытый ключ, входящий в состав пары ключей, у организации, отвечающей за окончательную подпись.</span><span class="sxs-lookup"><span data-stu-id="39717-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="39717-110">Обычно этот ключ предоставляется в форме SNK-файла, который может быть создан с помощью [программы строгих имен (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md), входящей в состав пакета средств разработки программного обеспечения для Windows.</span><span class="sxs-lookup"><span data-stu-id="39717-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the Windows Software Development Kit (SDK).</span></span>  
  
2. <span data-ttu-id="39717-111">Включите в исходный код сборки два указанных ниже настраиваемых атрибута из пространства имен <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="39717-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    - <span data-ttu-id="39717-112">Атрибут <xref:System.Reflection.AssemblyKeyFileAttribute>, который передает имя файла, содержащего открытый ключ, своему конструктору в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="39717-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    - <span data-ttu-id="39717-113">Атрибут<xref:System.Reflection.AssemblyDelaySignAttribute>, который указывает, что используется отложенная подпись, передавая значение **true** своему конструктору в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="39717-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="39717-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="39717-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. <span data-ttu-id="39717-115">Компилятор вставляет открытый ключ в манифест сборки и резервирует в PE-файле место для полной подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="39717-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="39717-116">При компоновке сборки должен использоваться подлинный открытый ключ, чтобы другие сборки, ссылающиеся на данную сборку, могли получить этот ключ и сохранить его в своих ссылках на сборку.</span><span class="sxs-lookup"><span data-stu-id="39717-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4. <span data-ttu-id="39717-117">Так как подпись строгого имени сборки пока некорректна, необходимо отключить проверку этой подписи.</span><span class="sxs-lookup"><span data-stu-id="39717-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="39717-118">Это можно сделать с помощью программы строгих имен, используя параметр **–Vr**.</span><span class="sxs-lookup"><span data-stu-id="39717-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="39717-119">В следующем примере производится отключение проверки сборки с именем `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="39717-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="39717-120">Чтобы отключить проверку на платформах, где нельзя запустить средства для работы со строгими именами, такими как микропроцессоры Advanced RISC Machine (ARM), используйте параметр **–Vk** для создания файла реестра.</span><span class="sxs-lookup"><span data-stu-id="39717-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="39717-121">Импортируйте файл реестра в реестр на компьютере, где нужно отключить проверку.</span><span class="sxs-lookup"><span data-stu-id="39717-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="39717-122">В следующем примере создается файл реестра для `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="39717-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="39717-123">С помощью параметра **–Vr** или **–Vk** можно дополнительно включить SNK-файл для подписывания ключа теста.</span><span class="sxs-lookup"><span data-stu-id="39717-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="39717-124">Строгие имена не являются средством обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="39717-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="39717-125">Они служат только для однозначной идентификации.</span><span class="sxs-lookup"><span data-stu-id="39717-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="39717-126">Если во время разработки с помощью Visual Studio на компьютере с 64-разрядной архитектурой используется отложенная подпись и сборка компилируется для конфигурации **Любой ЦП**, возможно, параметр **-Vr** потребуется применить дважды.</span><span class="sxs-lookup"><span data-stu-id="39717-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="39717-127">(В Visual Studio конфигурация **Любой ЦП** является значением свойства сборки **Целевая платформа**; при компиляции из командной строки это параметр по умолчанию.) Чтобы запустить приложение из командной строки или в проводнике, используйте 64-разрядную версию [Sn.exe (средство строгих имен)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) для применения к сборке параметра **-Vr**.</span><span class="sxs-lookup"><span data-stu-id="39717-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="39717-128">Чтобы загрузить сборку в Visual Studio во время разработки (например, если сборка содержит компоненты, используемые другими сборками в приложении), необходимо использовать 32-разрядную версию средства работы со строгими именами.</span><span class="sxs-lookup"><span data-stu-id="39717-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="39717-129">Причина заключается в том, что JIT-компилятор компилирует сборки в 64-разрядный машинный код, когда сборка запускается из командной строки, и в 32-разрядный машинный код, когда сборка загружается в среду во время разработки.</span><span class="sxs-lookup"><span data-stu-id="39717-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5. <span data-ttu-id="39717-130">Позже, обычно сразу перед поставкой, необходимо отправить сборку в подписывающий центр организации для подписания действующим строгим именем с помощью параметра программы строгих имен **–R**.</span><span class="sxs-lookup"><span data-stu-id="39717-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="39717-131">В следующем примере сборка с именем `myAssembly.dll` подписывается строгим именем с помощью пары ключей `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="39717-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39717-132">См. также</span><span class="sxs-lookup"><span data-stu-id="39717-132">See also</span></span>

- [<span data-ttu-id="39717-133">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="39717-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="39717-134">Практическое руководство. Создание пары открытого и закрытого ключей</span><span class="sxs-lookup"><span data-stu-id="39717-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="39717-135">Sn.exe (средство строгих имен)</span><span class="sxs-lookup"><span data-stu-id="39717-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="39717-136">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="39717-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
