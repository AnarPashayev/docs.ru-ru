---
title: Практическое руководство. Доступ к членам объекта
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410546"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="44b0e-102">Практическое руководство. Доступ к членам объекта (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44b0e-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="44b0e-103">При наличии переменной объекта, ссылающейся на объект, часто требуется работать с элементами этого объекта, такими как его методы, свойства, поля и события.</span><span class="sxs-lookup"><span data-stu-id="44b0e-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="44b0e-104">Например, после создания нового <xref:System.Windows.Forms.Form> объекта может потребоваться задать его <xref:System.Windows.Forms.Control.Text%2A> свойство или вызвать его <xref:System.Windows.Forms.Control.Focus%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="44b0e-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="44b0e-105">Доступ к членам</span><span class="sxs-lookup"><span data-stu-id="44b0e-105">Accessing Members</span></span>

<span data-ttu-id="44b0e-106">Доступ к членам объекта осуществляется через переменную, ссылающуюся на него.</span><span class="sxs-lookup"><span data-stu-id="44b0e-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="44b0e-107">Получение доступа к членам объекта</span><span class="sxs-lookup"><span data-stu-id="44b0e-107">To access members of an object</span></span>

- <span data-ttu-id="44b0e-108">Используйте оператор доступа к членам ( `.` ) между именем объектной переменной и именем члена.</span><span class="sxs-lookup"><span data-stu-id="44b0e-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="44b0e-109">Если член является [общим](../../../language-reference/modifiers/shared.md), для доступа к нему не требуется переменная.</span><span class="sxs-lookup"><span data-stu-id="44b0e-109">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="44b0e-110">Доступ к членам объекта известного типа</span><span class="sxs-lookup"><span data-stu-id="44b0e-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="44b0e-111">Если тип объекта известно во время компиляции, можно использовать *раннее связывание* для переменной, ссылающейся на нее.</span><span class="sxs-lookup"><span data-stu-id="44b0e-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="44b0e-112">Доступ к членам объекта, тип которых вы узнаете во время компиляции</span><span class="sxs-lookup"><span data-stu-id="44b0e-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="44b0e-113">Объявите переменную объекта для типа объекта, который необходимо назначить переменной.</span><span class="sxs-lookup"><span data-stu-id="44b0e-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="44b0e-114">С помощью `Option Strict On` можно назначать только <xref:System.Windows.Forms.Form> объекты (или объекты типа, производного от <xref:System.Windows.Forms.Form> ) `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="44b0e-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="44b0e-115">Если вы определили класс или структуру с расширяющимся `CType` преобразованием в <xref:System.Windows.Forms.Form> , можно также присвоить этому классу или структуре значение `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="44b0e-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="44b0e-116">Используйте оператор доступа к членам ( `.` ) между именем объектной переменной и именем члена.</span><span class="sxs-lookup"><span data-stu-id="44b0e-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="44b0e-117">Можно получить доступ ко всем методам и свойствам, относящимся к <xref:System.Windows.Forms.Form> классу, независимо от значения `Option Strict` параметра.</span><span class="sxs-lookup"><span data-stu-id="44b0e-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="44b0e-118">Доступ к членам объекта неизвестного типа</span><span class="sxs-lookup"><span data-stu-id="44b0e-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="44b0e-119">Если тип объекта не знается во время компиляции, необходимо использовать *позднее связывание* для любой переменной, ссылающейся на нее.</span><span class="sxs-lookup"><span data-stu-id="44b0e-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="44b0e-120">Доступ к членам объекта, тип которых не знается во время компиляции</span><span class="sxs-lookup"><span data-stu-id="44b0e-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="44b0e-121">Объявите переменную объекта для [типа данных Object](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="44b0e-121">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="44b0e-122">(Объявление переменной как совпадает `Object` с ее объявлением как <xref:System.Object?displayProperty=nameWithType> .)</span><span class="sxs-lookup"><span data-stu-id="44b0e-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="44b0e-123">С помощью `Option Strict On` можно получить доступ только к тем элементам, которые определены в <xref:System.Object> классе.</span><span class="sxs-lookup"><span data-stu-id="44b0e-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="44b0e-124">Используйте оператор доступа к членам ( `.` ) между именем объектной переменной и именем члена.</span><span class="sxs-lookup"><span data-stu-id="44b0e-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="44b0e-125">Чтобы иметь возможность доступа к членам любого объекта, назначаемого переменной объекта, необходимо задать `Option Strict Off` .</span><span class="sxs-lookup"><span data-stu-id="44b0e-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="44b0e-126">При этом компилятор не может гарантировать, что данный элемент предоставляется объектом, назначаемым переменной.</span><span class="sxs-lookup"><span data-stu-id="44b0e-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="44b0e-127">Если объект не предоставляет член, к которому вы пытаетесь получить доступ, <xref:System.MemberAccessException> возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="44b0e-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="44b0e-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="44b0e-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="44b0e-129">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="44b0e-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="44b0e-130">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="44b0e-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="44b0e-131">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="44b0e-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="44b0e-132">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="44b0e-132">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
