---
description: -deterministic (параметры компилятора C#)
title: -deterministic (параметры компилятора C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: 9d0bcc2957e5a666c21cdc2ce61e74fc90fe3530
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125830"
---
# <a name="-deterministic"></a><span data-ttu-id="e17d7-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="e17d7-103">-deterministic</span></span>

<span data-ttu-id="e17d7-104">Указывает компилятору на необходимость создания сборки, чьи побайтовые выходные данные идентичны в разных компиляциях, если входные данные идентичны.</span><span class="sxs-lookup"><span data-stu-id="e17d7-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e17d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e17d7-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="e17d7-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="e17d7-106">Remarks</span></span>

<span data-ttu-id="e17d7-107">По умолчанию выходные данные компилятора из заданного набора входных данных являются уникальными, поскольку компилятор добавляет метку времени и идентификатор GUID, который создается из случайных чисел.</span><span class="sxs-lookup"><span data-stu-id="e17d7-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="e17d7-108">Вы можете использовать параметр `-deterministic` для создания *детерминированной сборки*, двоичное содержимое которой идентично в разных компиляциях при условии, что входные данные не изменяются.</span><span class="sxs-lookup"><span data-stu-id="e17d7-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="e17d7-109">Компилятор учитывает идентичность следующих входных данных:</span><span class="sxs-lookup"><span data-stu-id="e17d7-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="e17d7-110">Последовательность параметров командной строки.</span><span class="sxs-lookup"><span data-stu-id="e17d7-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="e17d7-111">Содержимое RSP-файла ответов в компиляторе.</span><span class="sxs-lookup"><span data-stu-id="e17d7-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="e17d7-112">Точная версия компилятора и его связанные сборки.</span><span class="sxs-lookup"><span data-stu-id="e17d7-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="e17d7-113">Текущий путь к каталогу.</span><span class="sxs-lookup"><span data-stu-id="e17d7-113">The current directory path.</span></span>
- <span data-ttu-id="e17d7-114">Двоичное содержимое всех файлов, явным образом переданных компилятору прямо или косвенно, в том числе:</span><span class="sxs-lookup"><span data-stu-id="e17d7-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="e17d7-115">Исходные файлы</span><span class="sxs-lookup"><span data-stu-id="e17d7-115">Source files</span></span>
  - <span data-ttu-id="e17d7-116">Связанные сборки</span><span class="sxs-lookup"><span data-stu-id="e17d7-116">Referenced assemblies</span></span>
  - <span data-ttu-id="e17d7-117">Связанные модули</span><span class="sxs-lookup"><span data-stu-id="e17d7-117">Referenced modules</span></span>
  - <span data-ttu-id="e17d7-118">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="e17d7-118">Resources</span></span>
  - <span data-ttu-id="e17d7-119">Файл ключа строгого имени</span><span class="sxs-lookup"><span data-stu-id="e17d7-119">The strong name key file</span></span>
  - <span data-ttu-id="e17d7-120">Файлы ответов @</span><span class="sxs-lookup"><span data-stu-id="e17d7-120">@ response files</span></span>
  - <span data-ttu-id="e17d7-121">Анализаторы</span><span class="sxs-lookup"><span data-stu-id="e17d7-121">Analyzers</span></span>
  - <span data-ttu-id="e17d7-122">Наборы правил</span><span class="sxs-lookup"><span data-stu-id="e17d7-122">Rulesets</span></span>
  - <span data-ttu-id="e17d7-123">Дополнительные файлы, которые могут использоваться анализаторами</span><span class="sxs-lookup"><span data-stu-id="e17d7-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="e17d7-124">Текущий язык и региональные параметры (для языка сообщений о диагностике и исключениях).</span><span class="sxs-lookup"><span data-stu-id="e17d7-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="e17d7-125">Кодировка по умолчанию (или текущая кодовая страница), если кодировка не указана.</span><span class="sxs-lookup"><span data-stu-id="e17d7-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="e17d7-126">Наличие, отсутствие и содержимое файлов на пути поиска компилятора (задается, например, с помощью `-lib` или `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="e17d7-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="e17d7-127">Платформа среды CLR, в которой выполняется компилятор.</span><span class="sxs-lookup"><span data-stu-id="e17d7-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="e17d7-128">Значение `%LIBPATH%`, которое может повлиять на загрузку зависимостей анализатора.</span><span class="sxs-lookup"><span data-stu-id="e17d7-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="e17d7-129">Если источники общедоступны, детерминированную компиляцию можно использовать, чтобы установить, компилируются ли двоичные данные из надежного источника.</span><span class="sxs-lookup"><span data-stu-id="e17d7-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="e17d7-130">Ее также можно использовать в системе непрерывной сборки, чтобы определить необходимость выполнения шагов сборки, зависящих от изменений в двоичном файле.</span><span class="sxs-lookup"><span data-stu-id="e17d7-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e17d7-131">См. также</span><span class="sxs-lookup"><span data-stu-id="e17d7-131">See also</span></span>

- [<span data-ttu-id="e17d7-132">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="e17d7-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e17d7-133">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="e17d7-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
