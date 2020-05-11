---
title: -win32res (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 3bb1614fcf28c62a9000c9b96af2f046f329fb1e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794381"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="81c40-102">-win32res (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="81c40-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="81c40-103">Параметр **-win32res** вставляет ресурс Win32 в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="81c40-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c40-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81c40-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="81c40-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="81c40-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="81c40-106">Файл ресурсов, который требуется добавить в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="81c40-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81c40-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="81c40-107">Remarks</span></span>  
 <span data-ttu-id="81c40-108">Файл ресурсов Win32 можно создать с помощью [компилятора ресурсов](resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="81c40-108">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="81c40-109">Компилятор ресурсов вызывается при компиляции программы Visual C++; RES-файл создается из RC-файла.</span><span class="sxs-lookup"><span data-stu-id="81c40-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="81c40-110">Ресурс Win32 может содержать сведения о версии или точечный рисунок (значок) для упрощения идентификации приложения в проводнике.</span><span class="sxs-lookup"><span data-stu-id="81c40-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="81c40-111">Если параметр **-win32res** не задан, компилятор будет создавать сведения о версии на основе версии сборки.</span><span class="sxs-lookup"><span data-stu-id="81c40-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="81c40-112">Дополнительные сведения о ссылках на файлы ресурсов .NET Framework и их присоединении см. в разделах [-linkresource](./linkresource-compiler-option.md) и [-resource](./resource-compiler-option.md) соответственно.</span><span class="sxs-lookup"><span data-stu-id="81c40-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="81c40-113">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81c40-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="81c40-114">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="81c40-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="81c40-115">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="81c40-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="81c40-116">Чтобы выбрать файл в поле со списком, нажмите кнопку **Файл ресурсов**.</span><span class="sxs-lookup"><span data-stu-id="81c40-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c40-117">Пример</span><span class="sxs-lookup"><span data-stu-id="81c40-117">Example</span></span>  
 <span data-ttu-id="81c40-118">Скомпилируйте `in.cs` и присоедините файл ресурсов Win32 `rf.res`, чтобы создать `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="81c40-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="81c40-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="81c40-119">See also</span></span>

- [<span data-ttu-id="81c40-120">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="81c40-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="81c40-121">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="81c40-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
