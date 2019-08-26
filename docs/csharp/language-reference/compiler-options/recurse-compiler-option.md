---
title: -recurse (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606744"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="9940b-102">-recurse (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="9940b-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="9940b-103">Параметр -recurse позволяет компилировать файлы исходного кода во всех вложенных каталогах заданного каталога (dir) или каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="9940b-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9940b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9940b-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9940b-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="9940b-105">Arguments</span></span>  
 <span data-ttu-id="9940b-106">`dir` (необязательно)</span><span class="sxs-lookup"><span data-stu-id="9940b-106">`dir` (optional)</span></span>  
 <span data-ttu-id="9940b-107">Каталог, с которого будет начинаться поиск.</span><span class="sxs-lookup"><span data-stu-id="9940b-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="9940b-108">Если этот параметр не задан, поиск начинается с каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="9940b-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="9940b-109">Файлы для поиска.</span><span class="sxs-lookup"><span data-stu-id="9940b-109">The file(s) to search for.</span></span> <span data-ttu-id="9940b-110">Поддерживаются подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="9940b-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9940b-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="9940b-111">Remarks</span></span>  
 <span data-ttu-id="9940b-112">Параметр **-recurse** позволяет компилировать файлы исходного кода во всех вложенных каталогах заданного каталога (`dir`) или каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="9940b-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="9940b-113">Чтобы скомпилировать все соответствующие файлы в каталоге проекта, не задавая параметр **-recurse**, можно использовать подстановочные знаки в именах файлов.</span><span class="sxs-lookup"><span data-stu-id="9940b-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="9940b-114">Этот параметр компилятора недоступен в Visual Studio и не может быть изменен программным способом.</span><span class="sxs-lookup"><span data-stu-id="9940b-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9940b-115">Пример</span><span class="sxs-lookup"><span data-stu-id="9940b-115">Example</span></span>  
 <span data-ttu-id="9940b-116">Компиляция всех файлов C# в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="9940b-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="9940b-117">Компиляция всех файлов C# в каталоге dir1\dir2 и всех вложенных в него каталогах, а также создание файла dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="9940b-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9940b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="9940b-118">See also</span></span>

- [<span data-ttu-id="9940b-119">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="9940b-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9940b-120">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="9940b-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
