---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3102ae8d8c28be43883eeaff6c4f829b355384a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701428"
---
# <a name="servicehost"></a><span data-ttu-id="25ea4-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="25ea4-101">\@ServiceHost</span></span>
<span data-ttu-id="25ea4-102">Связывает фабрику, используемую для создания узла службы, с размещаемой службой и другими элементами программирования, необходимыми для доступа или компиляции кода размещения, представленного в SVC-файле.</span><span class="sxs-lookup"><span data-stu-id="25ea4-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ea4-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="25ea4-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="25ea4-104">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="25ea4-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="25ea4-105">Служба</span><span class="sxs-lookup"><span data-stu-id="25ea4-105">Service</span></span>  
 <span data-ttu-id="25ea4-106">Имя типа CLR размещенной службы.</span><span class="sxs-lookup"><span data-stu-id="25ea4-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="25ea4-107">Это должно быть полное имя типа, который реализует один или несколько контактов службы.</span><span class="sxs-lookup"><span data-stu-id="25ea4-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="25ea4-108">Factory</span><span class="sxs-lookup"><span data-stu-id="25ea4-108">Factory</span></span>  
 <span data-ttu-id="25ea4-109">Имя типа CLR фабрики узла службы, используемой для создания узла службы.</span><span class="sxs-lookup"><span data-stu-id="25ea4-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="25ea4-110">Этот атрибут является необязательным.</span><span class="sxs-lookup"><span data-stu-id="25ea4-110">This attribute is optional.</span></span> <span data-ttu-id="25ea4-111">Если данный атрибут не задан, по умолчанию используется значение <xref:System.ServiceModel.Activation.ServiceHostFactory>, которое возвращает экземпляр <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="25ea4-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="25ea4-112">Отладка</span><span class="sxs-lookup"><span data-stu-id="25ea4-112">Debug</span></span>  
 <span data-ttu-id="25ea4-113">Указывает, должны ли службы Windows Communication Foundation (WCF) компилироваться с отладочными символами.</span><span class="sxs-lookup"><span data-stu-id="25ea4-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="25ea4-114">`true` Если службы WCF должны компилироваться с отладочными символами. в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="25ea4-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="25ea4-115">Язык</span><span class="sxs-lookup"><span data-stu-id="25ea4-115">Language</span></span>  
 <span data-ttu-id="25ea4-116">Задает язык, используемый при компиляции всего встроенного кода в файле (SVC).</span><span class="sxs-lookup"><span data-stu-id="25ea4-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="25ea4-117">Значения данного атрибута могут представлять любой язык, поддерживаемый .NET, включая C#, VB и JS, что соответствует языкам C#, Visual Basic .NET и JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="25ea4-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="25ea4-118">Этот атрибут является необязательным.</span><span class="sxs-lookup"><span data-stu-id="25ea4-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="25ea4-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="25ea4-119">CodeBehind</span></span>  
 <span data-ttu-id="25ea4-120">Определяет файл исходного кода, реализующего веб-службу XML, если реализующий ее класс находится в другом файле и не был скомпилирован в сборку и помещен в каталог «\Bin».</span><span class="sxs-lookup"><span data-stu-id="25ea4-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25ea4-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="25ea4-121">Remarks</span></span>  
 <span data-ttu-id="25ea4-122"><xref:System.ServiceModel.ServiceHost> Используется для размещения службы — это точка расширения в модели программирования Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="25ea4-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="25ea4-123">Для создания узла службы <xref:System.ServiceModel.ServiceHost> используется шаблон фабрики, поскольку он, возможно, имеет полиморфный тип, экземпляр которого среда размещения не должна создавать явно.</span><span class="sxs-lookup"><span data-stu-id="25ea4-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="25ea4-124">В реализации по умолчанию используется фабрика <xref:System.ServiceModel.Activation.ServiceHostFactory> для создания экземпляра узла службы <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="25ea4-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="25ea4-125">Но можно предоставить собственную фабрику (один, которая возвращает производный узел), указав имя типа CLR реализации фабрики в [ \@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) директива.</span><span class="sxs-lookup"><span data-stu-id="25ea4-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="25ea4-126">Чтобы использовать собственный настраиваемой фабрики узла службы вместо фабрики по умолчанию, просто предоставить имя типа в [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) директива следующим образом:</span><span class="sxs-lookup"><span data-stu-id="25ea4-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="25ea4-127">Создавайте реализацию фабрики в наиболее простом виде.</span><span class="sxs-lookup"><span data-stu-id="25ea4-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="25ea4-128">Если имеется значительный объем пользовательской логики, то можно увеличить возможность повторного использования кода, если разместить эту логику на узле, а не в фабрике.</span><span class="sxs-lookup"><span data-stu-id="25ea4-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="25ea4-129">Например, чтобы включить конечную точку с поддержкой AJAX для `MyService`, укажите <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> значения `Factory` атрибута, а не значение по умолчанию <xref:System.ServiceModel.Activation.ServiceHostFactory>в [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) директив как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="25ea4-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25ea4-130">Пример</span><span class="sxs-lookup"><span data-stu-id="25ea4-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25ea4-131">См. также</span><span class="sxs-lookup"><span data-stu-id="25ea4-131">See also</span></span>

- [<span data-ttu-id="25ea4-132">Пользовательский узел службы</span><span class="sxs-lookup"><span data-stu-id="25ea4-132">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
