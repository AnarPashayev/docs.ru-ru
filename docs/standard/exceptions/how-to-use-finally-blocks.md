---
title: Практическое руководство. Использование блоков Finally
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 8bc36ce9a755762bb5159a27f9ef5699b2992f0e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828040"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="49b8e-102">Использование блоков finally</span><span class="sxs-lookup"><span data-stu-id="49b8e-102">How to use finally blocks</span></span>

<span data-ttu-id="49b8e-103">При возникновении исключения выполнение останавливается, и управление передается соответствующему обработчику исключений.</span><span class="sxs-lookup"><span data-stu-id="49b8e-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="49b8e-104">Часто это означает, что ожидаемые вами строки кода пропускаются.</span><span class="sxs-lookup"><span data-stu-id="49b8e-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="49b8e-105">Даже при возникновении исключения требуется определенная очистка ресурсов, например закрытие файла.</span><span class="sxs-lookup"><span data-stu-id="49b8e-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="49b8e-106">Для этого можно использовать блок `finally`.</span><span class="sxs-lookup"><span data-stu-id="49b8e-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="49b8e-107">Блок `finally` выполняются всегда, независимо от того, возникает ли исключение.</span><span class="sxs-lookup"><span data-stu-id="49b8e-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="49b8e-108">В следующем примере кода блок `try`/`catch` используется, чтобы перехватить <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="49b8e-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="49b8e-109">Метод `Main` создает два массива и пытается скопировать один из них в другой.</span><span class="sxs-lookup"><span data-stu-id="49b8e-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="49b8e-110">Это действие создает исключение <xref:System.ArgumentOutOfRangeException>, и ошибка выводится на консоль.</span><span class="sxs-lookup"><span data-stu-id="49b8e-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="49b8e-111">Блок `finally` выполняется вне зависимости от результата операции копирования.</span><span class="sxs-lookup"><span data-stu-id="49b8e-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="49b8e-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="49b8e-112">See also</span></span>

- [<span data-ttu-id="49b8e-113">Исключения</span><span class="sxs-lookup"><span data-stu-id="49b8e-113">Exceptions</span></span>](index.md)
