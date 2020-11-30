---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032774"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP. Изменения инфраструктуры текста ответа

Инфраструктура текста ответа HTTP изменена. Если вы используете `HttpResponse` напрямую, вам не нужно вносить никаких изменений в код. См. сведения ниже, если вы используете оболочку, заменяете `HttpResponse.Body` или обращаетесь к `HttpContext.Features`.

#### <a name="version-introduced"></a>Представленная версия

3.0

#### <a name="old-behavior"></a>Старое поведение

С текстом ответа HTTP связаны три API:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Новое поведение

При замене `HttpResponse.Body` полностью заменяется `IHttpResponseBodyFeature` с оболочкой вокруг указанного потока с помощью `StreamResponseBodyFeature` для предоставления реализаций по умолчанию для всех ожидаемых API. Возврат к исходному потоку отменяет это изменение.

#### <a name="reason-for-change"></a>Причина изменения

Объединение API текста ответа в единый новый интерфейс функций.

#### <a name="recommended-action"></a>Рекомендованное действие

Используйте `IHttpResponseBodyFeature` том, где ранее использовали `IHttpResponseFeature.Body`, `IHttpSendFileFeature` или `IHttpBufferingFeature`.

#### <a name="category"></a>Категория

ASP.NET Core

#### <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
