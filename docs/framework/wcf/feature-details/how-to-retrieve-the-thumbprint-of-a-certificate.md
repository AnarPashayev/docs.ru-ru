---
title: Практическое руководство. Получение отпечатка сертификата
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 51debbbcfec2fd5b82460e1dd1d6ece8e77bfc13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000783"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Практическое руководство. Получение отпечатка сертификата
При написании приложения Windows Communication Foundation (WCF), использующий сертификат X.509 для проверки подлинности, часто бывает необходимо задать утверждения из сертификата. Например, при использовании перечисления <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> в методе <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> необходимо указать утверждение отпечатка. Чтобы найти значение утверждения, необходимо выполнить два действия. Сначала необходимо открыть оснастку сертификатов консоли управления (MMC). (См. [Практическое руководство. Просмотр сертификатов с помощью оснастки MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) После этого, как описано в этом разделе, необходимо найти соответствующий сертификат и скопировать его отпечаток (или другие значения утверждений).  
  
 Если сертификат используется для проверки подлинности службы, важно запомнить значение столбца **Кому выдан** (первый столбец консоли). При использовании для защиты транспорта протокола SSL одним из первых шагов является сравнение базового адреса универсального кода ресурса (URI) службы со значением поля **Кому выдан** . Значения должны совпадать, в противном случае процесс проверки подлинности будет прерван.  
  
 Также можно использовать командлет Powershell New-SelfSignedCertificate для создания временных сертификатов для использования только во время разработки. По умолчанию однако такой сертификат не выдан центром сертификации и может использоваться в рабочей среде. Дополнительные сведения см. в разделе [Как Создание временных сертификатов для использования во время разработки](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Извлечение отпечатка сертификата  
  
1. Откройте оснастку "Сертификаты" консоли управления (MMC). (См. [Практическое руководство. Просмотр сертификатов с помощью оснастки MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2. В левой области окна **Корень консоли** щелкните узел **Сертификаты (локальный компьютер)**.  
  
3. Щелкните папку **Личные** , чтобы развернуть ее.  
  
4. Щелкните папку **Сертификаты** , чтобы развернуть ее.  
  
5. В списке сертификатов найдите заголовок **Назначения** . Найдите сертификат, назначением которого является **Проверка подлинности клиента** .  
  
6. Дважды щелкните сертификат.  
  
7. В диалоговом окне **Сертификат** перейдите на вкладку **Состав** .  
  
8. Найдите в списке поле **Отпечаток**и щелкните его.  
  
9. Скопируйте шестнадцатеричные значения из текстового поля. Если этот отпечаток используется в коде `X509FindType`, удалите пробелы между шестнадцатеричными значениями. Например, отпечаток "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" необходимо задавать в коде в виде "a909502dd82ae41433e6f83886b00d4277a32a7b".  
  
## <a name="see-also"></a>См. также

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Практическое руководство. Настройка порта с помощью SSL-сертификата](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Практическое руководство. Просмотр сертификатов с помощью оснастки MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)
- [Практическое руководство. Создание временных сертификатов для использования во время разработки](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
