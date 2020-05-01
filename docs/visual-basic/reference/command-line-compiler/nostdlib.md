---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347909"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="e4c71-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4c71-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="e4c71-103">Указывает компилятору не ссылаться автоматически на стандартные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="e4c71-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c71-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4c71-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4c71-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="e4c71-105">Remarks</span></span>  
 <span data-ttu-id="e4c71-106">Параметр `-nostdlib` удаляет автоматическую ссылку на сборку System.dll и запрещает компилятору считывать файл Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="e4c71-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="e4c71-107">Файл Vbc.rsp, расположенный в том же каталоге, что и файл Vbc.exe, ссылается на часто используемые сборки .NET Framework и импортирует пространства имен `System` и `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="e4c71-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4c71-108">При этом компилятор всегда ссылается на сборки Mscorlib.dll и Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="e4c71-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4c71-109">Параметр `-nostdlib` недоступен в среде разработки Visual Studio. Он доступен только при компиляции из командной строки.</span><span class="sxs-lookup"><span data-stu-id="e4c71-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c71-110">Пример</span><span class="sxs-lookup"><span data-stu-id="e4c71-110">Example</span></span>  
 <span data-ttu-id="e4c71-111">Следующий код компилирует `T2.vb` без создания ссылок на стандартные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="e4c71-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="e4c71-112">Необходимо присвоить константе условной компиляции `_MYTYPE` строку Empty, чтобы удалить объект `My`.</span><span class="sxs-lookup"><span data-stu-id="e4c71-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4c71-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e4c71-113">See also</span></span>

- [<span data-ttu-id="e4c71-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e4c71-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="e4c71-115">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="e4c71-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e4c71-116">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="e4c71-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e4c71-117">Настройка доступа к объектам через My</span><span class="sxs-lookup"><span data-stu-id="e4c71-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
