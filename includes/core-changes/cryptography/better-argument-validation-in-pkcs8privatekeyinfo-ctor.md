---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263307"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="7d4b7-101">Улучшенная проверка аргументов в конструкторе Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="7d4b7-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="7d4b7-102">Начиная с .NET Core 3.0, предварительная версия 9, конструктор `Pkcs8PrivateKeyInfo` проверяет параметр `algorithmParameters` как одно значение в кодировке BER.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7d4b7-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="7d4b7-103">Change description</span></span>

<span data-ttu-id="7d4b7-104">До .NET Core 3.0, предварительная версия 9 [конструктор `Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) не проверял аргумент `algorithmParameters`.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="7d4b7-105">Когда этот аргумент представляет недопустимое значение, конструктор выполняет задачу, но вызов любого из методов <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> или <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> выдает исключение <xref:System.ArgumentException> для неподдерживаемого аргумента (`preEncodedValue`) или <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="7d4b7-106">При запуске с помощью .NET Core 3.0, версий, предшествующих предварительной версии 9, следующий код выдает исключение только при вызове метода <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>:</span><span class="sxs-lookup"><span data-stu-id="7d4b7-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="7d4b7-107">Начиная с .NET Core 3.0 (предварительная версия 9), аргумент проверяется в конструкторе, и появление недопустимого значения приводит к тому, что метод вызывает исключение <xref:System.Security.Cryptography.CryptographicException>.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="7d4b7-108">Это изменение позволяет связать исключение с источником ошибки данных.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="7d4b7-109">Например:</span><span class="sxs-lookup"><span data-stu-id="7d4b7-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="7d4b7-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7d4b7-110">Version introduced</span></span>

<span data-ttu-id="7d4b7-111">3.0, предварительная версия 9</span><span class="sxs-lookup"><span data-stu-id="7d4b7-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d4b7-112">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="7d4b7-112">Recommended action</span></span>

<span data-ttu-id="7d4b7-113">Убедитесь, что предоставлены только допустимые значения `algorithmParameters` и что при вызовах конструктора `Pkcs8PrivateKeyInfo` проверяются и <xref:System.Security.Cryptography.CryptographicException>, и <xref:System.ArgumentException>, если требуется обработка исключений.</span><span class="sxs-lookup"><span data-stu-id="7d4b7-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="7d4b7-114">Категория</span><span class="sxs-lookup"><span data-stu-id="7d4b7-114">Category</span></span>

<span data-ttu-id="7d4b7-115">Шифрование</span><span class="sxs-lookup"><span data-stu-id="7d4b7-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="7d4b7-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7d4b7-116">Affected APIs</span></span>

- <span data-ttu-id="7d4b7-117">[Конструктор Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="7d4b7-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
