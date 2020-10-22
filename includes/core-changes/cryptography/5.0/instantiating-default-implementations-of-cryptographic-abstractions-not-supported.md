---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159562"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="0c5f0-101">Создание экземпляров реализаций по умолчанию для криптографических абстракций не поддерживается</span><span class="sxs-lookup"><span data-stu-id="0c5f0-101">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="0c5f0-102">Начиная с версии .NET 5.0 перегрузки `Create()` без параметров для криптографических абстракций не рекомендуются к применению и приводят к возникновению предупреждения.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-102">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0c5f0-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0c5f0-103">Change description</span></span>

<span data-ttu-id="0c5f0-104">В .NET Framework версий с 2.0 по 4.8 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, могут быть настроены для возврата различных алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-104">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="0c5f0-105">Например, при установке .NET Framework 4.8 по умолчанию статический метод без параметров <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> возвращает экземпляр алгоритма SHA1, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-105">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="0c5f0-106">**Только .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="0c5f0-106">**.NET Framework only**</span></span>

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

<span data-ttu-id="0c5f0-107">Также можно использовать [конфигурации на уровне компьютера](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) для изменения алгоритма по умолчанию без необходимости программного вызова `CryptoConfig`.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-107">You can also use [machine-wide configuration](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="0c5f0-108">В .NET Core версий с 2.0 по 3.1 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, всегда создают исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-108">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="0c5f0-109">В .NET 5.0 и более поздних версий фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, не рекомендуются для использования и во время компиляции с создают предупреждение идентификатором `SYSLIB0007`.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-109">In .NET 5.0 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="0c5f0-110">Во время выполнения эти методы продолжают создавать исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-110">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="0c5f0-111">Это изменение происходит только во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-111">This is a compile-time only change.</span></span> <span data-ttu-id="0c5f0-112">Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-112">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="0c5f0-113">Для применения не рекомендуются только перегрузки методов `Create()` без параметров.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-113">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="0c5f0-114">Параметризованные перегрузки по-прежнему актуальны и функционируют в соответствии с ожиданиями.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-114">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="0c5f0-115">Перегрузки без параметров для *определенных* семейств алгоритмов (не абстракции) также сохраняют актуальность и будут продолжать работать ожидаемым образом.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-115">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a><span data-ttu-id="0c5f0-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="0c5f0-116">Reason for change</span></span>

<span data-ttu-id="0c5f0-117">Система конфигурации шифрования, представленная в .NET Framework, больше не используется в .NET Core и .NET 5.0 и более поздних версий, поскольку она является устаревшей и не позволяет обеспечить необходимую гибкость шифрования.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-117">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="0c5f0-118">Требования к обратной совместимости .NET также не позволяют платформе обновлять определенные API шифрования, чтобы обеспечить поддержку улучшений технологий шифрования.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-118">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="0c5f0-119">Например, метод <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> был представлен в .NET Framework 1.0, когда алгоритм хэширования SHA-1 соответствовал уровню развития технологий на тот момент.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-119">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="0c5f0-120">Прошло двадцать лет, и теперь SHA-1 считается ненадежным, но мы не можем изменить <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> для возврата другого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-120">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="0c5f0-121">Это может привести к неприемлемым критическим изменениям в использовании приложений.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-121">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="0c5f0-122">Рекомендации предписывают, что библиотеки, использующие примитивы шифрования (такие как AES, SHA-\* и RSA), должны полностью контролировать использование этих примитивов.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-122">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="0c5f0-123">Приложения, для которых требуется обеспечить гарантированную актуальность в будущем, должны использовать библиотеки более высокого уровня, которые заключают эти примитивы в оболочку, а затем добавляют возможности управления ключами и гибкого шифрования.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-123">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="0c5f0-124">Такие библиотеки часто предоставляются средой размещения.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-124">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="0c5f0-125">В качестве примера можно привести [библиотеку защиты данных ASP.NET](/aspnet/core/security/data-protection/), которая обеспечивает решение этих задач от имени вызывающего приложения.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-125">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c5f0-126">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0c5f0-126">Version introduced</span></span>

<span data-ttu-id="0c5f0-127">5.0 (RC1)</span><span class="sxs-lookup"><span data-stu-id="0c5f0-127">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c5f0-128">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0c5f0-128">Recommended action</span></span>

- <span data-ttu-id="0c5f0-129">Рекомендуется заменить вызовы к устаревшим API вызовами методов фабрики для конкретных алгоритмов, например <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-129">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0c5f0-130">Таким образом, вы будете полностью контролировать алгоритмы, для которых создаются экземпляры.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-130">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="0c5f0-131">Если необходимо обеспечить совместимость с существующими полезными данными, создаваемыми приложениями .NET Framework, которые используют устаревшие API, используйте предложенные в следующей таблице альтернативные варианты.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-131">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="0c5f0-132">В этой таблице приводится сопоставление алгоритмов .NET Framework по умолчанию с их эквивалентами в .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-132">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="0c5f0-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c5f0-133">.NET Framework</span></span> | <span data-ttu-id="0c5f0-134">Совместимый эквивалент в .NET Core или .NET 5.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="0c5f0-134">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="0c5f0-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c5f0-135">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="0c5f0-136">Алгоритм SHA-1 считается ненадежным.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-136">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="0c5f0-137">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-137">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="0c5f0-138">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-138">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="0c5f0-139">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-139">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="0c5f0-140">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-140">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="0c5f0-141">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-141">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="0c5f0-142">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-142">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="0c5f0-143">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-143">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="0c5f0-144">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-144">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="0c5f0-145">Если вам по-прежнему требуется вызывать устаревшие перегрузки `Create()` без параметров, вы можете отключить предупреждение `SYSLIB0007` в коде.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-145">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="0c5f0-146">Это предупреждение также можно отключить в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-146">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="0c5f0-147">В таком случае предупреждение также будет отключено для всех исходных файлов в проекте.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-147">Doing so disables the warning for all source files within the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="0c5f0-148">Если отключить `SYSLIB0007`, для указанных здесь API шифрования будут отключены только предупреждения об устаревании.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-148">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="0c5f0-149">Другие предупреждения не отключаются.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-149">It does not disable any other warnings.</span></span> <span data-ttu-id="0c5f0-150">Кроме того, даже если отключить предупреждение, эти устаревшие API все равно будут создавать исключение <xref:System.PlatformNotSupportedException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0c5f0-150">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

#### <a name="category"></a><span data-ttu-id="0c5f0-151">Категория</span><span class="sxs-lookup"><span data-stu-id="0c5f0-151">Category</span></span>

- <span data-ttu-id="0c5f0-152">Шифрование</span><span class="sxs-lookup"><span data-stu-id="0c5f0-152">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c5f0-153">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0c5f0-153">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

-->
