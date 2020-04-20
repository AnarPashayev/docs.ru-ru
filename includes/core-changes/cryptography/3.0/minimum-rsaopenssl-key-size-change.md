---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275107"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="f2f5c-101">Увеличен минимальный размер создаваемых ключей RSAOpenSsl</span><span class="sxs-lookup"><span data-stu-id="f2f5c-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="f2f5c-102">Минимальный размер создаваемых ключей RSA в Linux увеличен с 384 до 512 бит.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f2f5c-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f2f5c-103">Change description</span></span>

<span data-ttu-id="f2f5c-104">Начиная с версии .NET Core 3.0, минимальный допустимый размер ключа, сообщаемый свойством `LegalKeySizes` для экземпляров RSA из <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> и <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> в Linux, увеличился с 384 до 512.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="f2f5c-105">В результате в .NET Core 2.2 и более ранних версий вызов такого метода, как `RSA.Create(384)`, выполняется успешно.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="f2f5c-106">В .NET Core 3.0 и более поздних версий при вызове метода `RSA.Create(384)` создается исключение, указывающее на то, что размер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="f2f5c-107">Изменение было внесено, так как для OpenSSL, где выполняются криптографические операции в Linux, между выпусками версий 1.0.2 и 1.1.0 увеличено минимальное значение.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="f2f5c-108">В .NET Core 3.0 предпочтительно использовать OpenSSL версий от 1.1.x до 1.0.x. Передаваемый номер версии был повышен в соответствии с повышением лимита для зависимостей.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f2f5c-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f2f5c-109">Version introduced</span></span>

<span data-ttu-id="f2f5c-110">3,0</span><span class="sxs-lookup"><span data-stu-id="f2f5c-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f2f5c-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f2f5c-111">Recommended action</span></span>

<span data-ttu-id="f2f5c-112">Если вы вызываете любой затронутый API-интерфейс, убедитесь, что размер созданных ключей не меньше минимального значения, установленного поставщиком.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="f2f5c-113">Стандарт 384-битового шифрования RSA уже считается небезопасным (как и стандарт 512-битового шифрования).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="f2f5c-114">В современных документах, таких как [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf) (Специальная публикация NIST 800-57, часть 1, редакция 4), рекомендуется создавать ключи с минимальным размером 2048 бит.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="f2f5c-115">Категория</span><span class="sxs-lookup"><span data-stu-id="f2f5c-115">Category</span></span>

<span data-ttu-id="f2f5c-116">Шифрование</span><span class="sxs-lookup"><span data-stu-id="f2f5c-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2f5c-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f2f5c-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
