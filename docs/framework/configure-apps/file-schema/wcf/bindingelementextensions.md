---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 775f93f319c136a29a32ffaa1dfabc12ee081b29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700999"
---
# <a name="bindingelementextensions"></a><span data-ttu-id="45fa9-101">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="45fa9-101">\<bindingElementExtensions></span></span>
<span data-ttu-id="45fa9-102">В этом разделе описывается, как обеспечивается использование пользовательского элемента привязки в файле конфигурации компьютера или приложения.</span><span class="sxs-lookup"><span data-stu-id="45fa9-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="45fa9-103">Элемент пользовательской привязки можно добавить в эту коллекцию, используя ключевое слово `add`, присвоив атрибуту `type` элемента значение, соответствующее расширению элемента привязки, и указав в атрибуте `name` пользовательский элемент привязки.</span><span class="sxs-lookup"><span data-stu-id="45fa9-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="45fa9-104">Расширения привязки позволяют пользователю создавать свои собственные элементы привязки и задействовать их как часть пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="45fa9-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="45fa9-105">Ну уровне программирования расширение привязки представляет собой тип, реализующий абстрактный класс <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="45fa9-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="45fa9-106">В файле конфигурации раздел `bindingElementExtensions` используется для определения элемента расширения.</span><span class="sxs-lookup"><span data-stu-id="45fa9-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="45fa9-107">В следующем примере элемент `add` и атрибут `name` используются для добавления расширения привязки в раздел `bindingElementExtensions` файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="45fa9-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="45fa9-108">Чтобы добавить в элемент возможность настройки, пользователю следует записать и зарегистрировать элемент `bindingElementExtensionSection`.</span><span class="sxs-lookup"><span data-stu-id="45fa9-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="45fa9-109">Дополнительные сведения об этом см. в документации по <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="45fa9-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="45fa9-110">После определения элемента и типа его конфигурации расширение можно использовать как часть пользовательской привязки (см. следующий пример).</span><span class="sxs-lookup"><span data-stu-id="45fa9-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="45fa9-111">См. также</span><span class="sxs-lookup"><span data-stu-id="45fa9-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="45fa9-112">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="45fa9-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
