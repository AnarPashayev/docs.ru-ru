---
title: Реализация операций чтения и запросов в микрослужбе CQRS
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Реализация стороны запросов CQRS в микрослужбе заказов в eShopOnContainers с помощью Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 41932122326cf4c49b9c9e2c344d2ac17da7466b
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358899"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Реализация операций чтения и запросов в микрослужбе CQRS

При выполнении операций чтения и запросов микрослужба заказов в примере приложения eShopOnContainers реализует запросы независимо от модели проблемно-ориентированного программирования (DDD) и области транзакций. Это было сделано, главным образом, потому, что требования к запросам и транзакциям значительно отличаются. Операции записи выполняют транзакции, которые должны соответствовать логике предметной области. Запросы, с другой стороны, являются идемпотентными, их можно отделить от правил предметной области.

Это простой подход, как показано на рис. 7-3. API-интерфейс реализуется контроллерами веб-API с помощью любой инфраструктуры, например микро-ORM (средство объектно-реляционного отображения), такого как Dapper, и возвращения динамических ViewModel, в зависимости от потребностей приложения пользовательского интерфейса.

![Схема, на которой в общем показана сторона запросов в упрощенной микрослужбе CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Рис. 7-3**. Самый простой метод запросов в микрослужбе CQRS

Самый простой вариант для стороны запросов в упрощенном подходе CQRS можно реализовать путем запросов базы данных с помощью Micro-ORM, например Dapper, для возврата динамических ViewModel. Определения запроса обращаются к базе данных и возвращают динамическую ViewModel, которая создается в режиме реального времени для каждого запроса. Поскольку запросы идемпотентны, они не меняют данные, сколько бы раз вы ни выполняли запрос. Значит, вам не нужно ограничиваться шаблоном DDD, используемым на стороне транзакций, например статистическими выражениями и другими шаблонами. Поэтому запросы отделены от области транзакций. Вы запрашиваете у базы данных необходимые для пользовательского интерфейса данные и получаете динамические ViewModel, которые не нужно статически определять нигде, кроме самих инструкций SQL (для ViewModel нет классов).

Это простой подход, поэтому код на стороне запросов (например, код, использующий микро-ORM, вроде [Dapper](https://github.com/StackExchange/Dapper)) можно реализовать [в том же проекте веб-API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Это показано на рис. 7-4. Запросы определяются в проекте микрослужбы **Ordering.API** в решении eShopOnContainers.

![Снимок экрана: папка Queries в проекте Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Рис. 7-4**. Запросы в микрослужбе заказов в eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Использование моделей представления, специально созданных для клиентских приложений, независимо от ограничений модели предметной области

Поскольку запросы выполняются для получения данных, необходимых клиентским приложениям, можно создать тип возвращаемого значения специально для клиентов на основе данных, возвращаемых запросами. Эти модели, или объекты передачи данных (DTO), называются ViewModel.

Возвращаемые данные (ViewModel) могут быть результатом объединения данных из нескольких сущностей или таблиц в базе данных или даже нескольких статистических выражений, определенных в модели предметной области для области транзакций. В этом случае, так как вы создаете запросы независимо от модели предметной области, границы и ограничения статистических выражений игнорируются, и вы можете обратиться к любой нужной таблице или столбцу. Такой подход обеспечивает большую гибкость и производительность для разработчиков, создающих или обновляющих запросы.

ViewModels могут быть статическими типами, определенными в классах (как реализовано в микрослужбе заказов). Они также могут создаваться динамически в зависимости от выполненных запросов, что очень удобно для разработчиков.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Использование Dapper в качестве микро-ORM для выполнения запросов

Для запросов вы можете использовать любой микро-ORM, Entity Framework Core или даже просто ADO.NET. В примере приложения eShopOnContainers Dapper выбран для микрослужбы заказов как хороший пример популярного микро-ORM. Он может выполнять обычные SQL-запросы с высокой производительностью благодаря легкости платформы. С помощью Dapper вы можете написать SQL-запрос, который обратится к нескольким таблицам и соединит их.

Dapper — это проект с открытым кодом (изначально созданный Сэмом Сэффроном), который является частью стандартных блоков, используемых в [Stack Overflow](https://stackoverflow.com/). Чтобы использовать Dapper, просто установите его с помощью [пакета Dapper NuGet](https://www.nuget.org/packages/Dapper), как показано на рисунке:

![Снимок экрана: пакет Dapper в представлении пакетов NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Затем добавьте директиву `using`, чтобы у кода был доступ к методам расширения Dapper.

При добавлении Dapper в код вы напрямую используете класс <xref:System.Data.SqlClient.SqlConnection>, доступный в пространстве имен <xref:System.Data.SqlClient>. Метод QueryAsync и другие методы расширения, которые расширяют класс <xref:System.Data.SqlClient.SqlConnection>, — это прямой и эффективный способ выполнения запросов.

## <a name="dynamic-versus-static-viewmodels"></a>Динамические и статические модели ViewModel

Когда модели представления возвращаются с сервера в клиентские приложения, их можно представить себе в виде объектов передачи данных (DTO), которые могут отличаться для внутренних сущностей предметной области в вашей модели сущностей, поскольку модели представления хранят данные так, как это необходимо клиентскому приложению. Поэтому во многих случаях вы можете объединять данные из нескольких сущностей предметной области и составлять модели ViewModel в точном соответствии с требованиями клиентского приложения.

Эти ViewModel или DTO могут быть определены явным образом (в виде классов-владельцев данных), как и представленный выше класс `OrderSummary`. Вы также можете просто вернуть динамические ViewModel или DTO на основе атрибутов, полученных из запросов в виде динамических типов.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel как динамический тип

Как показано в следующем коде, `ViewModel` можно получить напрямую с помощью запросов, вернув *динамический* тип, который внутренне основан на атрибутах, возвращенных запросом. Это означает, что подмножество атрибутов, которое будет возвращено, основано на самом запросе. Поэтому, если вы добавляете в запрос или соединение новый столбец, данные динамически добавляются к возвращаемой `ViewModel`.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

Важно отметить, что при использовании динамического типа возвращенная коллекция данных динамически собирается в виде ViewModel.

**Преимущества.** При этом подходе можно реже менять статические классы ViewModel при обновлении SQL-предложения запроса, что очень удобно при написании кода. Это простой метод, позволяющий быстро приспособиться к изменениям в будущем.

**Недостатки.** В долгосрочной перспективе использование динамических типов может негативно отразиться на ясности и повлиять на совместимость службы с клиентскими приложениями. Кроме того, ПО промежуточного слоя, например Swashbuckle, не может предоставить тот же уровень документации для типов возвращаемого значения, если вы используете динамические типы.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel как предопределенные классы объектов передачи данных

**Преимущества.** Предопределенные статические классы ViewModel (например, "контракты") на основе явных классов объектов передачи данных лучше подходят для общедоступных API-интерфейсов, а также для долгосрочных микрослужб, даже если они используются только в том же самом приложении.

Если вы хотите указать типы ответов для Swagger, необходимо использовать явные классы объектов передачи данных в качестве типа возвращаемого значения. Таким образом, с помощью предопределенных классов объектов передачи данных вы сможете получить больше сведений из Swagger. Так вы сможете улучшить документацию по API и совместимость при использовании API.

**Недостатки.** Как уже упоминалось, при обновлении кода будет сложнее обновить классы объектов передачи данных.

*Совет, основанный на нашем опыте.* В запросах, реализованных микрослужбой заказов в контейнерах eShopOnContainer, мы начали разработку, используя динамические модели ViewModel, так как это удобно на ранних этапах разработки. Но после стабилизации разработки мы выполнили рефакторинг API и использовали статические или предопределенные объекты передачи данных для ViewModel, так как микрослужбам удобнее знать явные типы объектов передачи данных и использовать их как "контракты".

В следующем примере показано, как запрос возвращает данные с помощью явного класса объекта передачи данных ViewModel: класса OrderSummary.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a>Описания типов ответов веб-API

Разработчиков, использующих веб-интерфейсов API и микрослужбы, в первую очередь волнуют возвращаемые данные, а именно: типы ответов и коды ошибок (если они не стандартны). Типы ответов обрабатываются в XML-комментариях и заметках к данным.

Без правильной документации в пользовательском интерфейсе Swagger потребителю не хватает знаний о том, какой тип значений возвращается или что могут вернуть HTTP-коды. Проблему можно решить, если добавить <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, чтобы Swashbuckle создал больше информации о модели возврата и возвращенных значениях API, как в примере кода:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

Однако атрибут `ProducesResponseType` не может использовать динамический тип. Он требует явный тип, как объект передачи данных ViewModel `OrderSummary`, показанный в следующем примере:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Это еще одна причина, по которой явные типы возвращаемого значения лучше динамических в долгосрочной перспективе. При использовании атрибута `ProducesResponseType` вы также можете указать ожидаемый результат в отношении возможных ошибок и кодов HTTP, например 200, 400 и т. д.

На следующем рисунке показано, как пользовательский интерфейс Swagger отображает сведения ResponseType.

![Снимок экрана: страница пользовательского интерфейса Swagger для Ordering API.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Рис. 7-5**. Пользовательский интерфейс Swagger, отображающий типы ответов и возможные коды состояния HTTP в веб-API

На рисунке выше показан пример значений на базе типов ViewModel и коды состояния HTTP, которые могут возвращаться.

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman (Джули Лерман). Точки данных — Dapper, Entity Framework и гибридные приложения (статья в журнале MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **Страницы справки по веб-API ASP.NET Core с использованием Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Назад](eshoponcontainers-cqrs-ddd-microservice.md)
>[Вперед](ddd-oriented-microservice.md)
