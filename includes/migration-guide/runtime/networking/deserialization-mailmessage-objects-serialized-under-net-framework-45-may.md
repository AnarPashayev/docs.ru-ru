---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235953"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="a6ce3-101">Десериализация объектов MailMessage, сериализованных в .NET Framework 4.5, может завершиться сбоем</span><span class="sxs-lookup"><span data-stu-id="a6ce3-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a6ce3-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="a6ce3-102">Details</span></span>|<span data-ttu-id="a6ce3-103">Начиная с версии .NET Framework 4.5, объекты <xref:System.Web.Mail.MailMessage> могут содержать символы, отличные от ASCII.</span><span class="sxs-lookup"><span data-stu-id="a6ce3-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="a6ce3-104">В .NET Framework 4 поддерживаются только символы ASCII.</span><span class="sxs-lookup"><span data-stu-id="a6ce3-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="a6ce3-105">В .NET Framework 4 не могут быть десериализованы объекты <xref:System.Web.Mail.MailMessage>, содержащие отличные от ASCII символы и сериализованные в .NET Framework 4.5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="a6ce3-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>|
|<span data-ttu-id="a6ce3-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="a6ce3-106">Suggestion</span></span>|<span data-ttu-id="a6ce3-107">Убедитесь, что в коде реализована обработка исключений при десериализации объекта <xref:System.Web.Mail.MailMessage>.</span><span class="sxs-lookup"><span data-stu-id="a6ce3-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>|
|<span data-ttu-id="a6ce3-108">Область</span><span class="sxs-lookup"><span data-stu-id="a6ce3-108">Scope</span></span>|<span data-ttu-id="a6ce3-109">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="a6ce3-109">Minor</span></span>|
|<span data-ttu-id="a6ce3-110">Версия</span><span class="sxs-lookup"><span data-stu-id="a6ce3-110">Version</span></span>|<span data-ttu-id="a6ce3-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a6ce3-111">4.5</span></span>|
|<span data-ttu-id="a6ce3-112">Тип</span><span class="sxs-lookup"><span data-stu-id="a6ce3-112">Type</span></span>|<span data-ttu-id="a6ce3-113">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="a6ce3-113">Runtime</span></span>|
|<span data-ttu-id="a6ce3-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a6ce3-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
