---
title: Практическое руководство. Порядок отключения безопасных сеансов в WSFederationHttpBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972052"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="2abd6-102">Практическое руководство. Порядок отключения безопасных сеансов в WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2abd6-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="2abd6-103">Некоторые службы могут требовать федеративных учетных данных, но не поддерживать безопасные сеансы.</span><span class="sxs-lookup"><span data-stu-id="2abd6-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="2abd6-104">В этом случае необходимо отключить возможность безопасных сеансов.</span><span class="sxs-lookup"><span data-stu-id="2abd6-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="2abd6-105">В отличие от класса <xref:System.ServiceModel.WSHttpBinding>, класс <xref:System.ServiceModel.WSFederationHttpBinding> не предоставляет способа отключения безопасных сеансов при взаимодействии со службой.</span><span class="sxs-lookup"><span data-stu-id="2abd6-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="2abd6-106">Вместо этого необходимо создать пользовательскую привязку, которая заменяет параметры безопасного сеанса начальной загрузкой.</span><span class="sxs-lookup"><span data-stu-id="2abd6-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="2abd6-107">В этом разделе показано, как изменить элементы привязки, содержащиеся в привязке <xref:System.ServiceModel.WSFederationHttpBinding>, чтобы создать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="2abd6-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="2abd6-108">Результат совпадает с <xref:System.ServiceModel.WSFederationHttpBinding>, за исключением того, что не используются безопасные сеансы.</span><span class="sxs-lookup"><span data-stu-id="2abd6-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="2abd6-109">Создание пользовательской федеративной привязки без безопасных сеансов</span><span class="sxs-lookup"><span data-stu-id="2abd6-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="2abd6-110">Создайте экземпляр класса <xref:System.ServiceModel.WSFederationHttpBinding> либо принудительно в коде, либо загрузив один из файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2abd6-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="2abd6-111">Клонируйте <xref:System.ServiceModel.WSFederationHttpBinding> в <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="2abd6-112">Найдите <xref:System.ServiceModel.Channels.SecurityBindingElement> в <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="2abd6-113">Найдите <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> в <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="2abd6-114">Замените исходный элемент <xref:System.ServiceModel.Channels.SecurityBindingElement> элементом привязки безопасности начальной загрузки из <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="2abd6-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="2abd6-115">Пример</span><span class="sxs-lookup"><span data-stu-id="2abd6-115">Example</span></span>

<span data-ttu-id="2abd6-116">В следующем примере создается пользовательская федеративная привязка без безопасных сеансов.</span><span class="sxs-lookup"><span data-stu-id="2abd6-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="2abd6-117">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="2abd6-117">Compiling the Code</span></span>

- <span data-ttu-id="2abd6-118">Чтобы скомпилировать этот пример кода, создайте проект, ссылающийся на сборку System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="2abd6-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="2abd6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="2abd6-119">See also</span></span>

- [<span data-ttu-id="2abd6-120">Привязки и безопасность</span><span class="sxs-lookup"><span data-stu-id="2abd6-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
