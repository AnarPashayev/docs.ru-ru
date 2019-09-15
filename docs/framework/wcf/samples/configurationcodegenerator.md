---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990067"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="f835d-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="f835d-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="f835d-103">ConfigurationCodeGenerator - это средство, позволяющее предоставлять системе конфигурации реализации пользовательских каналов.</span><span class="sxs-lookup"><span data-stu-id="f835d-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="f835d-104">Это позволяет пользователям пользовательских каналов настраивать каналы с помощью файла конфигурации, как это происходит в случае с системными привязками, например `NetTcpBinding`, или пользовательскими привязками с помощью элемента `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="f835d-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="f835d-105">При разработке пользовательского канала и его предоставлении в модели программирования с помощью нового элемента `BindingElement` или `Binding` необходимо создать набор классов, чтобы `BindingElement` или `Binding` можно было настраивать с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f835d-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="f835d-106">Средство ConfigurationCodeGenerator позволяет создать эти классы и сделать работу пользователей более удобной.</span><span class="sxs-lookup"><span data-stu-id="f835d-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="f835d-107">Построение средства</span><span class="sxs-lookup"><span data-stu-id="f835d-107">To build the tool</span></span>  
  
1. <span data-ttu-id="f835d-108">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f835d-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f835d-109">При построении решения создается один файл: Конфигуратионкодеженератор. exe.</span><span class="sxs-lookup"><span data-stu-id="f835d-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="f835d-110">Файл самплерун. cmd содержит образец командной строки, который показывает, как использовать это средство для создания классов для [транспорта. Пример](../../../../docs/framework/wcf/samples/transport-udp.md) протокола UDP.</span><span class="sxs-lookup"><span data-stu-id="f835d-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="f835d-111">Запуск средства</span><span class="sxs-lookup"><span data-stu-id="f835d-111">To run the tool</span></span>  
  
1. <span data-ttu-id="f835d-112">В командной строке введите следующую команду, если имеется пользовательский тип `BindingElement` и пользовательский тип `Binding`:</span><span class="sxs-lookup"><span data-stu-id="f835d-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="f835d-113">Либо введите следующую команду, если имеется только пользовательский тип `BindingElement`:</span><span class="sxs-lookup"><span data-stu-id="f835d-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="f835d-114">Либо введите следующую команду, если имеется только пользовательский тип `Binding`:</span><span class="sxs-lookup"><span data-stu-id="f835d-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="f835d-115">Команда создает три файла CS для элемента `BindingElement` (если задан параметр /be:), пять файлов CS для стандартного элемента `Binding` (если задан параметр /sb:), а также XML-файл.</span><span class="sxs-lookup"><span data-stu-id="f835d-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="f835d-116">Если используется параметр /be, один из файлов CS реализует `BindingElementExtensionSection` для элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="f835d-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="f835d-117">Этот код предоставляет элемент `BindingElement` для системы конфигурации, чтобы элементом привязки могли пользоваться другие пользовательские привязки.</span><span class="sxs-lookup"><span data-stu-id="f835d-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="f835d-118">В других файлах содержатся классы, представляющие значения по умолчанию и константы.</span><span class="sxs-lookup"><span data-stu-id="f835d-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="f835d-119">В файлах имеются комментарии `//TODO` напоминающие разработчикам о необходимости обновить значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f835d-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="f835d-120">Если задан параметр /sb, два файла CS реализуют элементы `StandardBindingElement` и `StandardBindingCollectionElement` соответственно, в результате чего стандартная привязка предоставляется системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f835d-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="f835d-121">В других файлах содержатся классы, представляющие значения по умолчанию и константы.</span><span class="sxs-lookup"><span data-stu-id="f835d-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="f835d-122">В файлах имеются комментарии `//TODO` напоминающие разработчикам о необходимости обновить значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f835d-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="f835d-123">Если указан параметр/SB:, кодетоаддто\<*йоурстдбиндинг*>. cs содержит код, который необходимо вручную добавить в класс, реализующий стандартную привязку.</span><span class="sxs-lookup"><span data-stu-id="f835d-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="f835d-124">Файл SampleConfig.xml file содержит код конфигурации, который необходимо добавить в файл конфигурации, регистрирующий обработчики, определенные ранее на шагах 1 и 2.</span><span class="sxs-lookup"><span data-stu-id="f835d-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
