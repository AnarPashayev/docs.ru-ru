---
title: Практическое руководство. использование блока try/catch для перехвата исключений
description: Включайте в блок try операторы, которые могут создавать исключение. Помещайте операторы для обработки исключений в один блок catch или несколько.
ms.date: 02/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: cfe5b2b304cdb9efe7f0d91059fe1c279b4fa2dd
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828014"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="0bbfd-104">Использование блока try/catch для перехвата исключений</span><span class="sxs-lookup"><span data-stu-id="0bbfd-104">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="0bbfd-105">Поместите все операторы кода, которые могут вызвать исключение, в блок `try`, а операторы, которые обрабатывают исключения, поместите в одном или нескольких блоках `catch` под блоком `try`.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-105">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="0bbfd-106">Каждый блок `catch` включает тип исключения и может содержать дополнительные инструкции, необходимые для обработки этого типа исключения.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-106">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="0bbfd-107">В следующем примере <xref:System.IO.StreamReader> открывает файл с именем *data.txt* и извлекает строку из файла.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-107">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="0bbfd-108">Так как код может вызывать любое из трех исключений, он помещается в блок `try`.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-108">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="0bbfd-109">Три блока `catch` перехватывают исключения и обрабатывают их, отображая результаты в консоли.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-109">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="0bbfd-110">Среда CLR перехватывает исключения, не обрабатываемые блоками `catch`.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-110">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="0bbfd-111">Если исключение перехватывается в среде CLR, в зависимости от конфигурации среды CLR может возникнуть один из следующих результатов:</span><span class="sxs-lookup"><span data-stu-id="0bbfd-111">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="0bbfd-112">Откроется диалоговое окно **отладки**.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-112">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="0bbfd-113">Программа прекратит выполнение, и откроется диалоговое окно со сведениями об исключении.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-113">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="0bbfd-114">В [стандартном потоке вывода ошибок](xref:System.Console.Error) будет выведена ошибка.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-114">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="0bbfd-115">Большая часть кода может создавать исключения, и некоторые исключения, например <xref:System.OutOfMemoryException>, могут вызываться самой средой CLR в любое время.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-115">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="0bbfd-116">Приложениям не требуется обрабатывать эти исключения, но вы должны помнить об этом при написании библиотек, предназначенных для других пользователей.</span><span class="sxs-lookup"><span data-stu-id="0bbfd-116">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="0bbfd-117">Рекомендации о том, когда следует помещать код в блок `try`, см. в разделе [о лучших методиках обработки исключений](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0bbfd-117">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bbfd-118">См. также</span><span class="sxs-lookup"><span data-stu-id="0bbfd-118">See also</span></span>

- [<span data-ttu-id="0bbfd-119">Исключения</span><span class="sxs-lookup"><span data-stu-id="0bbfd-119">Exceptions</span></span>](index.md)
- [<span data-ttu-id="0bbfd-120">Обработка ошибок ввода-вывода в .NET</span><span class="sxs-lookup"><span data-stu-id="0bbfd-120">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
