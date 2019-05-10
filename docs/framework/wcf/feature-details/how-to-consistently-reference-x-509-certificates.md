---
title: Практическое руководство. Согласованное обращение к сертификатам X.509
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2214517784d311cbd0fe487fd6db2cbf48189955
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662793"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="42434-102">Практическое руководство. Согласованное обращение к сертификатам X.509</span><span class="sxs-lookup"><span data-stu-id="42434-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="42434-103">Существует несколько способов идентификации сертификата: с помощью хэша сертификата, имени поставщика и серийного номера, а также идентификатора ключа субъекта (SKI).</span><span class="sxs-lookup"><span data-stu-id="42434-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="42434-104">Идентификатор ключа субъекта (SKI) обеспечивает уникальную идентификацию открытого ключа субъекта сертификата, поэтому он часто используется при работе с цифровой подписью XML.</span><span class="sxs-lookup"><span data-stu-id="42434-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="42434-105">Значение SKI обычно является частью сертификата X.509 в виде *расширения сертификатов X.509*.</span><span class="sxs-lookup"><span data-stu-id="42434-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="42434-106">Windows Communication Foundation (WCF) имеет значение по умолчанию *стиль ссылки* , использующий имя поставщика и серийный номер, если в сертификате отсутствует расширение SKI.</span><span class="sxs-lookup"><span data-stu-id="42434-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="42434-107">Если в сертификате имеется расширение идентификатора ключа субъекта (SKI), стиль ссылки по умолчанию использует его для указания на сертификат.</span><span class="sxs-lookup"><span data-stu-id="42434-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="42434-108">Если в процессе разработки приложения, выполняется переход с сертификатов, которые не имеют расширение SKI на сертификаты, использующие расширение SKI, стиль ссылки, используемые в сообщениях, созданный WCF также изменяется.</span><span class="sxs-lookup"><span data-stu-id="42434-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="42434-109">Если требуется согласованный стиль ссылки независимо от наличия расширения идентификатора ключа субъекта (SKI), необходимый стиль ссылки можно настроить, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="42434-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42434-110">Пример</span><span class="sxs-lookup"><span data-stu-id="42434-110">Example</span></span>  
 <span data-ttu-id="42434-111">В следующем примере кода создается пользовательский элемент привязки безопасности, использующий единый согласованный стиль ссылки с именем издателя и серийным номером.</span><span class="sxs-lookup"><span data-stu-id="42434-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42434-112">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="42434-112">Compiling the Code</span></span>  
 <span data-ttu-id="42434-113">Для компиляции кода требуются следующие пространства имен.</span><span class="sxs-lookup"><span data-stu-id="42434-113">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="42434-114">См. также</span><span class="sxs-lookup"><span data-stu-id="42434-114">See also</span></span>

- [<span data-ttu-id="42434-115">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="42434-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
