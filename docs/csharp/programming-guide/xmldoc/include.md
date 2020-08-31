---
title: <include> Руководство по программированию на C#.
description: Сведения о теге <include> XML. Этот тег позволяет указать ссылку на комментарии в другом файле, которые описывают типы и элементы вашего исходного кода.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: d2de8fea17850685668766bc4ec6e64b1be77cce
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053195"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="e47d6-105">\<include> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="e47d6-105">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e47d6-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e47d6-106">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="e47d6-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e47d6-107">Parameters</span></span>

- `filename`

  <span data-ttu-id="e47d6-108">Имя XML-файла, содержащего документацию.</span><span class="sxs-lookup"><span data-stu-id="e47d6-108">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="e47d6-109">Имя файла может быть квалифицировано с помощью относительного пути к файлу исходного кода.</span><span class="sxs-lookup"><span data-stu-id="e47d6-109">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="e47d6-110">`filename` необходимо заключать в одинарные кавычки (' ').</span><span class="sxs-lookup"><span data-stu-id="e47d6-110">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="e47d6-111">Путь тегов в `filename`, который ведет к тегу `name`.</span><span class="sxs-lookup"><span data-stu-id="e47d6-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="e47d6-112">Путь необходимо заключать в одинарные кавычки (' ').</span><span class="sxs-lookup"><span data-stu-id="e47d6-112">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="e47d6-113">Спецификатор имени в теге, предшествующий комментариям. `name` будет иметь идентификатор `id`.</span><span class="sxs-lookup"><span data-stu-id="e47d6-113">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

  <span data-ttu-id="e47d6-114">Идентификатор тега, который предшествует комментариям.</span><span class="sxs-lookup"><span data-stu-id="e47d6-114">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="e47d6-115">Идентификатор заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="e47d6-115">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="e47d6-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="e47d6-116">Remarks</span></span>

<span data-ttu-id="e47d6-117">Тег `<include>` позволяет задать ссылку на комментарии в другом файле, которые описывают типы и элементы вашего исходного кода.</span><span class="sxs-lookup"><span data-stu-id="e47d6-117">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="e47d6-118">Этот способ является альтернативой размещению комментариев документации непосредственно в файле исходного кода.</span><span class="sxs-lookup"><span data-stu-id="e47d6-118">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="e47d6-119">Помещая комментарии документации в отдельный файл, вы можете реализовать управление их версиями отдельно от версий исходного кода.</span><span class="sxs-lookup"><span data-stu-id="e47d6-119">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="e47d6-120">В этом случае файл исходного кода может быть извлечен для изменения одним пользователем, а файл документации — другим.</span><span class="sxs-lookup"><span data-stu-id="e47d6-120">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="e47d6-121">Тег `<include>` использует XML-синтаксис XPath.</span><span class="sxs-lookup"><span data-stu-id="e47d6-121">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="e47d6-122">Сведения об использовании тега `<include>` см. в документации по XPath.</span><span class="sxs-lookup"><span data-stu-id="e47d6-122">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="e47d6-123">Пример</span><span class="sxs-lookup"><span data-stu-id="e47d6-123">Example</span></span>

<span data-ttu-id="e47d6-124">В этом примере представлено несколько файлов.</span><span class="sxs-lookup"><span data-stu-id="e47d6-124">This is a multifile example.</span></span> <span data-ttu-id="e47d6-125">Ниже показан первый файл, в котором используется тег `<include>`.</span><span class="sxs-lookup"><span data-stu-id="e47d6-125">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="e47d6-126">Второй файл, *xml_include_tag.doc*, содержит следующие комментарии документации:</span><span class="sxs-lookup"><span data-stu-id="e47d6-126">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a><span data-ttu-id="e47d6-127">Выходные данные программы</span><span class="sxs-lookup"><span data-stu-id="e47d6-127">Program output</span></span>

<span data-ttu-id="e47d6-128">При компиляции классов Test и Test2 с использованием следующей команды в командной строке создаются следующие выходные данные: `-doc:DocFileName.xml.` В Visual Studio параметр "Комментарии XML-документа" задается в области построения конструктора проектов.</span><span class="sxs-lookup"><span data-stu-id="e47d6-128">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="e47d6-129">При обнаружении тега `<include>` компилятор C# выполняет поиск комментариев документации в файле *xml_include_tag.doc* вместо текущего файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="e47d6-129">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="e47d6-130">После этого компилятор создает файл *DocFileName.xml*, который будет использоваться средствами для работы с документацией, такими как [Sandcastle](https://github.com/EWSoftware/SHFB), для подготовки окончательной версии документации.</span><span class="sxs-lookup"><span data-stu-id="e47d6-130">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a><span data-ttu-id="e47d6-131">См. также</span><span class="sxs-lookup"><span data-stu-id="e47d6-131">See also</span></span>

- [<span data-ttu-id="e47d6-132">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="e47d6-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e47d6-133">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="e47d6-133">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
