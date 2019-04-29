---
title: Сведения о вызывающем объекте
description: Описывает, как использовать информационные атрибуты аргумента вызывающего объекта, чтобы получить сведения о вызывающем объекте из метода.
ms.date: 04/25/2017
ms.openlocfilehash: 13092df453b684d3ed4a93c842ea49c066157cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703170"
---
# <a name="caller-information"></a>Сведения о вызывающем объекте

С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода. Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта. Эти сведения полезны для трассировки, отладки и создания средств диагностики.

Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам, каждый из которых имеет значение по умолчанию. В следующей таблице перечислены информационные атрибуты вызывающего объекта, которые определены в [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) пространство имен:

|Атрибут|Описание|Тип|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Полный путь исходного файла, содержащего вызывающий объект. Это путь к файлу во время компиляции.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Номер строки в исходном файле, в которой вызывается метод.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Имя свойства или метода вызывающего объекта. См. в разделе "имена элементов" Далее в этом разделе.|`String`|

## <a name="example"></a>Пример

Следующий пример показывает, как эти атрибуты можно использовать для трассировки вызывающий объект.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Примечания

Информационные атрибуты вызывающего объекта может применяться только к необязательным параметрам. Информационные атрибуты вызывающего объекта при компиляции для записи правильное значение для каждого необязательного параметра, атрибут информация вызывающего объекта.

Информационные значения вызывающего объекта передаются как литералы в IL во время компиляции. В отличие от результатов [StackTrace](/dotnet/api/system.diagnostics.stacktrace) свойство для исключений, результаты не затрагиваются обфускацией.

Можно явно передать необязательные аргументы, чтобы управлять сведениями о вызывающем объекте или скрывать сведения о вызывающем объекте.

## <a name="member-names"></a>Имена членов

Можно использовать [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) атрибут, чтобы не указывать имя члена в виде `String` аргумента в вызываемый метод. При использовании этого метода, позволяет избежать проблемы рефакторинга и переименования неизменная `String` значения. Это особенно полезно при выполнении следующих задач:

* Использование процедур трассировки и диагностики.
* Реализация [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) интерфейс во время привязки данных. Этот интерфейс позволяет свойству объекта уведомлять связанный элемент управления об изменении свойства, чтобы элемент управления мог отображать обновленные сведения. Без [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) атрибут, необходимо указать имя свойства как литерал.

На следующем рисунке показана член имена, которые возвращаются при использовании атрибут CallerMemberName.

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
