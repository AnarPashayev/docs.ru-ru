---
title: Элемент <remove> для <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 7c0173879c692588cc2e15f0b14a5687bb0404fb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300677"
---
# <a name="remove-element-for-configsections"></a>\<Удалить > элемент для \<configSections >

Удаляет предварительно определенный раздел или группу разделов.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<Удалить >**

## <a name="syntax"></a>Синтаксис

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Атрибут

|           | Описание |
| --------- | ----------- |
| **name**  | Обязательный атрибут.<br><br>Задает имя раздела или группы разделов. |

## <a name="parent-element"></a>Родительский элемент

|     | Описание |
| --- | ----------- |
| [ **\<configSections >** элемент](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Содержит раздел конфигурации и пространства имен объявления. |

## <a name="child-elements"></a>Дочерние элементы

None

## <a name="remarks"></a>Примечания

Можно использовать  **\<удалить >** элемент нужно удалить разделы и группы разделов из приложения, которые были определены на более высоком уровне в иерархии файла конфигурации.

## <a name="example"></a>Пример

В следующем примере показано, как использовать  **\<удалить >** элемент в файле конфигурации приложения для удаления раздела, ранее определенные в файле конфигурации компьютера.

В коде следующего файла конфигурации компьютера объявляет разделе  **\<sampleSection >** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

В коде следующего файла конфигурации приложения удаляет  **\<sampleSection >** раздел. После удаления приложения не удается получить параметры в  **\<sampleSection >** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>файл конфигурации

Этот элемент может использоваться в файле конфигурации приложения, файл конфигурации компьютера (*Machine.config*), и *Web.config* файлы, которые не на уровне каталога приложения.

## <a name="see-also"></a>См. также

- [Схема файла конфигурации для .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
