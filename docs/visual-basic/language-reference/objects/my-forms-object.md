---
title: Объект My.Forms
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372444"
---
# <a name="myforms-object"></a><span data-ttu-id="00278-102">Объект My.Forms</span><span class="sxs-lookup"><span data-stu-id="00278-102">My.Forms Object</span></span>

<span data-ttu-id="00278-103">Предоставляет свойства для доступа к экземпляру каждой формы Windows Form, объявленной в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="00278-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="00278-104">Комментарии</span><span class="sxs-lookup"><span data-stu-id="00278-104">Remarks</span></span>

<span data-ttu-id="00278-105">`My.Forms`Объект предоставляет экземпляр каждой формы в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="00278-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="00278-106">Имя свойства совпадает с именем формы, к которой обращается свойство.</span><span class="sxs-lookup"><span data-stu-id="00278-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="00278-107">Доступ к формам, предоставляемым объектом, можно получить `My.Forms` с помощью имени формы без уточнения.</span><span class="sxs-lookup"><span data-stu-id="00278-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="00278-108">Так как имя свойства совпадает с именем типа формы, это позволяет получить доступ к форме, как если бы она имела экземпляр по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="00278-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="00278-109">Например, предложение `My.Forms.Form1.Show` эквивалентно предложению `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="00278-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="00278-110">`My.Forms`Объект предоставляет только формы, связанные с текущим проектом.</span><span class="sxs-lookup"><span data-stu-id="00278-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="00278-111">Он не предоставляет доступ к формам, объявленным в упоминаемых библиотеках DLL.</span><span class="sxs-lookup"><span data-stu-id="00278-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="00278-112">Для доступа к форме, предоставляемой библиотекой DLL, необходимо использовать полное имя формы, записанное как *dllname*. *Формнаме*.</span><span class="sxs-lookup"><span data-stu-id="00278-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="00278-113">Свойство можно использовать <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> для получения коллекции всех открытых форм приложения.</span><span class="sxs-lookup"><span data-stu-id="00278-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="00278-114">Объект и его свойства доступны только для приложений Windows.</span><span class="sxs-lookup"><span data-stu-id="00278-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="00278-115">Свойства</span><span class="sxs-lookup"><span data-stu-id="00278-115">Properties</span></span>

<span data-ttu-id="00278-116">Каждое свойство `My.Forms` объекта предоставляет доступ к экземпляру формы в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="00278-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="00278-117">Имя свойства совпадает с именем формы, к которой обращается свойство, а тип свойства совпадает с типом формы.</span><span class="sxs-lookup"><span data-stu-id="00278-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="00278-118">При конфликте имен имя свойства для доступа к форме — *RootNamespace*_*Namespace* \_ *формнаме*.</span><span class="sxs-lookup"><span data-stu-id="00278-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="00278-119">Например, рассмотрим две формы с именем, `Form1.` Если одна из этих форм находится в корневом пространстве имен `WindowsApplication1` и в пространстве имен `Namespace1` , поэтому доступ к этой форме осуществляется через `My.Forms.WindowsApplication1_Namespace1_Form1` .</span><span class="sxs-lookup"><span data-stu-id="00278-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="00278-120">`My.Forms`Объект предоставляет доступ к экземпляру главной формы приложения, созданному при запуске.</span><span class="sxs-lookup"><span data-stu-id="00278-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="00278-121">Для всех других форм `My.Forms` объект создает новый экземпляр формы при обращении к нему и сохраняет его.</span><span class="sxs-lookup"><span data-stu-id="00278-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="00278-122">Последующие попытки доступа к этому свойству возвращают этот экземпляр формы.</span><span class="sxs-lookup"><span data-stu-id="00278-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="00278-123">Форму можно удалить, назначив `Nothing` свойству для этой формы.</span><span class="sxs-lookup"><span data-stu-id="00278-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="00278-124">Средство задания свойств вызывает <xref:System.Windows.Forms.Form.Close%2A> метод формы, а затем присваивает `Nothing` хранимому значению.</span><span class="sxs-lookup"><span data-stu-id="00278-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="00278-125">Если присвоить значение, отличное от `Nothing` свойства, метод задания выдаст <xref:System.ArgumentException> исключение.</span><span class="sxs-lookup"><span data-stu-id="00278-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="00278-126">Можно проверить `My.Forms` , сохраняет ли свойство объекта экземпляр формы с помощью `Is` `IsNot` оператора или.</span><span class="sxs-lookup"><span data-stu-id="00278-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="00278-127">С помощью этих операторов можно проверить, имеет ли свойство значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="00278-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="00278-128">Как правило, `Is` `IsNot` оператор или должен считывать значение свойства для выполнения сравнения.</span><span class="sxs-lookup"><span data-stu-id="00278-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="00278-129">Однако если текущее свойство хранится `Nothing` , свойство создает новый экземпляр формы, а затем возвращает этот экземпляр.</span><span class="sxs-lookup"><span data-stu-id="00278-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="00278-130">Однако компилятор Visual Basic обрабатывает свойства объекта по- `My.Forms` разному и позволяет `Is` `IsNot` оператору или проверить состояние свойства без изменения его значения.</span><span class="sxs-lookup"><span data-stu-id="00278-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="00278-131">Пример</span><span class="sxs-lookup"><span data-stu-id="00278-131">Example</span></span>

<span data-ttu-id="00278-132">В этом примере изменяется заголовок формы по умолчанию `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="00278-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="00278-133">Чтобы этот пример работал, проект должен иметь форму с именем `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="00278-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="00278-134">Этот код будет работать только в проекте приложения Windows.</span><span class="sxs-lookup"><span data-stu-id="00278-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="00278-135">Требования</span><span class="sxs-lookup"><span data-stu-id="00278-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="00278-136">Доступность по типу проекта</span><span class="sxs-lookup"><span data-stu-id="00278-136">Availability by Project Type</span></span>

|<span data-ttu-id="00278-137">Тип проекта</span><span class="sxs-lookup"><span data-stu-id="00278-137">Project type</span></span>|<span data-ttu-id="00278-138">Доступно</span><span class="sxs-lookup"><span data-stu-id="00278-138">Available</span></span>|
|---|---|
|<span data-ttu-id="00278-139">Приложение Windows</span><span class="sxs-lookup"><span data-stu-id="00278-139">Windows Application</span></span>|<span data-ttu-id="00278-140">**Да**</span><span class="sxs-lookup"><span data-stu-id="00278-140">**Yes**</span></span>|
|<span data-ttu-id="00278-141">Библиотека классов</span><span class="sxs-lookup"><span data-stu-id="00278-141">Class Library</span></span>|<span data-ttu-id="00278-142">нет</span><span class="sxs-lookup"><span data-stu-id="00278-142">No</span></span>|
|<span data-ttu-id="00278-143">Консольное приложение</span><span class="sxs-lookup"><span data-stu-id="00278-143">Console Application</span></span>|<span data-ttu-id="00278-144">нет</span><span class="sxs-lookup"><span data-stu-id="00278-144">No</span></span>|
|<span data-ttu-id="00278-145">Библиотека элементов управления Windows</span><span class="sxs-lookup"><span data-stu-id="00278-145">Windows Control Library</span></span>|<span data-ttu-id="00278-146">нет</span><span class="sxs-lookup"><span data-stu-id="00278-146">No</span></span>|
|<span data-ttu-id="00278-147">Библиотека веб-элементов управления</span><span class="sxs-lookup"><span data-stu-id="00278-147">Web Control Library</span></span>|<span data-ttu-id="00278-148">нет</span><span class="sxs-lookup"><span data-stu-id="00278-148">No</span></span>|
|<span data-ttu-id="00278-149">Служба Windows</span><span class="sxs-lookup"><span data-stu-id="00278-149">Windows Service</span></span>|<span data-ttu-id="00278-150">нет</span><span class="sxs-lookup"><span data-stu-id="00278-150">No</span></span>|
|<span data-ttu-id="00278-151">Веб-сайт</span><span class="sxs-lookup"><span data-stu-id="00278-151">Web Site</span></span>|<span data-ttu-id="00278-152">нет</span><span class="sxs-lookup"><span data-stu-id="00278-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="00278-153">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="00278-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="00278-154">Объекты</span><span class="sxs-lookup"><span data-stu-id="00278-154">Objects</span></span>](index.md)
- [<span data-ttu-id="00278-155">Оператор is</span><span class="sxs-lookup"><span data-stu-id="00278-155">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="00278-156">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="00278-156">IsNot Operator</span></span>](../operators/isnot-operator.md)
- [<span data-ttu-id="00278-157">Доступ к формам приложения</span><span class="sxs-lookup"><span data-stu-id="00278-157">Accessing Application Forms</span></span>](../../developing-apps/programming/accessing-application-forms.md)
