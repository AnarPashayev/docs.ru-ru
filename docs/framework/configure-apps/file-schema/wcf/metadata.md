---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: c0c9848d073c799e1f97dd79b375848dfab71e99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763910"
---
# <a name="metadata"></a>\<метаданные >
Задает способ обработки метаданных службы.  
  
 \<system.ServiceModel>  
\<Клиент >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Задает все средства импорта политики, контролирующие импорт утверждений пользовательской политики о привязках. Средство импорта политики используется для поиска утверждений пользовательской политики о свойствах привязки, а также для подключения пользовательского элемента привязки, реализующего свойства, необходимые для утверждения.|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Задает все средства импорта WSDL, импортирующие метаданные на языке WSDL 1.1 с вложениями WS-Policy. Средство импорта WSDL используется для импорта метаданных, а также для их преобразования в различные классы, представляющие данные контракта и конечной точки. Он может выборочно импортировать сведения контракта и конечной точки, а также свойства, предоставляющие сведения об ошибках и принимающие сведения о типах, относящиеся к процессу импорта и преобразования. Оно также поддерживает импорт данных привязки и свойств, предоставляющих доступ к каким-либо документам политики, документам WSDL, расширениям WSDL и документам схемы XML.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Клиент >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|В разделе client определяется список конечных точек, к которым может подключаться клиент.|  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Конфигурация клиента WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Клиенты](../../../../../docs/framework/wcf/feature-details/clients.md)
