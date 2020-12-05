---
title: Сведения о вызывающем объекте
description: Описывает использование атрибутов аргумента сведений вызывающей стороны для получения сведений о вызывающем объекте из метода.
ms.date: 11/04/2019
ms.openlocfilehash: 700cde26fbe4e6c48155f88bfc63af59af86cfe2
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739780"
---
# <a name="caller-information"></a>Сведения о вызывающем объекте

С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода. Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта. Эти сведения полезны для трассировки, отладки и создания средств диагностики.

Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам, каждый из которых имеет значение по умолчанию. В следующей таблице перечислены атрибуты сведений о вызывающем объекте, определенные в пространстве имен [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :

|attribute|Описание|Тип|
|---------|-----------|----|
|[каллерфилепас](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Полный путь исходного файла, содержащего вызывающий объект. Это путь к файлу во время компиляции.|`String`
|[каллерлиненумбер](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Номер строки в исходном файле, в которой вызывается метод.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Имя свойства или метода вызывающего объекта. См. раздел имена членов далее в этом разделе.|`String`|

## <a name="example"></a>Пример

В следующем примере показано, как с помощью этих атрибутов можно отслеживать вызывающий объект.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf $"Message: {message}")
        Trace.WriteLine(sprintf $"Member name: {memberName}")
        Trace.WriteLine(sprintf $"Source file path: {path}")
        Trace.WriteLine(sprintf $"Source line number: {line}")
```

## <a name="remarks"></a>Remarks

Атрибуты сведений о вызывающем объекте могут применяться только к необязательным параметрам. Атрибуты сведений о вызывающем объекте приводят к тому, что компилятор записывает правильное значение для каждого необязательного параметра, дополненного атрибутом сведений о вызывающем объекте.

Информационные значения вызывающего объекта передаются как литералы в IL во время компиляции. В отличие от результатов свойства [StackTrace](/dotnet/api/system.diagnostics.stacktrace) для исключений, на результаты не влияет маскировка.

Можно явно передать необязательные аргументы, чтобы управлять сведениями о вызывающем объекте или скрывать сведения о вызывающем объекте.

## <a name="member-names"></a>Имена членов

Можно использовать атрибут, [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) чтобы не указывать имя члена в качестве `String` аргумента вызываемого метода. Этот прием позволяет избежать проблемы, заключающейся в том, что операция рефакторинга и переименования не изменяет значений `String`. Это особенно полезно при выполнении следующих задач:

- Использование процедур трассировки и диагностики.
- Реализация интерфейса [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) при привязке данных. Этот интерфейс позволяет свойству объекта уведомлять связанный элемент управления об изменении свойства, чтобы элемент управления мог отображать обновленные сведения. Без [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) атрибута необходимо указать имя свойства в виде литерала.

На следующей диаграмме показаны имена элементов, возвращаемых при использовании атрибута CallerMemberName.

|Фрагмент кода, в пределах которого происходит вызов|Результат имени члена|
|-------------------|------------------|
|Метод, свойство или событие|Имя метода, свойства или события, из которого происходил вызов.|
|Конструктор|Строка ".ctor"|
|Статический конструктор|Строка ".cctor"|
|Деструктор|Строка "Finalize"|
|Определяемые пользователем операторы и преобразования|Созданное имя члена, например, "op_Addition".|
|Конструктора атрибута|Имя члена, к которому применяется атрибут. Если атрибут — любой элемент внутри члена (например, параметр, возвращаемое значение или параметр универсального типа), то результат — имя члена, который связан с этим элементом.|
|Нет содержащего члена (например, уровень сборки или атрибуты, примененные к типам)|Значение необязательного параметра по умолчанию.|

## <a name="see-also"></a>См. также

- [Атрибуты](attributes.md)
- [Именованные аргументы](parameters-and-arguments.md#named-arguments)
- [Необязательные параметры](parameters-and-arguments.md#optional-parameters)
