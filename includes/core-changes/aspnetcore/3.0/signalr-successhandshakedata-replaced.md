---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901855"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="ca240-101">SignalR. Замена HandshakeProtocol.SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="ca240-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="ca240-102">Поле [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) было удалено и заменено вспомогательным методом, который создает ответ об успешном подтверждении с учетом определенного `IHubProtocol`.</span><span class="sxs-lookup"><span data-stu-id="ca240-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca240-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ca240-103">Version introduced</span></span>

<span data-ttu-id="ca240-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ca240-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ca240-105">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="ca240-105">Old behavior</span></span>

<span data-ttu-id="ca240-106">`HandshakeProtocol.SuccessHandshakeData` являлось полем `public static ReadOnlyMemory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="ca240-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ca240-107">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="ca240-107">New behavior</span></span>

<span data-ttu-id="ca240-108">`HandshakeProtocol.SuccessHandshakeData` заменено методом `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, который возвращает `ReadOnlyMemory<byte>` на основе указанного протокола.</span><span class="sxs-lookup"><span data-stu-id="ca240-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ca240-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="ca240-109">Reason for change</span></span>

<span data-ttu-id="ca240-110">Дополнительные поля были добавлены в _ответ_ подтверждения, которые не являются константами и отличаются в зависимости от выбранного протокола.</span><span class="sxs-lookup"><span data-stu-id="ca240-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca240-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ca240-111">Recommended action</span></span>

<span data-ttu-id="ca240-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ca240-112">None.</span></span> <span data-ttu-id="ca240-113">Этот тип не предназначен для использования из пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="ca240-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="ca240-114">Это `public`, поэтому он может быть общим для сервера SignalR и клиента.</span><span class="sxs-lookup"><span data-stu-id="ca240-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="ca240-115">Он также может использоваться клиентами SignalR пользователя, написанными на .NET.</span><span class="sxs-lookup"><span data-stu-id="ca240-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="ca240-116">Это изменение не влияет на **пользователей** SignalR.</span><span class="sxs-lookup"><span data-stu-id="ca240-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="ca240-117">Категория</span><span class="sxs-lookup"><span data-stu-id="ca240-117">Category</span></span>

<span data-ttu-id="ca240-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ca240-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca240-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ca240-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
