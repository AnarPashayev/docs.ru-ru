---
title: Директива x:Property
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432680"
---
# <a name="xproperty-directive"></a><span data-ttu-id="f6efa-102">Директива x:Property</span><span class="sxs-lookup"><span data-stu-id="f6efa-102">x:Property Directive</span></span>

<span data-ttu-id="f6efa-103">Объявляет свойство XAML в разметке.</span><span class="sxs-lookup"><span data-stu-id="f6efa-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="f6efa-104">Использование элемента объекта XAML</span><span class="sxs-lookup"><span data-stu-id="f6efa-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="f6efa-105">Значения XAML</span><span class="sxs-lookup"><span data-stu-id="f6efa-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="f6efa-106">Имя класса резервирования или разделяемого класса для рабочей среды XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="f6efa-107">Имя члена определяемого свойства.</span><span class="sxs-lookup"><span data-stu-id="f6efa-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="f6efa-108">Имя типа (или другая строковая форма, специфичная для платформы), указывающее тип этого свойства.</span><span class="sxs-lookup"><span data-stu-id="f6efa-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6efa-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="f6efa-109">Remarks</span></span>

<span data-ttu-id="f6efa-110">В реализации услуг .NET XAML .</span><span class="sxs-lookup"><span data-stu-id="f6efa-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="f6efa-111">`x:Property` не имеет прямое резервирование типа, но поддерживается классом <xref:System.Windows.Markup.PropertyDefinition>.</span><span class="sxs-lookup"><span data-stu-id="f6efa-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="f6efa-112">В потоке узлов XAML элемент `x:Property` представляется как член с именем `Property` из пространства имен XAML языка XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="f6efa-113">Член `Property` хранит атрибуты, объявленные в разметке.</span><span class="sxs-lookup"><span data-stu-id="f6efa-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="f6efa-114">Значение `Name` и `Type` не присваиваются на уровне услуг .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="f6efa-115">Они хранятся в исходном потоке узлов XAML как строковые значения для последующей интерпретации в соответствии с правилами, которые могут быть наложены конкретными платформами.</span><span class="sxs-lookup"><span data-stu-id="f6efa-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="f6efa-116">Эти значения могут выравниваться по значениям имени XAML и типа XAML или могут быть допустимы только в системе с резервированием типов, в зависимости от реализации.</span><span class="sxs-lookup"><span data-stu-id="f6efa-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="f6efa-117">Для поддержки практического использования `x:Members` как средства указания определений членов в разметке эти члены должны быть связаны с классом, который может быть изменен.</span><span class="sxs-lookup"><span data-stu-id="f6efa-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="f6efa-118">Предполагаемая модель состоит в том, что `x:Members` существует в качестве члена типа, указывающего `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="f6efa-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="f6efa-119">Однако механизм связывания типов и членов или для создания динамических определений членов не поддерживается на уровне .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="f6efa-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="f6efa-120">Это отводится отдельным платформам, имеющим модели приложений, поддерживающие определения членов из XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="f6efa-121">Как правило, для поддержки этой функции требуются действия MSBUILD при построении, которые компилируют разметку XAML и либо интегрируют его с выделенным кодом, либо создают чистые сборки из XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="f6efa-122">x:Property для Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f6efa-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="f6efa-123">Для Windows Workflow Foundation `x:Property` определяет члены пользовательского действия, составленного полностью в XAML, или заданные XAML динамические члены для конструктора действий с выделенным кодом.</span><span class="sxs-lookup"><span data-stu-id="f6efa-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="f6efa-124">`x:Class` также должен быть указан в корневом элементе рабочей среды XAML.</span><span class="sxs-lookup"><span data-stu-id="f6efa-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="f6efa-125">Это не является требованием на уровне .NET XAML Services, но становится требованием, когда производство XAML загружается действиями msBUILD, которые поддерживают пользовательские действия и Фонд обработки данных Windows XAML в целом.</span><span class="sxs-lookup"><span data-stu-id="f6efa-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="f6efa-126">Фонд Рабочего процесса Windows не использует чистое имя типа `x:Property` `Type` XAML в качестве предполагаемого значения для атрибута, а вместо этого использует конвенцию, которая не документирована здесь.</span><span class="sxs-lookup"><span data-stu-id="f6efa-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="f6efa-127">Для получения дополнительной информации [см.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6efa-127">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
