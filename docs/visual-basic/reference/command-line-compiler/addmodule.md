---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2de5fe82f1969a2fdb305d45951d7d698252c0c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816438"
---
# <a name="-addmodule"></a><span data-ttu-id="82664-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="82664-102">-addmodule</span></span>
<span data-ttu-id="82664-103">Дает компилятору указание сделать всю информацию о типах из указанных файлов доступной компилируемому проекту.</span><span class="sxs-lookup"><span data-stu-id="82664-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82664-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82664-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="82664-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="82664-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="82664-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="82664-106">Required.</span></span> <span data-ttu-id="82664-107">Разделенный запятыми список файлов, которые содержат метаданные, но не содержат манифестов сборки.</span><span class="sxs-lookup"><span data-stu-id="82664-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="82664-108">Имена файлов, содержащие пробелы, которые должны быть заключены в кавычки (» «).</span><span class="sxs-lookup"><span data-stu-id="82664-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82664-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="82664-109">Remarks</span></span>  
 <span data-ttu-id="82664-110">Файлы, упорядоченные по `fileList` параметр должен быть создан с `-target:module` параметр, или с помощью другого компилятора эквивалентно `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="82664-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="82664-111">Все модули, добавленные с помощью `-addmodule` во время выполнения должны находиться в том же каталоге, что и выходной файл.</span><span class="sxs-lookup"><span data-stu-id="82664-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="82664-112">То есть можно указать модуль в любом каталоге во время компиляции, но во время выполнения он должен находиться в каталоге приложения.</span><span class="sxs-lookup"><span data-stu-id="82664-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="82664-113">Если это не так, вы получаете <xref:System.TypeLoadException> ошибки.</span><span class="sxs-lookup"><span data-stu-id="82664-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="82664-114">При указании (явно или неявно) любой[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) параметра, отличное от `-target:module` с `-addmodule`, файлов, передаваемый `-addmodule` становятся частью сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="82664-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="82664-115">Сборка необходима для проведения выходной файл, который имеет один или добавить дополнительные файлы с `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="82664-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="82664-116">Используйте [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) для импорта метаданных из файла, содержащего сборку.</span><span class="sxs-lookup"><span data-stu-id="82664-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82664-117">`-addmodule` Не доступна из среды разработки Visual Studio; она доступна только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="82664-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82664-118">Пример</span><span class="sxs-lookup"><span data-stu-id="82664-118">Example</span></span>  
 <span data-ttu-id="82664-119">В следующем коде создается модуль.</span><span class="sxs-lookup"><span data-stu-id="82664-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="82664-120">Следующий код импортирует типы модуля.</span><span class="sxs-lookup"><span data-stu-id="82664-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="82664-121">При запуске `t1`, он выводит `802`.</span><span class="sxs-lookup"><span data-stu-id="82664-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82664-122">См. также</span><span class="sxs-lookup"><span data-stu-id="82664-122">See also</span></span>

- [<span data-ttu-id="82664-123">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="82664-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="82664-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82664-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="82664-125">-ссылке (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82664-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="82664-126">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="82664-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
