---
title: Модульное тестирование F# в .NET Core с помощью dotnet test и xUnit
description: Сведения о концепциях модульного тестирования для F# в .NET Core в рамках пошаговой процедуры по созданию примера решения с помощью команды dotnet-test и xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 3a9744bfebd93c5004011819b8c6e739e84b97d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626489"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Модульное тестирование библиотек F# в .NET Core с использованием dotnet-test и xUnit

Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования. Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) перед началом работы. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Создание исходного проекта

Откройте окно оболочки. Создайте каталог с именем *unit-testing-with-fsharp* для хранения решения.
В этом каталоге выполните команду выполните команду [`dotnet new sln`](../tools/dotnet-new.md), чтобы создать решение. Это упрощает управление библиотекой классов и проектом модульного теста.
В каталоге решения создайте каталог *MathService*. Актуальная структура каталогов и файлов приведена ниже:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Чтобы создать исходный проект, перейдите в каталог *MathService* и выполните команду [`dotnet new classlib -lang F#`](../tools/dotnet-new.md).  Создайте реализацию службы вычислений со сбоем:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Вернитесь в каталог *unit-testing-with-fsharp*. Чтобы добавить проект библиотеки классов в решение, выполните команду [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md).

## <a name="creating-the-test-project"></a>Создание тестового проекта

Затем создайте каталог *MathService.Tests*. Ниже представлена структура каталогов:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Перейдите в каталог *MathService.Tests* и создайте проект с помощью [`dotnet new xunit -lang F#`](../tools/dotnet-new.md). Эта команда создает тестовый проект, использующий xUnit в качестве библиотеки тестов. Созданный шаблон настраивает средство выполнения тестов в файле *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда В предыдущем шаге `dotnet new` добавила пакет xUnit и средство запуска xUnit. Теперь добавьте в проект библиотеку классов `MathService` в качестве еще одной зависимости. Используйте команду [`dotnet add reference`](../tools/dotnet-add-reference.md):

```
dotnet add reference ../MathService/MathService.fsproj
```

Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) на сайте GitHub.

Ниже показан окончательный макет решения:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

Выполните команду [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) в каталоге *unit-testing-with-fsharp*. 

## <a name="creating-the-first-test"></a>Создание первого теста

Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс. Откройте файл *Tests.fs* и добавьте следующий код:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

Атрибут `[<Fact>]` обозначает метод теста, который выполняется с помощью средства выполнения тестов. Из каталога *unit-testing-with-fsharp* выполните команду [`dotnet test`](../tools/dotnet-test.md) для создания тестов и библиотеки классов, а затем выполните тесты. Средство запуска тестов xUnit содержит точку входа в программу для выполнения тестов. `dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.

Эти два теста демонстрируют самые простые тесты, которые выполняются и завершаются сбоем. `My test` выполняется успешно, а `Fail every time` завершается сбоем. Сейчас создайте тест для метода `squaresOfOdds`. Метод `squaresOfOdds` возвращает последовательность квадратов всех нечетных целочисленных значений, которые являются частью входной последовательности. Вместо того чтобы писать все эти функции одновременно, можно постепенно создавать тесты, проверяющие функциональность. Если тест выполняется успешно, создается необходимая функция метода.

Самый простой тест — вызов `squaresOfOdds` со всеми четными числами, где результатом должна быть пустая последовательность целых чисел.  Вот этот тест:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Тест не будет пройден. Вы еще не создали реализацию. Чтобы тест был пройден, напишите простейший код в классе `MathService`, который работает:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

В каталоге *unit-testing-with-fsharp* снова выполните команду `dotnet test`. Команда `dotnet test` запускает сборку для проекта `MathService` и затем для проекта `MathService.Tests`. После сборки обоих проектов она запускает этот отдельный тест. Он выполняется.

## <a name="completing-the-requirements"></a>Выполнение требований

Теперь, когда тест проходит успешно, пора создать дополнительные тесты. Следующий простой пример работает с последовательностью, единственным нечетным числом которой является `1`. Число 1 использовать проще, потому что квадрат 1 равен 1. Вот этот тест:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Выполнение `dotnet test` запускает ваши тесты. В результатах видно, что новый тест завершается сбоем. Теперь необходимо обновить метод `squaresOfOdds`, чтобы обработать этот новый тест. Чтобы тест выполнялся успешно, необходимо отфильтровать все четные числа из последовательности. Чтобы сделать это, напишите небольшую функцию фильтра и используйте `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Нужно выполнить еще один шаг: определить квадрат каждого из нечетных чисел. Начнем с написания нового теста:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Чтобы вычислить квадрат каждого нечетного числа, можно исправить тест, пропустив фильтрованную последовательность через операцию сопоставления:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Вы создали небольшую библиотеку и набор модульных тестов для нее. Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса и получить возможность сосредоточиться на задачах приложения.
