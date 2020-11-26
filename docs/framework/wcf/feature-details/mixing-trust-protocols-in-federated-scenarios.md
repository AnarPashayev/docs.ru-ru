---
title: Использование нескольких протоколов доверия в сценариях федерации
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248179"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="05e01-102">Использование нескольких протоколов доверия в сценариях федерации</span><span class="sxs-lookup"><span data-stu-id="05e01-102">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="05e01-103">Возможны сценарии, в которых федеративные клиенты взаимодействуют со службой и службой маркеров безопасности, версии доверия которых не совпадают.</span><span class="sxs-lookup"><span data-stu-id="05e01-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="05e01-104">Код WSDL службы может содержать утверждение `RequestSecurityTokenTemplate` с элементами WS-Trust, версии которых не совпадают с версией службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="05e01-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="05e01-105">В таких случаях клиент Windows Communication Foundation (WCF) преобразует элементы WS-Trust, полученные из, в, `RequestSecurityTokenTemplate` чтобы соответствовать версии доверия STS.</span><span class="sxs-lookup"><span data-stu-id="05e01-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="05e01-106">WCF обрабатывает несоответствующие версии доверия только для стандартных привязок.</span><span class="sxs-lookup"><span data-stu-id="05e01-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="05e01-107">Все стандартные параметры алгоритма, распознаваемые WCF, являются частью стандартной привязки.</span><span class="sxs-lookup"><span data-stu-id="05e01-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="05e01-108">В этом разделе описывается поведение WCF с различными параметрами доверия между службой и STS.</span><span class="sxs-lookup"><span data-stu-id="05e01-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="05e01-109">Проверяющая сторона и служба маркеров безопасности используют версию февраля 2005 г.</span><span class="sxs-lookup"><span data-stu-id="05e01-109">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="05e01-110">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="05e01-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="05e01-111">Файл конфигурации клиента содержит список параметров.</span><span class="sxs-lookup"><span data-stu-id="05e01-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="05e01-112">WCF не может различить параметры клиента и службы; Он добавляет все параметры и отправляет их в `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="05e01-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="05e01-113">Проверяющая сторона и служба маркеров безопасности используют версию Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="05e01-113">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="05e01-114">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="05e01-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="05e01-115">Файл конфигурации клиента содержит элемент `secondaryParameters`, являющийся оболочкой для параметров, заданных проверяющей стороной.</span><span class="sxs-lookup"><span data-stu-id="05e01-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="05e01-116">WCF удаляет `EncryptionAlgorithm` `CanonicalizationAlgorithm` `KeyWrapAlgorithm` элементы и из элемента верхнего уровня в RST, если они существуют внутри `SecondaryParameters` элемента.</span><span class="sxs-lookup"><span data-stu-id="05e01-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="05e01-117">WCF добавляет `SecondaryParameters` элемент в исходящий RST без изменений.</span><span class="sxs-lookup"><span data-stu-id="05e01-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="05e01-118">Проверяющая сторона использует версию февраля 2005 г., а служба маркеров безопасности - версию Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="05e01-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="05e01-119">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="05e01-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="05e01-120">Файл конфигурации клиента содержит список параметров.</span><span class="sxs-lookup"><span data-stu-id="05e01-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="05e01-121">В файле конфигурации клиента WCF не может различить параметры службы и клиента.</span><span class="sxs-lookup"><span data-stu-id="05e01-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="05e01-122">Поэтому WCF преобразует все параметры в пространство имен доверия версии 1,3.</span><span class="sxs-lookup"><span data-stu-id="05e01-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="05e01-123">WCF обрабатывает `KeyType` элементы, `KeySize` и `TokenType` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="05e01-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="05e01-124">Загружается код WSDL, создается привязка и присваиваются значения `KeyType`, `KeySize` и `TokenType` на основании параметров проверяющей стороны.</span><span class="sxs-lookup"><span data-stu-id="05e01-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="05e01-125">Создается файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="05e01-125">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="05e01-126">Теперь клиент может изменять любые параметры в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="05e01-126">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="05e01-127">Во время выполнения WCF копирует все параметры, указанные в `AdditionalTokenParameters` разделе файла конфигурации клиента, за исключением `KeyType` `KeySize` и `TokenType` , поскольку эти параметры задаются во время создания файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="05e01-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="05e01-128">Проверяющая сторона использует версию Trust 1.3, а служба маркеров безопасности - версию февраля 2005 г.</span><span class="sxs-lookup"><span data-stu-id="05e01-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="05e01-129">Код WSDL проверяющей стороны содержит следующие элементы в разделе `RequestSecurityTokenTemplate`:</span><span class="sxs-lookup"><span data-stu-id="05e01-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="05e01-130">Файл конфигурации клиента содержит элемент `secondaryParamters`, являющийся оболочкой для параметров, заданных проверяющей стороной.</span><span class="sxs-lookup"><span data-stu-id="05e01-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="05e01-131">WCF копирует все параметры, указанные в `SecondaryParameters` разделе, в элемент RST верхнего уровня, но не преобразует их в пространство имен 2005 WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="05e01-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
