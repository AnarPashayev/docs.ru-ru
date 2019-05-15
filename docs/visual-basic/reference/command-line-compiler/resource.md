---
title: -ресурсов (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 2d7da572ecc8d7d20917eaa244eefbcd7abe61f0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589512"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="c4a17-102">-ресурсов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a17-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="c4a17-103">Внедряет управляемый ресурс в сборку.</span><span class="sxs-lookup"><span data-stu-id="c4a17-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a17-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4a17-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4a17-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="c4a17-105">Arguments</span></span>  
  
|<span data-ttu-id="c4a17-106">Термин</span><span class="sxs-lookup"><span data-stu-id="c4a17-106">Term</span></span>|<span data-ttu-id="c4a17-107">Определение</span><span class="sxs-lookup"><span data-stu-id="c4a17-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="c4a17-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="c4a17-108">Required.</span></span> <span data-ttu-id="c4a17-109">Имя файла ресурсов для внедрения в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="c4a17-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="c4a17-110">По умолчанию `filename` является открытым в сборке.</span><span class="sxs-lookup"><span data-stu-id="c4a17-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="c4a17-111">Заключите имя файла в кавычки (» «), если он содержит пробел.</span><span class="sxs-lookup"><span data-stu-id="c4a17-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="c4a17-112">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="c4a17-112">Optional.</span></span> <span data-ttu-id="c4a17-113">Логическое имя ресурса; имя, использованное для ее загрузки.</span><span class="sxs-lookup"><span data-stu-id="c4a17-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="c4a17-114">По умолчанию используется имя файла.</span><span class="sxs-lookup"><span data-stu-id="c4a17-114">The default is the name of the file.</span></span> <span data-ttu-id="c4a17-115">При необходимости можно указать, является ли ресурс открытым или закрытым в манифесте сборки, как и в случае со следующим: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="c4a17-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4a17-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="c4a17-116">Remarks</span></span>  
 <span data-ttu-id="c4a17-117">Используйте `-linkresource` чтобы связать ресурс со сборкой, не помещая файл ресурсов в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="c4a17-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="c4a17-118">Если `filename` является файлом ресурсов .NET Framework, созданным, например, по [Resgen.exe (генератор файлов ресурсов)](../../../framework/tools/resgen-exe-resource-file-generator.md) или в среде разработки, он может осуществляться с помощью членов пространства <xref:System.Resources> пространства имен (см. <xref:System.Resources.ResourceManager> Дополнительные сведения).</span><span class="sxs-lookup"><span data-stu-id="c4a17-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="c4a17-119">Чтобы получить доступ к всем остальным ресурсам во время выполнения, используйте один из следующих методов: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, или <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4a17-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="c4a17-120">Краткой формой `-resource` является `-res`.</span><span class="sxs-lookup"><span data-stu-id="c4a17-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="c4a17-121">Сведения о настройке `-resource` в СРЕДЕ Visual Studio, см. в разделе [управлении ресурсами приложения (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c4a17-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a17-122">Пример</span><span class="sxs-lookup"><span data-stu-id="c4a17-122">Example</span></span>  
 <span data-ttu-id="c4a17-123">Следующий код компилирует `In.vb` и присоединение файла ресурсов `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="c4a17-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4a17-124">См. также</span><span class="sxs-lookup"><span data-stu-id="c4a17-124">See also</span></span>

- [<span data-ttu-id="c4a17-125">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="c4a17-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c4a17-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="c4a17-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="c4a17-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a17-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="c4a17-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a17-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="c4a17-129">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="c4a17-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
