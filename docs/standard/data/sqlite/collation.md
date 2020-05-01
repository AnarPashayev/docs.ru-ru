---
title: Параметры сортировки
ms.date: 12/13/2019
description: Узнайте, как создать пользовательскую последовательность сортировки.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242976"
---
# <a name="collation"></a><span data-ttu-id="19721-103">Параметры сортировки</span><span class="sxs-lookup"><span data-stu-id="19721-103">Collation</span></span>

<span data-ttu-id="19721-104">При сравнении текстовых значений для определения порядка и равенства в SQLite используются последовательности сортировки.</span><span class="sxs-lookup"><span data-stu-id="19721-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="19721-105">Вы можете указать используемые параметры сортировки при создании столбцов или для отдельных операций в SQL-запросах.</span><span class="sxs-lookup"><span data-stu-id="19721-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="19721-106">По умолчанию в SQLite предоставляется три последовательности сортировки.</span><span class="sxs-lookup"><span data-stu-id="19721-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="19721-107">Параметры сортировки</span><span class="sxs-lookup"><span data-stu-id="19721-107">Collation</span></span> | <span data-ttu-id="19721-108">Описание</span><span class="sxs-lookup"><span data-stu-id="19721-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="19721-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="19721-109">RTRIM</span></span>     | <span data-ttu-id="19721-110">Игнорирует конечные пробелы</span><span class="sxs-lookup"><span data-stu-id="19721-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="19721-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="19721-111">NOCASE</span></span>    | <span data-ttu-id="19721-112">Без учета регистра для символов A–Z в кодировке ASCII</span><span class="sxs-lookup"><span data-stu-id="19721-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="19721-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="19721-113">BINARY</span></span>    | <span data-ttu-id="19721-114">С учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="19721-114">Case-sensitive.</span></span> <span data-ttu-id="19721-115">Сравнивает байты напрямую</span><span class="sxs-lookup"><span data-stu-id="19721-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="19721-116">Настраиваемые параметры сортировки</span><span class="sxs-lookup"><span data-stu-id="19721-116">Custom collation</span></span>

<span data-ttu-id="19721-117">Вы можете определить собственные последовательности сортировки или переопределить встроенные, используя <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span><span class="sxs-lookup"><span data-stu-id="19721-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="19721-118">В следующем примере демонстрируется переопределение параметров сортировки NOCASE для поддержки символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="19721-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="19721-119">[Полный пример кода](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) можно найти на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="19721-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="19721-120">Оператор LIKE</span><span class="sxs-lookup"><span data-stu-id="19721-120">Like operator</span></span>

<span data-ttu-id="19721-121">Оператор LIKE в SQLite не учитывает параметры сортировки.</span><span class="sxs-lookup"><span data-stu-id="19721-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="19721-122">Реализация по умолчанию использует семантику, аналогичную параметрам сортировки NOCASE.</span><span class="sxs-lookup"><span data-stu-id="19721-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="19721-123">Регистр не учитывается для символов A–Z в кодировке ASCII.</span><span class="sxs-lookup"><span data-stu-id="19721-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="19721-124">Вы можете легко настроить учет регистра для оператора LIKE с помощью следующей инструкции pragma:</span><span class="sxs-lookup"><span data-stu-id="19721-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="19721-125">Дополнительные сведения о переопределении реализации оператора LIKE см. в описании [определяемых пользователем функций](user-defined-functions.md).</span><span class="sxs-lookup"><span data-stu-id="19721-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="19721-126">См. также</span><span class="sxs-lookup"><span data-stu-id="19721-126">See also</span></span>

* [<span data-ttu-id="19721-127">Определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="19721-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="19721-128">Синтаксис SQL</span><span class="sxs-lookup"><span data-stu-id="19721-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
