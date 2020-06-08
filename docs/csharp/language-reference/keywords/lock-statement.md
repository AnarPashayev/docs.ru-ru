---
title: Инструкция lock. Справочник по C#
description: Синхронизация доступа потоков к общему ресурсу с помощью оператора блокировки C#
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406694"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="dcbbb-103">Инструкция lock. (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="dcbbb-103">lock statement (C# reference)</span></span>

<span data-ttu-id="dcbbb-104">Оператор `lock` получает взаимоисключающую блокировку заданного объекта перед выполнением определенных операторов, а затем снимает блокировку.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="dcbbb-105">Во время блокировки поток, удерживающий блокировку, может снова поставить и снять блокировку.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="dcbbb-106">Любой другой поток не может получить блокировку и ожидает ее снятия.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="dcbbb-107">Оператор `lock` имеет форму</span><span class="sxs-lookup"><span data-stu-id="dcbbb-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="dcbbb-108">Здесь `x` — это выражение [ссылочного типа](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="dcbbb-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="dcbbb-109">Оно является точным эквивалентом</span><span class="sxs-lookup"><span data-stu-id="dcbbb-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="dcbbb-110">Так как в коде используется блок [try... finally](try-finally.md), блокировка освобождается, даже если возникает исключение в теле оператора `lock`.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="dcbbb-111">Нельзя использовать [оператор await](../operators/await.md) в теле оператора `lock`.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="dcbbb-112">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="dcbbb-112">Guidelines</span></span>

<span data-ttu-id="dcbbb-113">При синхронизации доступа потоков к общему ресурсу блокируйте выделенный экземпляр объекта (например, `private readonly object balanceLock = new object();`) или другой экземпляр, который, скорее всего, не будет использоваться как объект блокировки другими частями кода.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="dcbbb-114">Не используйте один и тот же экземпляр объекта блокировки для разных общих ресурсов: это может привести к взаимоблокировке или состязанию при блокировке.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="dcbbb-115">В особенности избегайте использования следующих объектов в качестве объектов блокировки:</span><span class="sxs-lookup"><span data-stu-id="dcbbb-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="dcbbb-116">`this`, так как он может использоваться вызывающими объектами как блокировка;</span><span class="sxs-lookup"><span data-stu-id="dcbbb-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="dcbbb-117">экземпляров <xref:System.Type>, так как их может получать оператор [typeof](../operators/type-testing-and-cast.md#typeof-operator) или отражение;</span><span class="sxs-lookup"><span data-stu-id="dcbbb-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="dcbbb-118">строковых экземпляров, включая строковые литералы, так как они могут быть [интернированы](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="dcbbb-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="dcbbb-119">Удерживайте блокировку в течение максимально короткого времени, чтобы сократить число конфликтов при блокировке.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="dcbbb-120">Пример</span><span class="sxs-lookup"><span data-stu-id="dcbbb-120">Example</span></span>

<span data-ttu-id="dcbbb-121">В следующем примере определяется класс `Account`, который синхронизирует доступ к закрытому полю `balance` путем блокировки выделенного экземпляра `balanceLock`.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="dcbbb-122">Использование того же экземпляра для блокировки гарантирует, что поле `balance` не смогут одновременно обновить два потока, пытающиеся вызвать методы `Debit` или `Credit` одновременно.</span><span class="sxs-lookup"><span data-stu-id="dcbbb-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="dcbbb-123">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="dcbbb-123">C# language specification</span></span>

<span data-ttu-id="dcbbb-124">Дополнительные сведения см. в разделе об [инструкции lock](~/_csharplang/spec/statements.md#the-lock-statement) в документации [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dcbbb-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dcbbb-125">См. также</span><span class="sxs-lookup"><span data-stu-id="dcbbb-125">See also</span></span>

- [<span data-ttu-id="dcbbb-126">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="dcbbb-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dcbbb-127">Ключевые слова C#</span><span class="sxs-lookup"><span data-stu-id="dcbbb-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="dcbbb-128">Обзор примитивов синхронизации</span><span class="sxs-lookup"><span data-stu-id="dcbbb-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
