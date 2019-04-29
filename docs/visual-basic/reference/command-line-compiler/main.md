---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793917"
---
# <a name="-main"></a><span data-ttu-id="4cb46-102">-main</span><span class="sxs-lookup"><span data-stu-id="4cb46-102">-main</span></span>
<span data-ttu-id="4cb46-103">Задает класс или модуль, содержащий процедуру `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="4cb46-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb46-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4cb46-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cb46-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="4cb46-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="4cb46-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="4cb46-106">Required.</span></span> <span data-ttu-id="4cb46-107">Имя класса или модуля, содержащего `Sub Main` процедуры, который должен вызываться при запуске программы.</span><span class="sxs-lookup"><span data-stu-id="4cb46-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="4cb46-108">Это может быть в форме **-main: модуль** или **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="4cb46-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cb46-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="4cb46-109">Remarks</span></span>  
 <span data-ttu-id="4cb46-110">Используйте этот параметр при создании исполняемого файла или исполняемой программы Windows.</span><span class="sxs-lookup"><span data-stu-id="4cb46-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="4cb46-111">Если **-основной** параметр указан, компилятор выполняет поиск допустимый общий `Sub Main` во всех открытых классов и модулей.</span><span class="sxs-lookup"><span data-stu-id="4cb46-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="4cb46-112">См. в разделе [процедура Main в Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) обсуждение различных видов `Main` процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cb46-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="4cb46-113">Когда `location` — это класс, который наследует от <xref:System.Windows.Forms.Form>, компилятор предоставляет значение по умолчанию `Main` процедуру, которая запускает приложение, если класс не имеет `Main` процедуры.</span><span class="sxs-lookup"><span data-stu-id="4cb46-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="4cb46-114">Это позволяет скомпилировать код из командной строки, который был создан в среде разработки.</span><span class="sxs-lookup"><span data-stu-id="4cb46-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="4cb46-115">Чтобы задать - основной в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4cb46-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="4cb46-116">Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="4cb46-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4cb46-117">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="4cb46-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="4cb46-118">Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="4cb46-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="4cb46-119">Убедитесь, что **Включить исполняющую** не установлен флажок.</span><span class="sxs-lookup"><span data-stu-id="4cb46-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="4cb46-120">Измените значение в **автоматически запускаемый объект** поле.</span><span class="sxs-lookup"><span data-stu-id="4cb46-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cb46-121">Пример</span><span class="sxs-lookup"><span data-stu-id="4cb46-121">Example</span></span>  
 <span data-ttu-id="4cb46-122">Следующий код компилирует `T2.vb` и `T3.vb`, указав, `Sub Main` процедуры будут находиться в `Test2` класса.</span><span class="sxs-lookup"><span data-stu-id="4cb46-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cb46-123">См. также</span><span class="sxs-lookup"><span data-stu-id="4cb46-123">See also</span></span>

- [<span data-ttu-id="4cb46-124">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="4cb46-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4cb46-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cb46-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="4cb46-126">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="4cb46-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4cb46-127">Процедура Main в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4cb46-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
