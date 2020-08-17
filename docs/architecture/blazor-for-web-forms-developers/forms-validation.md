---
title: Формы и проверка
description: Узнайте, как создавать формы с помощью проверки на стороне клиента в Blazor .
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: d2dce23996e996a736b04c9cdd1ccf3b549ff3ff
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267559"
---
# <a name="forms-and-validation"></a><span data-ttu-id="697e2-103">Формы и проверка</span><span class="sxs-lookup"><span data-stu-id="697e2-103">Forms and validation</span></span>

<span data-ttu-id="697e2-104">Платформа веб-форм ASP.NET включает набор проверочных элементов управления для проверки вводимых пользователем данных, вводимых в форму ( `RequiredFieldValidator` ,, `CompareValidator` `RangeValidator` и т. д.).</span><span class="sxs-lookup"><span data-stu-id="697e2-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="697e2-105">Платформа веб-форм ASP.NET также поддерживает привязку модели и проверку модели на основе заметок к данным ( `[Required]` ,, `[StringLength]` `[Range]` и т. д.).</span><span class="sxs-lookup"><span data-stu-id="697e2-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="697e2-106">Логика проверки может быть применена как на сервере, так и на клиенте с помощью ненавязчивой проверки на основе JavaScript.</span><span class="sxs-lookup"><span data-stu-id="697e2-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="697e2-107">`ValidationSummary`Серверный элемент управления используется для вывода сводки об ошибках проверки для пользователя.</span><span class="sxs-lookup"><span data-stu-id="697e2-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="697e2-108">Blazor поддерживает совместное использование логики проверки между клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="697e2-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="697e2-109">ASP.NET предоставляет предварительно построенные реализации JavaScript многих распространенных проверок серверов.</span><span class="sxs-lookup"><span data-stu-id="697e2-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="697e2-110">Во многих случаях разработчику по-прежнему нужно писать JavaScript для полной реализации логики проверки, зависящей от приложения.</span><span class="sxs-lookup"><span data-stu-id="697e2-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="697e2-111">Те же типы моделей, аннотации данных и логику проверки можно использовать как на сервере, так и на клиенте.</span><span class="sxs-lookup"><span data-stu-id="697e2-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="697e2-112">Blazor предоставляет набор входных компонентов.</span><span class="sxs-lookup"><span data-stu-id="697e2-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="697e2-113">Входные компоненты обрабатывали данные полей привязки в модели и проверяют ввод пользователя при отправке формы.</span><span class="sxs-lookup"><span data-stu-id="697e2-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="697e2-114">Компонент ввода</span><span class="sxs-lookup"><span data-stu-id="697e2-114">Input component</span></span>|<span data-ttu-id="697e2-115">Визуализированный HTML-элемент</span><span class="sxs-lookup"><span data-stu-id="697e2-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="697e2-116">`EditForm`Компонент заключает эти входные компоненты в оболочку и управляет процессом проверки с помощью `EditContext` .</span><span class="sxs-lookup"><span data-stu-id="697e2-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="697e2-117">При создании объекта `EditForm` необходимо указать, с каким экземпляром модели будет осуществляться привязка, с помощью `Model` параметра.</span><span class="sxs-lookup"><span data-stu-id="697e2-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="697e2-118">Проверка обычно выполняется с помощью заметок к данным и является расширяемой.</span><span class="sxs-lookup"><span data-stu-id="697e2-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="697e2-119">Чтобы включить проверку на основе заметок данных, добавьте `DataAnnotationsValidator` компонент в качестве дочернего элемента `EditForm` .</span><span class="sxs-lookup"><span data-stu-id="697e2-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="697e2-120">`EditForm`Компонент предоставляет удобное событие для обработки допустимых ( `OnValidSubmit` ) и недопустимых ( `OnInvalidSubmit` ) отправок.</span><span class="sxs-lookup"><span data-stu-id="697e2-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="697e2-121">Кроме того, существует более универсальное `OnSubmit` событие, которое позволяет самостоятельно инициировать и выполнять проверку.</span><span class="sxs-lookup"><span data-stu-id="697e2-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="697e2-122">Чтобы отобразить сводку ошибок проверки, используйте `ValidationSummary` компонент.</span><span class="sxs-lookup"><span data-stu-id="697e2-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="697e2-123">Чтобы отобразить сообщения проверки для определенного поля ввода, используйте `ValidationMessage` компонент, указав лямбда-выражение для `For` параметра, указывающего на соответствующий элемент модели.</span><span class="sxs-lookup"><span data-stu-id="697e2-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="697e2-124">Следующий тип модели определяет несколько правил проверки с помощью заметок к данным:</span><span class="sxs-lookup"><span data-stu-id="697e2-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="697e2-125">Следующий компонент демонстрирует создание формы в зависимости от Blazor `Starship` типа модели.</span><span class="sxs-lookup"><span data-stu-id="697e2-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="697e2-126">После отправки формы данные, привязанные к модели, не сохранялись в хранилище данных, например в базе данных.</span><span class="sxs-lookup"><span data-stu-id="697e2-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="697e2-127">В Blazor WebAssembly приложении данные должны быть отправлены на сервер.</span><span class="sxs-lookup"><span data-stu-id="697e2-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="697e2-128">Например, с помощью запроса HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="697e2-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="697e2-129">В Blazor серверном приложении данные уже находятся на сервере, но должны быть сохранены.</span><span class="sxs-lookup"><span data-stu-id="697e2-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="697e2-130">Обработка доступа к данным в Blazor приложениях — это тема раздела " [Работа с данными](data.md) ".</span><span class="sxs-lookup"><span data-stu-id="697e2-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="697e2-131">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="697e2-131">Additional resources</span></span>

<span data-ttu-id="697e2-132">Дополнительные сведения о [формах и проверке](/aspnet/core/blazor/forms-validation) в Blazor приложениях см Blazor . в документации.</span><span class="sxs-lookup"><span data-stu-id="697e2-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="697e2-133">[Назад](state-management.md)
>[Вперед](data.md)</span><span class="sxs-lookup"><span data-stu-id="697e2-133">[Previous](state-management.md)
[Next](data.md)</span></span>
