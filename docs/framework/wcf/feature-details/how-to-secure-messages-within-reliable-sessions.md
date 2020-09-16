---
title: Практическое руководство. Защита сообщений с помощью надежных сеансов
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: cec9356467886be022d05ead55d5cb6ccddcd838
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558684"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="8ad6e-102">Практическое руководство. Защита сообщений с помощью надежных сеансов</span><span class="sxs-lookup"><span data-stu-id="8ad6e-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="8ad6e-103">В этом разделе описывается обеспечение безопасности на уровне сообщения в ходе надежного сеанса обмена сообщениями с использованием одной из предоставляемых системой привязок, которые поддерживают такие сеансы, но не по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="8ad6e-104">Включите безопасный, надежный сеанс принудительно с помощью кода или декларативно в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="8ad6e-105">В этой процедуре для разрешения защищенного, надежного сеанса используются файлы конфигурации клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="8ad6e-106">Эта процедура включает выполнение трех основных задач, а именно:</span><span class="sxs-lookup"><span data-stu-id="8ad6e-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="8ad6e-107">необходимо задать, что клиент и служба обмениваются сообщениями в ходе надежного сеанса;</span><span class="sxs-lookup"><span data-stu-id="8ad6e-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="8ad6e-108">необходимо обеспечить безопасность на уровне сообщения в ходе надежного сеанса;</span><span class="sxs-lookup"><span data-stu-id="8ad6e-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="8ad6e-109">необходимо задать тип учетных данных клиента, который должен использоваться при проверке подлинности клиента в службе.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="8ad6e-110">В первой задаче важно, чтобы элемент конфигурации конечной точки содержал `bindingConfiguration` атрибут, который ссылается на конфигурацию привязки с именем (в этом примере) `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="8ad6e-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Элемент Configuration затем ссылается на это имя, чтобы включить надежные сеансы, задав `enabled` атрибуту [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) элемента значение `true` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="8ad6e-112">Можно потребовать гарантии упорядоченной доставки сообщений в ходе надежного сеанса, присвоив атрибуту `ordered` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="8ad6e-113">Исходный экземпляр примера, на котором основана эта процедура конфигурации, см. в разделе [надежный сеанс WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6e-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="8ad6e-114">Ключевые элементы второй задачи выполняются путем установки `mode` атрибута **\<security>** элемента, содержащегося в **\<binding>** элементе клиента и службы, на `Message` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="8ad6e-115">Наиболее важными элементами третьей задачи является установка `clientCredentialType` атрибута **\<message>** элемента, содержащегося в **\<security>** элементе клиента и службы, в значение `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="8ad6e-116">При использовании безопасности сообщений с надежными сеансами надежный обмен сообщениями пытается проверить подлинность клиента, не прошедшего проверку подлинности, до тех пор, пока не будет вызвано исключение при первом сбое.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="8ad6e-117">Настройка службы с помощью WSHttpBinding для использования надежного сеанса</span><span class="sxs-lookup"><span data-stu-id="8ad6e-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="8ad6e-118">Эта процедура описана в разделе [как обмениваться сообщениями в надежном сеансе](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6e-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="8ad6e-119">Настройка клиента с помощью WSHttpBinding для использования надежного сеанса</span><span class="sxs-lookup"><span data-stu-id="8ad6e-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="8ad6e-120">Эта процедура описана в разделе [как обмениваться сообщениями в надежном сеансе](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6e-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="8ad6e-121">Установка режима и ClientCredentialType в конфигурации</span><span class="sxs-lookup"><span data-stu-id="8ad6e-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="8ad6e-122">Добавьте соответствующий элемент привязки в [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) элемент файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="8ad6e-123">В следующем примере добавляется [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="8ad6e-124">Добавьте **\<binding>** элемент и присвойте его `name` атрибуту соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="8ad6e-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="8ad6e-125">В примере используется имя `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="8ad6e-126">Добавьте **\<security>** элемент и присвойте `mode` атрибуту значение `Message` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="8ad6e-127">В **\<security>** элементе добавьте **\<message>** элемент и присвойте `clientCredentialType` атрибуту значение `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="8ad6e-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
