---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804961"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng теперь правильно загружает ключи RSA нестандартного размера

|   |   |
|---|---|
|Подробные сведения|В версиях .NET Framework до 4.6.2 клиенты с нестандартным размером ключа для сертификатов RSA не могли получить доступ к этим ключам через методы расширения <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> и <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>.  Возникало исключение <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> с сообщением &quot;Запрошенный размер ключа не поддерживается&quot;. В .NET Framework 4.6.2 эта проблема была устранена. Аналогичным образом <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> и <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> теперь работают с нестандартными размерами ключа, не выдавая исключение <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Предложение|Если существует логика обработки исключений, которая полагается на предыдущее поведение, когда при использовании ключей нестандартного размера возникало исключение <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>, возможно, следует удалить эту логику.|
|Область|Пограничный случай|
|Версия|4.6.2|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
