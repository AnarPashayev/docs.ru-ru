---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237444"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="3943b-101">Значение по умолчанию HttpRequestMessage.Version изменено на 1.1</span><span class="sxs-lookup"><span data-stu-id="3943b-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span> 

<span data-ttu-id="3943b-102">Значение свойства <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> по умолчанию изменено с 2.0 на 1.1.</span><span class="sxs-lookup"><span data-stu-id="3943b-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3943b-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3943b-103">Version introduced</span></span>

<span data-ttu-id="3943b-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3943b-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="3943b-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="3943b-105">Change description</span></span>

<span data-ttu-id="3943b-106">В .NET Core с 1.0 по 2.0 значением свойства <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> по умолчанию является 1.1.</span><span class="sxs-lookup"><span data-stu-id="3943b-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="3943b-107">Начиная с .NET Core 2.1 оно было изменено на 2.1.</span><span class="sxs-lookup"><span data-stu-id="3943b-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span> 

<span data-ttu-id="3943b-108">Начиная с .NET Core 3.0 номер версии по умолчанию, возвращаемый свойством <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>, снова стал 1.1.</span><span class="sxs-lookup"><span data-stu-id="3943b-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="3943b-109">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="3943b-109">Recommended action</span></span>

<span data-ttu-id="3943b-110">Обновите код, если он зависит от свойства <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>, возвращающего значение по умолчанию 2.0.</span><span class="sxs-lookup"><span data-stu-id="3943b-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="3943b-111">Категория</span><span class="sxs-lookup"><span data-stu-id="3943b-111">Category</span></span>

<span data-ttu-id="3943b-112">Сети</span><span class="sxs-lookup"><span data-stu-id="3943b-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3943b-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3943b-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

