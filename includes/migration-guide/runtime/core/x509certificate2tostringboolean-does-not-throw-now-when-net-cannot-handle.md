---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858519"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="82ec2-101">Теперь метод X509Certificate2.ToString(Boolean) не создает исключение, когда .NET не удается обработать сертификат</span><span class="sxs-lookup"><span data-stu-id="82ec2-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="82ec2-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="82ec2-102">Details</span></span>|<span data-ttu-id="82ec2-103">В .NET Framework 4.5.2 и более ранних версиях этот метод создавал исключение, если значение <code>true</code> передавалось в параметр verbose и были установлены сертификаты, не поддерживаемые .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82ec2-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="82ec2-104">Теперь метод будет выполняться успешно и возвращать допустимую строку, в которой пропущены недоступные части сертификата.</span><span class="sxs-lookup"><span data-stu-id="82ec2-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="82ec2-105">Предложение</span><span class="sxs-lookup"><span data-stu-id="82ec2-105">Suggestion</span></span>|<span data-ttu-id="82ec2-106">Любой код, зависящий от <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>, следует обновить для ожидания того, что в некоторых случаях, когда ранее API возвращал исключение, в возвращаемой строке могут отсутствовать некоторые данные сертификата (например, открытый ключ, закрытый ключ и расширения).</span><span class="sxs-lookup"><span data-stu-id="82ec2-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="82ec2-107">Область</span><span class="sxs-lookup"><span data-stu-id="82ec2-107">Scope</span></span>|<span data-ttu-id="82ec2-108">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="82ec2-108">Edge</span></span>|
|<span data-ttu-id="82ec2-109">Версия</span><span class="sxs-lookup"><span data-stu-id="82ec2-109">Version</span></span>|<span data-ttu-id="82ec2-110">4.6</span><span class="sxs-lookup"><span data-stu-id="82ec2-110">4.6</span></span>|
|<span data-ttu-id="82ec2-111">Тип</span><span class="sxs-lookup"><span data-stu-id="82ec2-111">Type</span></span>|<span data-ttu-id="82ec2-112">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="82ec2-112">Runtime</span></span>|
|<span data-ttu-id="82ec2-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="82ec2-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

