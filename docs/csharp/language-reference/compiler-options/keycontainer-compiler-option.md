---
title: -keycontainer (параметры компилятора C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302781"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="7317c-102">-keycontainer (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="7317c-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="7317c-103">Задает имя контейнера криптографического ключа.</span><span class="sxs-lookup"><span data-stu-id="7317c-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7317c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7317c-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="7317c-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="7317c-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="7317c-106">Имя контейнера ключа строгого имени.</span><span class="sxs-lookup"><span data-stu-id="7317c-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7317c-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="7317c-107">Remarks</span></span>  
 <span data-ttu-id="7317c-108">Когда используется параметр **-keycontainer**, компилятор создает совместно используемый компонент.</span><span class="sxs-lookup"><span data-stu-id="7317c-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="7317c-109">Компилятор вставляет открытый ключ из указанного контейнера в манифест сборки, после чего подписывает финальную сборку закрытым ключом.</span><span class="sxs-lookup"><span data-stu-id="7317c-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="7317c-110">Чтобы создать файл ключа, в командной строке введите `sn -k file`.</span><span class="sxs-lookup"><span data-stu-id="7317c-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="7317c-111">Команда `sn -i` устанавливает пару ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="7317c-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="7317c-112">Этот параметр не поддерживается, когда компилятор работает на CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7317c-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="7317c-113">Чтобы подписать сборку при компиляции на CoreCLR, используйте параметр [-keyfile](keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="7317c-114">При компиляции с параметром [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) имя файла ключа сохраняется в модуле и включается в сборку при компиляции этого модуля с параметром [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="7317c-115">Этот параметр можно также указать в исходном коде любого модуля MSIL в качестве настраиваемого атрибута (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="7317c-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="7317c-116">Также можно передать сведения о шифровании компилятору с помощью параметра [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="7317c-117">Если нужно добавить в манифест сборки открытый ключ, но при этом отложить подпись сборки до завершения ее тестирования, используйте параметр [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="7317c-118">Дополнительные сведения см. в разделах [Создание и использование сборок со строгими именами](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) и [Отложенная подпись сборки](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7317c-119">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7317c-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7317c-120">Данный параметр компилятора недоступен в среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7317c-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="7317c-121">Программный доступ к этому параметру компилятора возможен с помощью свойства <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="7317c-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7317c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7317c-122">See also</span></span>

- [<span data-ttu-id="7317c-123">-keyfile (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="7317c-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="7317c-124">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="7317c-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="7317c-125">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="7317c-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
