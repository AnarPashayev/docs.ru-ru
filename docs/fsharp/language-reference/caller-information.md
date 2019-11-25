---
title: Сведения о вызывающем объекте
description: Описывает использование атрибутов аргумента сведений вызывающей стороны для получения сведений о вызывающем объекте из метода.
ms.date: 11/04/2019
ms.openlocfilehash: d995b37149277b7c7d1b6217ee484d3c90a7f8b3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976800"
---
# <a name="caller-information"></a><span data-ttu-id="d4563-103">Сведения о вызывающем объекте</span><span class="sxs-lookup"><span data-stu-id="d4563-103">Caller information</span></span>

<span data-ttu-id="d4563-104">С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода.</span><span class="sxs-lookup"><span data-stu-id="d4563-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="d4563-105">Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="d4563-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="d4563-106">Эти сведения полезны для трассировки, отладки и создания средств диагностики.</span><span class="sxs-lookup"><span data-stu-id="d4563-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="d4563-107">Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам, каждый из которых имеет значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d4563-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="d4563-108">В следующей таблице перечислены атрибуты сведений о вызывающем объекте, определенные в пространстве имен [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :</span><span class="sxs-lookup"><span data-stu-id="d4563-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="d4563-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d4563-109">Attribute</span></span>|<span data-ttu-id="d4563-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d4563-110">Description</span></span>|<span data-ttu-id="d4563-111">Type</span><span class="sxs-lookup"><span data-stu-id="d4563-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="d4563-112">каллерфилепас</span><span class="sxs-lookup"><span data-stu-id="d4563-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="d4563-113">Полный путь исходного файла, содержащего вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="d4563-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="d4563-114">Это путь к файлу во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="d4563-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="d4563-115">каллерлиненумбер</span><span class="sxs-lookup"><span data-stu-id="d4563-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="d4563-116">Номер строки в исходном файле, в которой вызывается метод.</span><span class="sxs-lookup"><span data-stu-id="d4563-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="d4563-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="d4563-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="d4563-118">Имя свойства или метода вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="d4563-118">Method or property name of the caller.</span></span> <span data-ttu-id="d4563-119">См. раздел имена членов далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d4563-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="d4563-120">Пример</span><span class="sxs-lookup"><span data-stu-id="d4563-120">Example</span></span>

<span data-ttu-id="d4563-121">В следующем примере показано, как с помощью этих атрибутов можно отслеживать вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="d4563-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a><span data-ttu-id="d4563-122">Заметки</span><span class="sxs-lookup"><span data-stu-id="d4563-122">Remarks</span></span>

<span data-ttu-id="d4563-123">Атрибуты сведений о вызывающем объекте могут применяться только к необязательным параметрам.</span><span class="sxs-lookup"><span data-stu-id="d4563-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="d4563-124">Атрибуты сведений о вызывающем объекте приводят к тому, что компилятор записывает правильное значение для каждого необязательного параметра, дополненного атрибутом сведений о вызывающем объекте.</span><span class="sxs-lookup"><span data-stu-id="d4563-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="d4563-125">Информационные значения вызывающего объекта передаются как литералы в IL во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="d4563-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="d4563-126">В отличие от результатов свойства [StackTrace](/dotnet/api/system.diagnostics.stacktrace) для исключений, на результаты не влияет маскировка.</span><span class="sxs-lookup"><span data-stu-id="d4563-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="d4563-127">Можно явно передать необязательные аргументы, чтобы управлять сведениями о вызывающем объекте или скрывать сведения о вызывающем объекте.</span><span class="sxs-lookup"><span data-stu-id="d4563-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="d4563-128">Имена членов</span><span class="sxs-lookup"><span data-stu-id="d4563-128">Member names</span></span>

<span data-ttu-id="d4563-129">Можно использовать атрибут [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) , чтобы не указывать имя члена в качестве аргумента `String` вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="d4563-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="d4563-130">С помощью этого метода можно избежать проблем, при которых Рефакторинг переименования не изменяет значения `String`.</span><span class="sxs-lookup"><span data-stu-id="d4563-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="d4563-131">Это особенно полезно при выполнении следующих задач:</span><span class="sxs-lookup"><span data-stu-id="d4563-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="d4563-132">Использование процедур трассировки и диагностики.</span><span class="sxs-lookup"><span data-stu-id="d4563-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="d4563-133">Реализация интерфейса [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) при привязке данных.</span><span class="sxs-lookup"><span data-stu-id="d4563-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="d4563-134">Этот интерфейс позволяет свойству объекта уведомлять связанный элемент управления об изменении свойства, чтобы элемент управления мог отображать обновленные сведения.</span><span class="sxs-lookup"><span data-stu-id="d4563-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="d4563-135">Без атрибута [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) необходимо указать имя свойства в виде литерала.</span><span class="sxs-lookup"><span data-stu-id="d4563-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="d4563-136">На следующей диаграмме показаны имена элементов, возвращаемых при использовании атрибута CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="d4563-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="d4563-137">Фрагмент кода, в пределах которого происходит вызов</span><span class="sxs-lookup"><span data-stu-id="d4563-137">Calls occurs within</span></span>|<span data-ttu-id="d4563-138">Результат имени члена</span><span class="sxs-lookup"><span data-stu-id="d4563-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="d4563-139">Метод, свойство или событие</span><span class="sxs-lookup"><span data-stu-id="d4563-139">Method, property, or event</span></span>|<span data-ttu-id="d4563-140">Имя метода, свойства или события, из которого происходил вызов.</span><span class="sxs-lookup"><span data-stu-id="d4563-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="d4563-141">Конструктор</span><span class="sxs-lookup"><span data-stu-id="d4563-141">Constructor</span></span>|<span data-ttu-id="d4563-142">Строка ".ctor"</span><span class="sxs-lookup"><span data-stu-id="d4563-142">The string ".ctor"</span></span>|
|<span data-ttu-id="d4563-143">Статический конструктор</span><span class="sxs-lookup"><span data-stu-id="d4563-143">Static constructor</span></span>|<span data-ttu-id="d4563-144">Строка ".cctor"</span><span class="sxs-lookup"><span data-stu-id="d4563-144">The string ".cctor"</span></span>|
|<span data-ttu-id="d4563-145">Деструктор</span><span class="sxs-lookup"><span data-stu-id="d4563-145">Destructor</span></span>|<span data-ttu-id="d4563-146">Строка "Finalize"</span><span class="sxs-lookup"><span data-stu-id="d4563-146">The string "Finalize"</span></span>|
|<span data-ttu-id="d4563-147">Определяемые пользователем операторы и преобразования</span><span class="sxs-lookup"><span data-stu-id="d4563-147">User-defined operators or conversions</span></span>|<span data-ttu-id="d4563-148">Созданное имя члена, например, "op_Addition".</span><span class="sxs-lookup"><span data-stu-id="d4563-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="d4563-149">Конструктора атрибута</span><span class="sxs-lookup"><span data-stu-id="d4563-149">Attribute constructor</span></span>|<span data-ttu-id="d4563-150">Имя члена, к которому применяется атрибут.</span><span class="sxs-lookup"><span data-stu-id="d4563-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="d4563-151">Если атрибут — любой элемент внутри члена (например, параметр, возвращаемое значение или параметр универсального типа), то результат — имя члена, который связан с этим элементом.</span><span class="sxs-lookup"><span data-stu-id="d4563-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="d4563-152">Нет содержащего члена (например, уровень сборки или атрибуты, примененные к типам)</span><span class="sxs-lookup"><span data-stu-id="d4563-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="d4563-153">Значение необязательного параметра по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d4563-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d4563-154">См. также</span><span class="sxs-lookup"><span data-stu-id="d4563-154">See also</span></span>

- [<span data-ttu-id="d4563-155">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d4563-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="d4563-156">Именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="d4563-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="d4563-157">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="d4563-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
