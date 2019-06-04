---
title: Элемент <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4187d266d82783ebb72073c1da92faff95352884
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489376"
---
# <a name="shadowcopyverifybytimestamp-element"></a>Элемент \<shadowCopyVerifyByTimeStamp>
Указывает, использует ли теневое копирование поведение при запуске по умолчанию, представленные в .NET Framework 4, или возвращается к поведению более ранних версий платформы .NET Framework при запуске.  
  
 \<Конфигурация > элемент  
\<Среда выполнения > элемент  
Элемент \<shadowCopyVerifyByTimeStamp>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|enabled|Обязательный атрибут.<br /><br /> Указывает, следует ли домены приложений, использующих теневое копирование сравнение отметки времени сборок при запуске, чтобы определить, обновлена ли сборки перед теневым копированием.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|true|При запуске копируются только те сборки, которые были обновлены с момента последнего копирования в каталог теневого копирования. Это значение по умолчанию для .NET Framework 4.|  
|False|Возвращается поведение при запуске предыдущих версий платформы .NET Framework, в которых должен был быть скопируйте все файлы во время запуска.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 Начиная с .NET Framework 4, копируются сборки только в том случае, если их отметки времени показывают, что они были изменены с момента последнего копирования в каталог теневого копирования. Это сокращает время запуска для многих приложений, использующих теневое копирование, как описано в разделе [теневое копирование сборок](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Для приложений с большим процентом и высокой частотой обновления сборок это изменение в поведении может не быть выгодно. В этом случае можно использовать этот элемент для восстановления поведения предыдущих версий платформы .NET Framework.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как отключить режим запуска по умолчанию теневое копирование в .NET Framework 4, и вернуться к поведению при запуске предыдущих версий платформы .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также

- [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Теневое копирование сборок](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
