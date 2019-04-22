---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: f2cdd228d8ce1912abbbe888c29c42f29299ebba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832740"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="8f4e2-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f4e2-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="8f4e2-103">Параметр **-refout** указывает путь к файлу, в который нужно выводить базовую сборку.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="8f4e2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f4e2-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="8f4e2-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="8f4e2-105">Arguments</span></span>

 <span data-ttu-id="8f4e2-106">`filepath` Путь и имя файла базовой сборки.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="8f4e2-107">Обычно следует во вложенной папке основной сборки.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="8f4e2-108">Согласно рекомендуемому соглашению (используемому в MSBuild), базовую сборку следует помещать во вложенную папку ref/ относительно основной сборки.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="8f4e2-109">Все папки в `filepath` должен существовать; компилятор не создает их.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="8f4e2-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="8f4e2-110">Remarks</span></span>

<span data-ttu-id="8f4e2-111">Visual Basic поддерживает `-refout` переключения, начиная с версии 15.3.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="8f4e2-112">Ссылка сборки являются только метаданные, которые содержат метаданные, но без реализации их кода.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="8f4e2-113">Они включают сведения о типе и члене для всем, кроме анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="8f4e2-114">Их тела заменяются одной `throw null` инструкции.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="8f4e2-115">Причина использования `throw null` тел методов (в отличие от отсутствии тела) является, поэтому PEVerify можно запустить и передать (проверки полноты метаданных).</span><span class="sxs-lookup"><span data-stu-id="8f4e2-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="8f4e2-116">Базовые сборки содержат уровня сборки [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) атрибута.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="8f4e2-117">Этот атрибут может быть задан в исходном коде (в этом случае компилятору не требуется его синтезировать).</span><span class="sxs-lookup"><span data-stu-id="8f4e2-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="8f4e2-118">Из-за этого атрибута среды выполнения не будет загружать базовые сборки для выполнения (но по-прежнему могут быть загружены в контекст только для отражения).</span><span class="sxs-lookup"><span data-stu-id="8f4e2-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="8f4e2-119">Средства, выполняющие отражение сборок необходимо убедиться, что они загружать базовые сборки как предназначенный только для отражения; в противном случае среда выполнения создает <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="8f4e2-120">Параметры `-refout` и [`-refonly`](refonly-compiler-option.md) являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="8f4e2-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f4e2-121">См. также</span><span class="sxs-lookup"><span data-stu-id="8f4e2-121">See also</span></span>

- [<span data-ttu-id="8f4e2-122">/refonly</span><span class="sxs-lookup"><span data-stu-id="8f4e2-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="8f4e2-123">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="8f4e2-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8f4e2-124">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="8f4e2-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
