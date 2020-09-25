---
title: Элемент <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 9ecf2e382b5d483377df871835793219b3f74760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170276"
---
# <a name="appdomainresourcemonitoring-element"></a>Элемент \<appDomainResourceMonitoring>

Указывает среде собирать статистику для всех доменов приложений в процессе за весь период его существования.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, собирает ли среда выполнения статистические данные для отслеживания ресурсов домена приложения.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`true`|Собираются статистические данные для отслеживания ресурсов домена приложения.|  
|`false`|Статистика по мониторингу ресурсов домена приложений не собирается.|  
  
### <a name="child-elements"></a>Дочерние элементы  

 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Remarks  

 Мониторинг ресурсов домена приложений доступен через класс домена управляемого приложения, интерфейс размещения [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) и трассировку событий для Windows (ETW). При включении мониторинга статистика собирается для всех доменов приложений в процессе в течение жизненного цикла процесса.  
  
 Чтобы включить мониторинг из управляемого кода, используйте <xref:System.AppDomain.MonitoringIsEnabled%2A> свойство.  
  
 Этот элемент конфигурации доступен только в .NET Framework 4 и более поздних версиях.  
  
## <a name="example"></a>Пример  

 В следующем примере показано, как включить отслеживание ресурсов домена приложения.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Схема параметров среды выполнения](index.md)
- [Схема файла конфигурации](../index.md)
