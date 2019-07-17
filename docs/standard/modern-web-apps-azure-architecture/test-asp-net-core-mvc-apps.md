---
title: Тестирование приложений MVC ASP.NET Core
description: Разработка современных веб-приложений с помощью ASP.NET Core и Azure | Тестирование приложений MVC ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 941c73f9a8b7b4c4336adfaec45775feec738f51
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804719"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="10c7b-103">Тестирование приложений MVC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10c7b-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="10c7b-104">*"Если вы не хотите выполнять модульное тестирование своего продукта, ваши заказчики также вряд ли захотят делать это".*</span><span class="sxs-lookup"><span data-stu-id="10c7b-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="10c7b-105">\_ -Аноним-</span><span class="sxs-lookup"><span data-stu-id="10c7b-105">\_- Anonymous-</span></span>

<span data-ttu-id="10c7b-106">В ответ на изменения в программном обеспечении любой сложности могут возникать самые непредвиденные ошибки.</span><span class="sxs-lookup"><span data-stu-id="10c7b-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="10c7b-107">Соответственно, после внесения изменений для любых приложений, за исключением самых простых или наименее важных, необходимо проводить тестирование.</span><span class="sxs-lookup"><span data-stu-id="10c7b-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="10c7b-108">Тестирование вручную является самым медленным, наименее надежным и наиболее дорогим способом проверить программное обеспечение.</span><span class="sxs-lookup"><span data-stu-id="10c7b-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="10c7b-109">К сожалению, если возможность тестирования не заложена в приложение на этапе проектирования, это может быть единственный доступный способ.</span><span class="sxs-lookup"><span data-stu-id="10c7b-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="10c7b-110">Приложения, при написании которых соблюдались изложенные в [главе 4](architectural-principles.md) архитектурные принципы, а также приложения ASP.NET Core поддерживают автоматические интеграционные и функциональные тесты.</span><span class="sxs-lookup"><span data-stu-id="10c7b-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="10c7b-111">Виды автоматических тестов</span><span class="sxs-lookup"><span data-stu-id="10c7b-111">Kinds of automated tests</span></span>

<span data-ttu-id="10c7b-112">Существует множество различных автоматических тестов приложений.</span><span class="sxs-lookup"><span data-stu-id="10c7b-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="10c7b-113">Самым простым низкоуровневым подходом является модульное тестирование.</span><span class="sxs-lookup"><span data-stu-id="10c7b-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="10c7b-114">Чуть выше уровнем располагаются интеграционные и функциональные тесты.</span><span class="sxs-lookup"><span data-stu-id="10c7b-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="10c7b-115">В этом документе не описываются другие виды тестирования, в том числе тесты пользовательского интерфейса, нагрузочные тесты и тесты на принятие сборки.</span><span class="sxs-lookup"><span data-stu-id="10c7b-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="10c7b-116">Модульные тесты</span><span class="sxs-lookup"><span data-stu-id="10c7b-116">Unit tests</span></span>

<span data-ttu-id="10c7b-117">В рамках модульного теста проверяется отдельная часть логики вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="10c7b-118">Проще описать те возможности, которые не реализует модульное тестирование.</span><span class="sxs-lookup"><span data-stu-id="10c7b-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="10c7b-119">Модульный тест не позволяет проверить работу кода с зависимостями или инфраструктурой, для чего предназначены интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="10c7b-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="10c7b-120">Модульный тест не позволяет проверить платформу, на которой написан код. Если возникают ошибки такого рода, следует отправить соответствующий отчет и написать код для обходного решения проблемы.</span><span class="sxs-lookup"><span data-stu-id="10c7b-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="10c7b-121">Модульный тест выполняется полностью в памяти и внутри процесса.</span><span class="sxs-lookup"><span data-stu-id="10c7b-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="10c7b-122">Он не взаимодействует с файловой системой, сетью или базой данных.</span><span class="sxs-lookup"><span data-stu-id="10c7b-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="10c7b-123">Модульные тесты предназначены исключительно для тестирования кода.</span><span class="sxs-lookup"><span data-stu-id="10c7b-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="10c7b-124">Поскольку модульные тесты проверяют только один блок кода без каких-либо внешних зависимостей, они должны выполняться предельно быстро.</span><span class="sxs-lookup"><span data-stu-id="10c7b-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="10c7b-125">Таким образом, набор из нескольких сотен модульных тестов может быть выполнен буквально за пару секунд.</span><span class="sxs-lookup"><span data-stu-id="10c7b-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="10c7b-126">Модульные тесты следует выполнять как можно чаще, в идеальном случае перед каждой отправкой в общий репозиторий системы управления версиями и в обязательном порядке перед каждой автоматизированной сборкой на сервере сборки.</span><span class="sxs-lookup"><span data-stu-id="10c7b-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="10c7b-127">Интеграционные тесты</span><span class="sxs-lookup"><span data-stu-id="10c7b-127">Integration tests</span></span>

<span data-ttu-id="10c7b-128">Несмотря на рекомендации по инкапсуляции кода, который взаимодействует с такими инфраструктурами, как базы данных и файловые системы, в некоторых случаях такой код все же используется и требует тестирования.</span><span class="sxs-lookup"><span data-stu-id="10c7b-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="10c7b-129">Кроме того, вам необходимо проверить корректность взаимодействия между слоями вашего кода после того, как будут полностью разрешены все зависимости приложения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="10c7b-130">Для этой цели используются интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="10c7b-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="10c7b-131">Интеграционные тесты выполняются дольше и требуют более тщательной настройки по сравнению с модульными, поскольку они часто полагаются на внешние зависимости и инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="10c7b-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="10c7b-132">В связи с этим по возможности не следует проверять с помощью интеграционных тестов то, что может быть проверено посредством модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-132">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="10c7b-133">Если конкретный сценарий можно проверить с помощью модульного теста, необходимо сделать именно так.</span><span class="sxs-lookup"><span data-stu-id="10c7b-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="10c7b-134">Если это невозможно, тогда попробуйте прибегнуть к интеграционному тестированию.</span><span class="sxs-lookup"><span data-stu-id="10c7b-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="10c7b-135">Процедуры настройки и уничтожения интеграционных тестов обычно гораздо более сложны по сравнению с модульными тестами.</span><span class="sxs-lookup"><span data-stu-id="10c7b-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="10c7b-136">Например, после выполнения интеграционного теста в отношении реальной базы данных необходимо предусмотреть способ возврата базы в известное состояние, которое было до начала тестирования.</span><span class="sxs-lookup"><span data-stu-id="10c7b-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="10c7b-137">С развитием новых тестов, добавляемых в схему рабочей базы данных, возрастает размер и степень сложности таких тестовых скриптов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="10c7b-138">Во многих крупных системах практически нецелесообразно выполнять полный набор интеграционных тестов на рабочих станциях разработчиков перед возвратом изменений в общую систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="10c7b-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="10c7b-139">В таких случаях интеграционные тесты могут выполняться на сервере сборки.</span><span class="sxs-lookup"><span data-stu-id="10c7b-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="10c7b-140">Класс реализации `LocalFileImageService` реализует логику получения и возврата байтов файла изображения из конкретной папки по заданному идентификатору:</span><span class="sxs-lookup"><span data-stu-id="10c7b-140">The `LocalFileImageService` implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a><span data-ttu-id="10c7b-141">Функциональные тесты</span><span class="sxs-lookup"><span data-stu-id="10c7b-141">Functional tests</span></span>

<span data-ttu-id="10c7b-142">Интеграционные тесты позволяют проверить корректность совместной работы нескольких компонентов системы с точки зрения разработчика.</span><span class="sxs-lookup"><span data-stu-id="10c7b-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="10c7b-143">В отличие от них, функциональные тесты позволяют проверить соответствие системы требованиям с точки зрения пользователя.</span><span class="sxs-lookup"><span data-stu-id="10c7b-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="10c7b-144">В следующей цитате приводится наглядная аналогия, позволяющая сравнить функциональные и модульные тесты:</span><span class="sxs-lookup"><span data-stu-id="10c7b-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="10c7b-145">"Разработку системы уже не раз сравнивали с возведением дома.</span><span class="sxs-lookup"><span data-stu-id="10c7b-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="10c7b-146">И хотя это не совсем корректно, на базе этой аналогии мы можем понять разницу между модульным и функциональным тестированием.</span><span class="sxs-lookup"><span data-stu-id="10c7b-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="10c7b-147">Модульное тестирование похоже на посещение строительной площадки инспектором.</span><span class="sxs-lookup"><span data-stu-id="10c7b-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="10c7b-148">Он проверяет различные внутренние системы дома, его фундамент, несущие конструкции, электрические и сантехнические сети, а также множество других компонентов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="10c7b-149">Таким образом, инспектор проверяет (тестирует) безопасность всех частей дома и их соответствие строительным нормам.</span><span class="sxs-lookup"><span data-stu-id="10c7b-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="10c7b-150">В этом контексте функциональные тесты можно сравнить с визитом владельца дома.</span><span class="sxs-lookup"><span data-stu-id="10c7b-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="10c7b-151">Он справедливо полагает, что все внутренние системы были проверены инспектором и, соответственно, функционируют в соответствии с предназначением.</span><span class="sxs-lookup"><span data-stu-id="10c7b-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="10c7b-152">Сам же владелец при этом будет сосредоточен на том, чтобы проверить, насколько комфортно ему будет жить в новом доме.</span><span class="sxs-lookup"><span data-stu-id="10c7b-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="10c7b-153">Он будет проверять внешний вид дома, размер его комнат, соответствие дома потребностям семьи и даже то, не будет ли его в дальнейшем беспокоить утренний свет, попадающий в окна.</span><span class="sxs-lookup"><span data-stu-id="10c7b-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="10c7b-154">Таким образом, владелец дома проводит функциональное тестирование своего жилища.</span><span class="sxs-lookup"><span data-stu-id="10c7b-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="10c7b-155">Важно понимать, что он делает это с точки зрения пользователя.</span><span class="sxs-lookup"><span data-stu-id="10c7b-155">He has the user's perspective.</span></span> <span data-ttu-id="10c7b-156">Инспектор осуществляет модульное тестирование.</span><span class="sxs-lookup"><span data-stu-id="10c7b-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="10c7b-157">Иными словами, он проверяет дом с точки зрения строителя".</span><span class="sxs-lookup"><span data-stu-id="10c7b-157">He has the builder's perspective."</span></span>

<span data-ttu-id="10c7b-158">Источник: [Сравнение модульного и функционального тестирования](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="10c7b-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="10c7b-159">Мне очень нравится следующее выражение: "Как разработчики мы совершаем две главных ошибки: мы создаем вещи неправильно и мы создаем неправильные вещи".</span><span class="sxs-lookup"><span data-stu-id="10c7b-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="10c7b-160">С помощью модульных тестов мы можем убедиться в том, что создаем вещи правильно. Функциональное тестирование позволяет проверить, что мы создаем правильные вещи.</span><span class="sxs-lookup"><span data-stu-id="10c7b-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="10c7b-161">Поскольку функциональные тесты выполняются на уровне системы, для них может потребоваться определенная степень автоматизации пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="10c7b-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="10c7b-162">Как и интеграционные тесты, они обычно имеют дело с определенного вида тестовой инфраструктурой.</span><span class="sxs-lookup"><span data-stu-id="10c7b-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="10c7b-163">Это делает их еще более медленными и нестабильными по сравнению с модульными и интеграционными тестами.</span><span class="sxs-lookup"><span data-stu-id="10c7b-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="10c7b-164">Поэтому необходимо использовать ровно столько функциональных тестов, сколько нужно для того, чтобы гарантировать функционирование системы в соответствии с требованиями пользователя.</span><span class="sxs-lookup"><span data-stu-id="10c7b-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="10c7b-165">Пирамида тестирования</span><span class="sxs-lookup"><span data-stu-id="10c7b-165">Testing Pyramid</span></span>

<span data-ttu-id="10c7b-166">Мартин Фаулер (Martin Fowler) описал пирамиду тестирования, пример которой показан на рис. 9-1.</span><span class="sxs-lookup"><span data-stu-id="10c7b-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="10c7b-167">Рис. 9-1. Пирамида тестирования</span><span class="sxs-lookup"><span data-stu-id="10c7b-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="10c7b-168">Уровни пирамиды и их относительный размер описывают различные виды тестов и их количество, необходимое для проверки приложения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="10c7b-169">Как видно из рисунка, в качестве фундамента рекомендуется брать большое количество модульных тестов, поверх которого проводится меньшее число интеграционных тестов. Венчает же пирамиду малочисленный уровень функциональных тестов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="10c7b-170">В идеале каждый уровень должен содержать только те тесты, которые невозможно выполнить надлежащим образом на более низком уровне.</span><span class="sxs-lookup"><span data-stu-id="10c7b-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="10c7b-171">При выборе теста, который будет выполняться в каждом конкретном сценарии, помните о пирамиде тестирования.</span><span class="sxs-lookup"><span data-stu-id="10c7b-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="10c7b-172">Что следует проверить</span><span class="sxs-lookup"><span data-stu-id="10c7b-172">What to test</span></span>

<span data-ttu-id="10c7b-173">Разработчики, не имеющие достаточного опыта в написании автоматических тестов, часто сталкиваются с проблемой выбора того, что следует проверять.</span><span class="sxs-lookup"><span data-stu-id="10c7b-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="10c7b-174">Для начала рекомендуется проверить условную логику.</span><span class="sxs-lookup"><span data-stu-id="10c7b-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="10c7b-175">Везде, где у вас используется метод, поведение которого изменяется в зависимости от значения условного выражения (if-else, switch и т. д.), следует проводить хотя бы пару тестов, проверяющих корректность поведения при различных условиях.</span><span class="sxs-lookup"><span data-stu-id="10c7b-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="10c7b-176">Если в коде используются условия ошибки, следует написать как минимум один тест для безошибочного прохождения кода и хотя бы один для выполнения кода с ошибками или нетипичными результатами. Это позволит проверить корректность работы приложения при возникновении ошибок.</span><span class="sxs-lookup"><span data-stu-id="10c7b-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="10c7b-177">Наконец, попробуйте сосредоточиться на том, что может пойти не по сценарию, и не зацикливайтесь на таких показателях, как объем протестированного кода.</span><span class="sxs-lookup"><span data-stu-id="10c7b-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="10c7b-178">Тем не менее в большинстве случаев рекомендуется протестировать как можно больший объем кода.</span><span class="sxs-lookup"><span data-stu-id="10c7b-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="10c7b-179">И все же часто лучше потратить больше времени на написание нескольких тестов для сложного критически важного метода, чем многократно проверять автоматические свойства только для того, чтобы увеличить объем протестированного кода.</span><span class="sxs-lookup"><span data-stu-id="10c7b-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="10c7b-180">Упорядочение тестовых проектов</span><span class="sxs-lookup"><span data-stu-id="10c7b-180">Organizing test projects</span></span>

<span data-ttu-id="10c7b-181">Вы можете упорядочивать тестовые проекты так, как это удобно вам.</span><span class="sxs-lookup"><span data-stu-id="10c7b-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="10c7b-182">В качестве общей рекомендации можно посоветовать разделять тесты по виду (модульные, интеграционные) и по тому, что они проверяют (проект, пространство имен).</span><span class="sxs-lookup"><span data-stu-id="10c7b-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="10c7b-183">Будут ли для этого применяться папки в рамках одного тестового проекта или потребуется несколько тестовых проектов, зависит от структуры решения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="10c7b-184">Работать с одним проектом проще, однако для крупных проектов с множеством тестов или для удобства выполнения различных наборов тестов вы можете использовать несколько тестовых проектов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="10c7b-185">Многие команды упорядочивают тестовые проекты на основе проверяемых проектов. В этом случае для приложений с достаточно большим числом проектов может получиться слишком много тестовых проектов, особенно если для каждого из них осуществляется разбиение по виду теста.</span><span class="sxs-lookup"><span data-stu-id="10c7b-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="10c7b-186">В качестве компромисса можно использовать подход с одним проектом для каждого вида теста для каждого приложения. В этом случае проверяемые проекты и классы будут определяться с помощью папок внутри тестовых проектов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="10c7b-187">Типовой подход предполагает размещение проектов приложения в папке src, а тестовых проектов — в параллельной папке tests.</span><span class="sxs-lookup"><span data-stu-id="10c7b-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="10c7b-188">Если это покажется вам более удобным, вы можете создать соответствующие папки решений в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10c7b-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="10c7b-189">Рис. 9-2. Упорядочение тестов для решения</span><span class="sxs-lookup"><span data-stu-id="10c7b-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="10c7b-190">Вы можете использовать любую предпочитаемую платформу тестирования.</span><span class="sxs-lookup"><span data-stu-id="10c7b-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="10c7b-191">Эффективным решением является платформа xUnit, на которой пишутся все тесты для ASP.NET Core и EF Core.</span><span class="sxs-lookup"><span data-stu-id="10c7b-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="10c7b-192">Вы можете добавить тестовый проект xUnit в Visual Studio, используя показанный на рис. 9-3 шаблон или через интерфейс командной строки с помощью команды dotnet new xunit.</span><span class="sxs-lookup"><span data-stu-id="10c7b-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="10c7b-193">Рис. 9-3. Добавление тестового проекта xUnit в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10c7b-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="10c7b-194">Присвоение имен тестам</span><span class="sxs-lookup"><span data-stu-id="10c7b-194">Test naming</span></span>

<span data-ttu-id="10c7b-195">Тестам следует присваивать единообразные имена, которые указывают на выполняемые ими задачи.</span><span class="sxs-lookup"><span data-stu-id="10c7b-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="10c7b-196">Я могу порекомендовать успешно проверенный на практике подход, при котором имена тестовых классов задаются на основе проверяемого ими класса и метода.</span><span class="sxs-lookup"><span data-stu-id="10c7b-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="10c7b-197">В этом случае получается множество небольших тестовых классов, однако можно легко определить, для чего предназначен каждый из них.</span><span class="sxs-lookup"><span data-stu-id="10c7b-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="10c7b-198">Таким образом, имена тестовых классов определяют проверяемый класс и метод. С помощью имени тестового метода можно указать, какое поведение он проверяет.</span><span class="sxs-lookup"><span data-stu-id="10c7b-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="10c7b-199">Это имя должно определять ожидаемое поведение, а также любые принимаемые входные данные и допущения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="10c7b-200">Примеры имен тестов:</span><span class="sxs-lookup"><span data-stu-id="10c7b-200">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="10c7b-201">В качестве варианта можно добавить в конец имени тестового класса слово "Should" (Должен) и слегка изменить формулировку:</span><span class="sxs-lookup"><span data-stu-id="10c7b-201">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="10c7b-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="10c7b-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="10c7b-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="10c7b-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="10c7b-204">Некоторые разработчики считают второй подход более понятным, несмотря на более длинные имена.</span><span class="sxs-lookup"><span data-stu-id="10c7b-204">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="10c7b-205">В любом случае постарайтесь выбрать соглашение об именовании, которое позволит легко определять поведение теста. Благодаря этому в случае неудачного завершения одного или нескольких тестов вы сможете легко определить, что именно не удалось сделать.</span><span class="sxs-lookup"><span data-stu-id="10c7b-205">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="10c7b-206">Не рекомендуется присваивать тестам слишком размытые имена, например ControllerTests.Test1, поскольку по ним вы не сможете определить, на что указывают результаты теста.</span><span class="sxs-lookup"><span data-stu-id="10c7b-206">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="10c7b-207">Если вы используете одно из описываемых выше соглашений об именовании, в результате чего получаете множество небольших тестовых классов, рекомендуется упорядочить тесты по папкам и пространствам имен.</span><span class="sxs-lookup"><span data-stu-id="10c7b-207">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="10c7b-208">На рис. 9-4 показан возможный подход к упорядочению тестов по папкам в рамках нескольких тестовых проектов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-208">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="10c7b-209">**Рис. 9-4.**</span><span class="sxs-lookup"><span data-stu-id="10c7b-209">**Figure 9-4.**</span></span> <span data-ttu-id="10c7b-210">Упорядочение тестовых классов по папкам на основе проверяемых классов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-210">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="10c7b-211">Безусловно, если конкретный класс приложения содержит много проверяемых методов (и, соответственно, много тестовых классов), может быть удобно поместить их в папку, соответствующую классу приложения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-211">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="10c7b-212">Такой подход аналогичен упорядочению обычных файлов в папках.</span><span class="sxs-lookup"><span data-stu-id="10c7b-212">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="10c7b-213">Если в папке, содержащей множество файлов, присутствует больше трех или четырех связанных файлов, их зачастую рекомендуется перенести в отдельную вложенную папку.</span><span class="sxs-lookup"><span data-stu-id="10c7b-213">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="10c7b-214">Модульное тестирование приложений ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10c7b-214">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="10c7b-215">В грамотно спроектированном приложении ASP.NET Core большая часть сложных функций и бизнес-логики инкапсулируется в бизнес-сущностях и различных службах.</span><span class="sxs-lookup"><span data-stu-id="10c7b-215">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="10c7b-216">Таким образом, само приложение MVC ASP.NET Core со всеми его контроллерами, фильтрами, моделями представлений и представлениями должно требовать минимального количества модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="10c7b-216">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="10c7b-217">Большая часть функционала конкретного действия выполняется за пределами самого метода действия.</span><span class="sxs-lookup"><span data-stu-id="10c7b-217">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="10c7b-218">Модульные тесты не позволяют эффективно проверить корректность маршрутизации или глобальной обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="10c7b-218">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="10c7b-219">Кроме того, модульное тестирование не позволяет проверить какие-либо фильтры, в том числе применяемые для подтверждения, проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="10c7b-219">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="10c7b-220">Без этих источников реакции на события большинство методов действия будут иметь небольшой размер, поскольку они делегируют основную часть выполняемых задач службам, которые могут быть протестированы независимо от использующего их контроллера.</span><span class="sxs-lookup"><span data-stu-id="10c7b-220">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="10c7b-221">В некоторых случаях, чтобы провести модульное тестирование кода, требуется выполнить его рефакторинг.</span><span class="sxs-lookup"><span data-stu-id="10c7b-221">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="10c7b-222">Зачастую для этого требуется определить абстракции и использовать внедрение зависимостей для доступа к абстракции в коде, который требуется протестировать, вместо того, чтобы писать код непосредственно для работы с инфраструктурой.</span><span class="sxs-lookup"><span data-stu-id="10c7b-222">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="10c7b-223">Например, рассмотрим простой метод действия для показа изображений:</span><span class="sxs-lookup"><span data-stu-id="10c7b-223">For example, consider this simple action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="10c7b-224">Модульное тестирование этого метода затруднено из-за наличия прямой зависимости от `System.IO.File`, который используется для чтения из файловой системы.</span><span class="sxs-lookup"><span data-stu-id="10c7b-224">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="10c7b-225">Вы можете проверить корректность поведения этого метода, однако для тестирования работы с реальными файлами вам потребуются интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="10c7b-225">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="10c7b-226">Следует отметить, что вы не сможете провести модульные тесты для маршрута этого метода. О том, как можно сделать это, вы узнаете вскоре из описания функционального теста.</span><span class="sxs-lookup"><span data-stu-id="10c7b-226">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="10c7b-227">Что следует проверять, если вы не можете напрямую протестировать поведение файловой системы или маршрут с помощью модульного теста?</span><span class="sxs-lookup"><span data-stu-id="10c7b-227">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="10c7b-228">После рефакторинга, который позволит провести модульное тестирование, вы можете заметить отсутствие некоторых тестовых случаев и функционального поведения, например обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="10c7b-228">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="10c7b-229">Что делает метод в том случае, если файл не найден?</span><span class="sxs-lookup"><span data-stu-id="10c7b-229">What does the method do when a file isn't found?</span></span> <span data-ttu-id="10c7b-230">Что он должен делать в такой ситуации?</span><span class="sxs-lookup"><span data-stu-id="10c7b-230">What should it do?</span></span> <span data-ttu-id="10c7b-231">В этом примере после рефакторинга метод будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="10c7b-231">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="10c7b-232">В качестве зависимостей внедряются \_logger и \_imageService.</span><span class="sxs-lookup"><span data-stu-id="10c7b-232">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="10c7b-233">После этого вы можете проверить, что в \_imageService передается тот же идентификатор, который был передан в метод действия, а полученное число байтов возвращается в FileResult.</span><span class="sxs-lookup"><span data-stu-id="10c7b-233">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="10c7b-234">Также вы можете проверить правильность ведения журнала ошибок, то есть регистрацию результата NotFound в случае отсутствия изображения, поскольку это поведение можно отнести к важным функциям приложения (то есть это не просто временный код, который разработчик добавляет для диагностики проблем).</span><span class="sxs-lookup"><span data-stu-id="10c7b-234">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="10c7b-235">Реальная логика файла вынесена в отдельную службу реализации и дополнена таким образом, чтобы возвращать специфичное для приложения исключение в том случае, если файл не найден.</span><span class="sxs-lookup"><span data-stu-id="10c7b-235">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="10c7b-236">Эту реализацию можно проверить отдельно с помощью интеграционного теста.</span><span class="sxs-lookup"><span data-stu-id="10c7b-236">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="10c7b-237">В большинстве случаев стоит использовать обработчики глобальных исключений в контроллерах, чтобы объем логики в них был минимальным и модульное тестирование не требовалось.</span><span class="sxs-lookup"><span data-stu-id="10c7b-237">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="10c7b-238">Вы должны выполнить большую часть тестирования действий контроллера с помощью функциональных тестов и класса `TestServer`, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="10c7b-238">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="10c7b-239">Интеграционное тестирование приложений ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10c7b-239">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="10c7b-240">Большая часть интеграционных тестов в приложениях ASP.NET Core должны работать со службами и другими типами реализации, определенными в проекте инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="10c7b-240">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="10c7b-241">Например, вы могли бы [проверить, что EF Core успешно обновился и получил ожидаемые данные](https://docs.microsoft.com/ef/core/miscellaneous/testing/) из ваших классов доступа к данным, находящихся в проекте инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="10c7b-241">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="10c7b-242">Лучший способ проверить, правильно ли работает проект ASP.NET Core MVC, — с помощью функциональных тестов, выполняемых при работе приложения на тестовом узле.</span><span class="sxs-lookup"><span data-stu-id="10c7b-242">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="10c7b-243">Функциональное тестирование приложений ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10c7b-243">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="10c7b-244">Для удобства функционального тестирования приложений ASP.NET Core используется класс `TestServer`.</span><span class="sxs-lookup"><span data-stu-id="10c7b-244">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="10c7b-245">Вы настраиваете `TestServer` с помощью `WebHostBuilder` напрямую (как обычно для приложения) или с помощью типа `WebApplicationFactory` (доступно начиная с версии 2.1).</span><span class="sxs-lookup"><span data-stu-id="10c7b-245">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="10c7b-246">Тестовый узел должен максимально соответствовать рабочему узлу, чтобы при тестировании приложение вело себя так же, как в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="10c7b-246">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="10c7b-247">Класс `WebApplicationFactory` помогает настраивать каталог ContentRoot на сервере TestServer, который используется платформой ASP.NET Core для поиска статических ресурсов, таких как представления.</span><span class="sxs-lookup"><span data-stu-id="10c7b-247">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="10c7b-248">Можно создать простые функциональные тесты, создав тестовый класс, который реализует IClassFixture\<WebApplicationFactory\<TEntry>>, где TEntry — это класс запуска веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="10c7b-248">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="10c7b-249">После этого ваше средство тестирования может создать клиента с помощью метода фабрики CreateClient:</span><span class="sxs-lookup"><span data-stu-id="10c7b-249">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="10c7b-250">Как правило, необходимо выполнить дополнительную конфигурацию сайта перед запуском каждого теста, например, настроить приложение, чтобы оно использовало выполняющееся в памяти хранилище данных, а затем заполнилось тестовыми данными.</span><span class="sxs-lookup"><span data-stu-id="10c7b-250">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="10c7b-251">Для этого создайте собственный подкласс WebApplicationFactory\<TEntry> и переопределите его метод ConfigureWebHost.</span><span class="sxs-lookup"><span data-stu-id="10c7b-251">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="10c7b-252">Приведенный ниже пример взят из проекта eShopOnWeb FunctionalTests и используется как часть тестов в главном веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="10c7b-252">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory 
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="10c7b-253">Тесты могут использовать эту пользовательскую фабрику WebApplicationFactory, чтобы с ее помощью создать клиент, а затем делать запросы к приложению, используя этот экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="10c7b-253">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="10c7b-254">Приложение заполнится данными, которые можно использовать в утверждениях теста.</span><span class="sxs-lookup"><span data-stu-id="10c7b-254">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="10c7b-255">Следующий тест проверяет, что домашняя страница приложения eShopOnWeb правильно загружается и содержит список продуктов, который был добавлен в приложение при заполнении данными.</span><span class="sxs-lookup"><span data-stu-id="10c7b-255">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="10c7b-256">Этот функциональный тест выполняет полный стек приложения MVC ASP.NET Core/Razor Pages, включая все существующие фильтры, модули привязки, ПО промежуточного слоя и т. д.</span><span class="sxs-lookup"><span data-stu-id="10c7b-256">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="10c7b-257">Он проверяет, что заданный маршрут ("/") возвращает ожидаемый код состояния успеха и выходные данные HTML.</span><span class="sxs-lookup"><span data-stu-id="10c7b-257">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="10c7b-258">Для этого не настраивается реальный веб-сервер, что позволяет избежать большинства недостатков, связанных с тестированием на реальном веб-сервере (например, проблем с настройкой брандмауэра).</span><span class="sxs-lookup"><span data-stu-id="10c7b-258">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="10c7b-259">Функциональные тесты, выполняемые в отношении TestServer, как правило, медленнее интеграционных и модульных тестов, однако значительно быстрее тестов, которые проводятся по сети с использованием тестового веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="10c7b-259">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="10c7b-260">Используйте функциональные тесты, чтобы убедиться, что стек интерфейса приложения работает надлежащим образом.</span><span class="sxs-lookup"><span data-stu-id="10c7b-260">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="10c7b-261">Эти тесты особенно полезны в случаях, когда вы обнаруживаете дублирование в контроллерах или страницах и решаете эту проблему путем добавления фильтров.</span><span class="sxs-lookup"><span data-stu-id="10c7b-261">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="10c7b-262">В идеале этот рефакторинг не изменит поведение приложения, и набор функциональных тестов проверит это.</span><span class="sxs-lookup"><span data-stu-id="10c7b-262">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="10c7b-263">Справочники — тестирование приложений MVC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10c7b-263">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="10c7b-264">**Тестирование на платформе ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="10c7b-264">**Testing in ASP.NET Core**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="10c7b-265">**Соглашение об именовании модульных тестов**</span><span class="sxs-lookup"><span data-stu-id="10c7b-265">**Unit Test Naming Convention**</span></span>  
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="10c7b-266">**Тестирование EF Core**</span><span class="sxs-lookup"><span data-stu-id="10c7b-266">**Testing EF Core**</span></span>  
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>

>[!div class="step-by-step"]
><span data-ttu-id="10c7b-267">[Назад](work-with-data-in-asp-net-core-apps.md)
>[Вперед](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="10c7b-267">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
