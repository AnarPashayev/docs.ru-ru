---
title: Общие сведения об интеграции с приложениями COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c283e7cbc4cb4b8bc37dd1313480410df93a93bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596829"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="b0762-102">Общие сведения об интеграции с приложениями COM</span><span class="sxs-lookup"><span data-stu-id="b0762-102">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="b0762-103">Windows Communication Foundation (WCF) предоставляет разработчику управляемого кода обширную среду для создания подключенных приложений.</span><span class="sxs-lookup"><span data-stu-id="b0762-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="b0762-104">Однако если у вас есть существенные инвестиции в неуправляемый код на основе COM и вы не хотите выполнять миграцию, веб-службы WCF можно интегрировать непосредственно в существующий код с помощью моникера службы WCF.</span><span class="sxs-lookup"><span data-stu-id="b0762-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="b0762-105">Моникер служб можно использовать в широком наборе сред разработки на базе модели COM, например в Office VBA, Visual Basic 6.0 и Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="b0762-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="b0762-106">Моникер службы использует канал связи WCF для всего обмена данными.</span><span class="sxs-lookup"><span data-stu-id="b0762-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="b0762-107">Механизмы безопасности и идентификации для этого канала отличаются от механизмов, используемых в стандартных прокси-средствах COM и DCOM.</span><span class="sxs-lookup"><span data-stu-id="b0762-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="b0762-108">Кроме того, поскольку моникер службы использует канал связи WCF, время ожидания по умолчанию составляет одну минуту для всех вызовов.</span><span class="sxs-lookup"><span data-stu-id="b0762-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="b0762-109">Моникер службы используется с `GetObject` функцией для предоставления неуправляемому разработчику строго типизированного, зависящего от com подхода к вызову веб-служб WCF.</span><span class="sxs-lookup"><span data-stu-id="b0762-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="b0762-110">Для этого требуется локальное, видимое COM определение контракта веб-службы WCF и используемой привязки.</span><span class="sxs-lookup"><span data-stu-id="b0762-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="b0762-111">Как и другие клиенты WCF, моникер службы должен создать типизированный канал для службы, хотя эта конструкция канала прозрачна для программиста COM при первом вызове метода.</span><span class="sxs-lookup"><span data-stu-id="b0762-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="b0762-112">В общих случаях с другими клиентами WCF при использовании моникера приложения указывают адрес, привязку и контракт для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="b0762-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="b0762-113">Контракт можно задать одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="b0762-113">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="b0762-114">Типизированный контракт: контракт регистрируется как видимый для модели COM тип на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="b0762-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="b0762-115">Контракт WSDL: контракт предоставляется в виде документа WSDL.</span><span class="sxs-lookup"><span data-stu-id="b0762-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="b0762-116">Контракт MEX: контракт получается в среде выполнения из конечной точки обмена метаданными (MEX).</span><span class="sxs-lookup"><span data-stu-id="b0762-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="b0762-117">Параметры, поддерживаемые моникером служб</span><span class="sxs-lookup"><span data-stu-id="b0762-117">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="b0762-118">В следующей таблице представлены параметры, поддерживаемые моникером служб.</span><span class="sxs-lookup"><span data-stu-id="b0762-118">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="b0762-119">Параметр</span><span class="sxs-lookup"><span data-stu-id="b0762-119">Parameter</span></span>|<span data-ttu-id="b0762-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b0762-120">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="b0762-121">URL-адрес службы.</span><span class="sxs-lookup"><span data-stu-id="b0762-121">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="b0762-122">Имя раздела привязки из конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="b0762-122">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="b0762-123">Именованный экземпляр привязки из именованного раздела привязки.</span><span class="sxs-lookup"><span data-stu-id="b0762-123">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="b0762-124">Идентификатор интерфейса (IID), представляющий контракт службы или имя контракта (из MEX).</span><span class="sxs-lookup"><span data-stu-id="b0762-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="b0762-125">Документ WSDL, обеспечивающий альтернативную форму определения контракта.</span><span class="sxs-lookup"><span data-stu-id="b0762-125">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="b0762-126">Идентификатор имени участника на уровне сервера (SPN), который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="b0762-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="b0762-127">Идентификатор имени участника-пользователя (UPN), который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="b0762-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="b0762-128">Идентификатор DNS, который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="b0762-128">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="b0762-129">URL-адрес конечной точки службы для обмена метаданными (MEX).</span><span class="sxs-lookup"><span data-stu-id="b0762-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="b0762-130">Имя раздела привязки из конфигурации приложения для соединения с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="b0762-131">Именованный экземпляр привязки из именованного раздела привязки для соединения с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="b0762-132">Пространство имен для имени раздела привязки, полученное в результате MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-132">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="b0762-133">Пространство имен контракта, полученное в результате MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-133">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="b0762-134">Идентификатор имени участника на уровне сервера (SPN), который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="b0762-135">Идентификатор имени участника-пользователя (UPN), который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="b0762-136">Идентификатор DNS, который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="b0762-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="b0762-137">Позволяет задать использование сериализатора "xml" или "datacontract".</span><span class="sxs-lookup"><span data-stu-id="b0762-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="b0762-138">Даже при использовании с полностью основанными на COM клиентами для моникера службы требуется WCF, а на клиентском компьютере должна быть установлена поддержка .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b0762-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="b0762-139">Также важно, чтобы в клиентские приложения, использующие моникер служб, была загружена соответствующая версия среды выполнения платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0762-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="b0762-140">При использовании моникера в приложениях Office может потребоваться файл конфигурации, чтобы обеспечить загрузку надлежащей версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0762-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="b0762-141">Например, при использовании Excel файл Excel.exe.config, расположенный в том же каталоге, что и файл Excel.exe, должен содержать следующий текст:</span><span class="sxs-lookup"><span data-stu-id="b0762-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="b0762-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="b0762-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="b0762-143">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="b0762-143">See also</span></span>

- [<span data-ttu-id="b0762-144">Практическое руководство. Регистрация и настройка моникера службы</span><span class="sxs-lookup"><span data-stu-id="b0762-144">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
