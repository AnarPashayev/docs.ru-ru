---
title: -lib (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606818"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="baaf1-102">-lib (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="baaf1-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="baaf1-103">Параметр **-lib** указывает расположение сборок, на которые ссылается параметр [-reference (параметры компилятора C#)](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="baaf1-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baaf1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="baaf1-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="baaf1-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="baaf1-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="baaf1-106">Каталог, в котором компилятор должен искать сборку, если она отсутствует в текущем рабочем каталоге (каталоге, из которого был вызван компилятор) и системном каталоге среды CLR.</span><span class="sxs-lookup"><span data-stu-id="baaf1-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="baaf1-107">Один или несколько дополнительных каталогов для поиска связанных сборок.</span><span class="sxs-lookup"><span data-stu-id="baaf1-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="baaf1-108">Имена дополнительных каталогов разделяются запятыми без пробелов.</span><span class="sxs-lookup"><span data-stu-id="baaf1-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baaf1-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="baaf1-109">Remarks</span></span>  
 <span data-ttu-id="baaf1-110">Компилятор выполняет поиск связанных сборок, для которых не указано полное имя, в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="baaf1-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="baaf1-111">Текущая рабочая папка.</span><span class="sxs-lookup"><span data-stu-id="baaf1-111">Current working directory.</span></span> <span data-ttu-id="baaf1-112">Это папка, из которой был вызван компилятор.</span><span class="sxs-lookup"><span data-stu-id="baaf1-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="baaf1-113">Системный каталог среды CLR.</span><span class="sxs-lookup"><span data-stu-id="baaf1-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="baaf1-114">Каталоги, заданные параметром **-lib**.</span><span class="sxs-lookup"><span data-stu-id="baaf1-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="baaf1-115">Каталоги, указанные переменной среды LIB.</span><span class="sxs-lookup"><span data-stu-id="baaf1-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="baaf1-116">Для указания ссылки на сборку используется параметр **-reference**.</span><span class="sxs-lookup"><span data-stu-id="baaf1-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="baaf1-117">Параметры **-lib** можно добавлять; каждое следующее указание этого параметра присоединяется к предыдущим значениям.</span><span class="sxs-lookup"><span data-stu-id="baaf1-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="baaf1-118">Вместо использования параметра **-lib** можно скопировать в рабочий каталог все необходимые сборки; это позволит просто передать имя сборки с помощью параметра **-reference**.</span><span class="sxs-lookup"><span data-stu-id="baaf1-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="baaf1-119">Затем сборки можно будет удалить из рабочего каталога.</span><span class="sxs-lookup"><span data-stu-id="baaf1-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="baaf1-120">Поскольку путь к зависимой сборке не указывается в манифесте сборки, приложение может быть запущено на целевом компьютере, после чего оно найдет используемую сборку в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="baaf1-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="baaf1-121">Несмотря на то, что компилятору удалось обнаружить сборку по ссылке, среда CLR может не найти и не загрузить данную сборку во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="baaf1-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="baaf1-122">Сведения о том, как среда выполнения выполняет поиск связанных сборок, см. в разделе [Обнаружение сборок в среде выполнения](../../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="baaf1-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="baaf1-123">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="baaf1-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="baaf1-124">Откройте диалоговое окно **Страницы свойств** проекта.</span><span class="sxs-lookup"><span data-stu-id="baaf1-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="baaf1-125">Откройте страницу свойств **Путь ссылок**.</span><span class="sxs-lookup"><span data-stu-id="baaf1-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="baaf1-126">Измените содержимое поля со списком.</span><span class="sxs-lookup"><span data-stu-id="baaf1-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="baaf1-127">Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="baaf1-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baaf1-128">Пример</span><span class="sxs-lookup"><span data-stu-id="baaf1-128">Example</span></span>  
 <span data-ttu-id="baaf1-129">Выполните компиляцию файла t2.cs для создания EXE-файла.</span><span class="sxs-lookup"><span data-stu-id="baaf1-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="baaf1-130">Компилятор выполнит поиск ссылок на сборку в рабочем каталоге и корневом каталоге диска С.</span><span class="sxs-lookup"><span data-stu-id="baaf1-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="baaf1-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="baaf1-131">See also</span></span>

- [<span data-ttu-id="baaf1-132">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="baaf1-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="baaf1-133">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="baaf1-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
